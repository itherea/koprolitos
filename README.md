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
  fonts/              Unbounded, Space Grotesk y JetBrains Mono (woff2, alojadas acá)
  img/                portada, fotogramas y tapa del disco en WebP
  og.jpg              imagen para compartir (1200 × 630)
  favicon.svg
```

No hay dependencias ni proceso de build: es HTML estático.

### Tipografía y sistema visual

- **Unbounded** para títulos y subtítulos (variable, 200–900).
- **Space Grotesk** para párrafos, fichas y lectura (variable, 300–700).
- **JetBrains Mono** para etiquetas, navegación y datos de la interfaz.

La paleta parte de un negro de terminal, texto hueso de alto contraste, un acento lima fosforescente para la interfaz y un color mineral por estrato (`--mineral`). Las fuentes se alojan en `assets/fonts` para no depender de Google Fonts en tiempo de ejecución.

## Cómo funciona el video

Cada póster es un link a YouTube. Con JavaScript activo, al hacer clic se reemplaza por el reproductor de `youtube-nocookie.com` con autoplay, así la página no carga YouTube hasta que alguien elige ver un video. El reproductor tiene un botón **Cerrar** y responde a `Escape` para volver al póster. Sin JavaScript, el link abre YouTube.

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
2. Copiar un bloque `<article class="spec">` en `index.html`, cambiar `data-yt`, el `href`, los textos, el `id` (`estrato-04`), la barra (`KP-26-04`, mineral, duración) y el color `--mineral`.
3. Agregar la canción al índice `<ol class="tracklist">` del inicio.
4. Actualizar los contadores y la duración total: `3 muestras` / `08:25` en la portada y en la cabecera de Estratos.
