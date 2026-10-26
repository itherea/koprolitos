# Koprolitos 2026

Sitio de una sola página que presenta los tres videoclips en plastilina que Ariel Hernán Contini dirigió y editó para *Antimeme*, el disco de Koprolitos (℗ Escalera circular), generados con IA.

Koprolitos: Gaspar Daffunchio, Pedro Daffunchio, Emanuel Bibiloni y Uriel Mackern.

| Estrato | Canción | Duración | YouTube |
|---|---|---|---|
| 01 | Nada de mí | 3:09 | `hHB4SJT_kek` |
| 02 | Civiles | 2:58 | `nhssz8m2v6I` |
| 03 | Panal | 2:18 | `ZwkB-K8fPCs` |

## Estructura

```
index.html            página completa (HTML, CSS y JS en un solo archivo)
assets/
  fonts/              Big Shoulders Display, Instrument Sans y JetBrains Mono (woff2, alojadas acá)
  img/                portada, fotogramas y tapa del disco en WebP
  og.jpg              imagen para compartir (1200 × 630)
  favicon.svg
```

No hay dependencias ni proceso de build: es HTML estático.

## Cómo funciona el video

Cada póster es un link a YouTube. Con JavaScript activo, al hacer clic se reemplaza por el reproductor de `youtube-nocookie.com` con autoplay, así la página no carga YouTube hasta que alguien elige ver un video. Sin JavaScript, el link abre YouTube.

## Probar en local

```bash
python3 -m http.server 8000
```

y abrir http://localhost:8000.

## Publicación

El sitio está publicado con GitHub Pages en https://itherea.github.io/koprolitos/ (rama `main`, raíz).

Si cambia de dominio, actualizar en `index.html` el `canonical`, `og:url` y `og:image`: tienen que ser direcciones absolutas para que WhatsApp e Instagram muestren la imagen al compartir el link.

## Agregar un estrato

1. Exportar el póster en WebP a 960 y 1600 px de ancho (`estrato-04-poster-960.webp`, `estrato-04-poster-1600.webp`) y tres fotogramas a 800 px (`estrato-04-a-800.webp`, etc.).
2. Copiar un bloque `<article class="spec">` en `index.html`, cambiar `data-yt`, el `href`, los textos y el color `--mineral`.
3. Actualizar el contador "3 muestras" del encabezado.
