# NodoWeb — Sitio principal

Sitio de una sola página construido con HTML + Tailwind CSS v4 (compilado localmente, sin CDN).

## Estructura

```
index.html            → el sitio
src/input.css          → tema (colores, tipografías) + estilos propios
dist/output.css        → CSS compilado y minificado (esto es lo que carga index.html)
package.json            → scripts de compilación
proyectos/               → proyectos de concepto enlazados desde la sección "Proyectos"
  cafe-raiz.html           → demo: cafetería de barrio
  ferreteria-central.html   → demo: ferretería + automatización de pedidos por WhatsApp
```

Los dos archivos en `proyectos/` son autosuficientes (CSS propio embebido, sin depender de
`dist/output.css`) y están claramente marcados en su propio contenido como proyectos de
concepto — no representan clientes reales. Cuando NodoWeb tenga los primeros clientes reales,
lo natural es reemplazarlos por casos reales (con permiso del cliente) en la sección
"Proyectos" de `index.html`.

## Cómo trabajar en el sitio

1. Instalar dependencias (solo la primera vez):
   ```
   npm install
   ```
2. Mientras editas `src/input.css`, deja esto corriendo en una terminal para que recompile solo:
   ```
   npm run watch
   ```
3. Antes de publicar cambios, genera la versión final minificada:
   ```
   npm run build
   ```
4. Abre `index.html` directamente en el navegador para revisar (no necesitas servidor).

## Cotizador y vista previa

- La sección "Cotizador" calcula un estimado en vivo según lo que la persona marque, y arma
  un mensaje de WhatsApp pre-escrito con el resumen — ajusta los precios en el objeto `PRICES`
  dentro de `index.html` si cambian las tarifas.
- `favicon.svg` / `favicon-32.png` / `favicon-16.png` / `apple-touch-icon.png`: ícono del sitio.
- `og-image.png`: imagen que se muestra al compartir el link (WhatsApp, Facebook, etc.).
- Los meta tags de Open Graph usan `https://sirthiagomaster.github.io/NodoWeb-Site/` (la URL real de
  GitHub Pages). Si en el futuro compran el dominio `nodoweb.co` y lo conectan, hay que volver a
  actualizar estas URLs en el `<head>` de `index.html`, en `robots.txt`, en `sitemap.xml` y en el
  bloque de datos estructurados (JSON-LD).

## Contacto y mapa

- WhatsApp y correo ya están puestos con los datos reales (no son placeholders).
- La sección de contacto incluye un mapa funcional (Leaflet + CARTO, sin necesidad de API key)
  que muestra la zona de cobertura (Medellín y Bello) en vez de una dirección exacta —
  NodoWeb no tiene local físico, así que mostrar una dirección puntual expondría
  innecesariamente dónde trabaja cada uno.

## Publicar el sitio

`dist/output.css` ya queda compilado y subido al repositorio (no depende de que GitHub compile nada),
así que basta con activar GitHub Pages apuntando a la rama principal, o conectar el repo a Netlify/Vercel.
