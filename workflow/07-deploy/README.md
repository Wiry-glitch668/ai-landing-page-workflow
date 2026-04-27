# Fase 6: Deploy (5 min)

## Quem faz: IA + Humano

## Processo basico

```bash
npm run build
rsync -avz --delete dist/ server:/var/www/[cliente]/
```

## Configuracao nginx (template)

```nginx
server {
    listen 80;
    server_name [dominio.com.br] www.[dominio.com.br];
    root /var/www/[cliente-slug];
    index index.html;

    gzip on;
    gzip_types text/plain text/css application/json application/javascript text/xml;

    location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg|webp|avif|woff2)$ {
        expires 1y;
        add_header Cache-Control "public, immutable";
    }

    location / {
        try_files $uri $uri/ /index.html;
    }

    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header Referrer-Policy "strict-origin-when-cross-origin" always;
}
```

## SSL

```bash
sudo certbot --nginx -d [dominio] -d www.[dominio]
```

## Adaptacoes para outros ambientes

- **Vercel:** `vercel deploy --prod`
- **Netlify:** `netlify deploy --prod --dir=dist`
- **GitHub Pages:** push para branch `gh-pages`

## Proxima fase: [08 - Otimizacao](../08-optimization/)
