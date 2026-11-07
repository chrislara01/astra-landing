# Astra — Landing page

Sitio estático (HTML + CSS + JS, sin build). Abre `index.html` o sírvelo con cualquier servidor web.

- `index.html` — la página completa
- `assets/` — logos de Astra
- `img/` — fotos provisionales (Unsplash, licencia libre)

## Publicar en GitHub Pages
Al hacer push a `main`, el workflow `.github/workflows/pages.yml` la publica.
En el repositorio: **Settings → Pages → Source: GitHub Actions** (una sola vez).

## Publicar en un servidor (Nginx)
Copia el contenido de esta carpeta a la raíz del sitio, por ejemplo `/var/www/astra`, y usa:

```nginx
server {
    listen 80;
    server_name astra.ejemplo.com;
    root /var/www/astra;
    index index.html;
    location / { try_files $uri $uri/ =404; }
    location ~* \.(jpg|svg)$ { expires 30d; add_header Cache-Control "public"; }
    gzip on; gzip_types text/html text/css application/javascript image/svg+xml;
}
```

## Pendiente antes de producción
- Número real de WhatsApp (ahora `5350000000`, aparece en los enlaces `wa.me`)
- Horario y formas de pago
- Fotos propias de los productos
