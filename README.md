# CONFORCA — demo de interfaz

Demo de la página principal de **Conforca, C.A.** (Servicios y Mantenimiento, RIF J-30912087-5):
venta de materiales de ferretería y artículos para la industria en general, más servicios
de mantenimiento.

HTML, CSS y JavaScript sin dependencias. No hace falta `npm install`.

## Correr en local

```bash
npm start
```

Queda en `http://localhost:3000`. El servidor ([server.js](server.js)) es un estático
mínimo de Node, cero dependencias, y sirve todo con `Cache-Control: no-cache`: editás
un archivo de `public/`, refrescás, y ya está.

## Deploy

El sitio es 100 % estático, así que en Vercel no corre `server.js` — se publica el
contenido de `public/` tal cual. Eso está declarado en [vercel.json](vercel.json):

```json
{ "framework": null, "outputDirectory": "public" }
```

Importás el repo en Vercel y no hay que configurar nada más: sin build command,
sin variables de entorno.

## Estructura

```
public/
  index.html      estructura y sprite de iconos SVG
  styles.css      diseño completo, tokens de color en :root
  app.js          catálogo de ejemplo (42 productos) y toda la interacción
  assets/
    logo.jpg
    img/          50 imágenes locales
    img/CREDITOS.txt   origen y licencia de cada imagen
server.js         servidor estático para desarrollo local
```

## Paleta

Azul, blanco y negro. El azul (`--azul: #28156E`) está muestreado del propio `logo.jpg`
— es el único color de la marca, el resto del archivo es blanco puro. No cambiarlo sin
volver a muestrear: de ahí depende que el logo y la pantalla de entrada se vean como
una sola pieza, y por eso la cortina de intro va en blanco.

`--azul-claro: #8DA2FF` existe porque el azul de marca es demasiado oscuro para usarlo
como texto o acento sobre los fondos negros (aviso superior, sección de más vendidos,
pie). Sobre fondo claro va `--azul`; sobre fondo negro va `--azul-claro`.

Reparto de superficies: aviso superior negro, nav principal blanco, nav secundaria azul,
hero y pie negros. El botón principal es `.btn-azul` (azul con texto blanco).

El dorado (`--dorado-tenue` / `--dorado` / `--dorado-claro`) es la única excepción a la
paleta y está acotado a un solo uso: el anillo animado de las tarjetas de "los que más
salen". Si se usa en otro lado deja de leerse como distintivo de esa sección.

## Pendientes antes de producción

- **Datos de contacto y ubicación.** Dirección, teléfono, correo, WhatsApp, redes
  sociales, sedes y horarios son de ejemplo. Están marcados en el HTML con
  `<!-- DATO PLACEHOLDER -->`. Los enlaces de WhatsApp apuntan a
  `https://wa.me/000000000000` a propósito: no llevan a ningún número real.
- **Licencias de las imágenes.** Las 50 vienen de Wikimedia Commons con licencias
  variadas (CC BY, CC BY-SA, dominio público). Hay que revisarlas una por una y dar
  la atribución que cada una exija, o —mejor— reemplazarlas por fotos reales de la
  mercancía. Ver [CREDITOS.txt](public/assets/img/CREDITOS.txt).
- **Logo.** `logo.jpg` es un JPEG con fondo blanco opaco. Si consiguen el original en
  PNG o SVG con transparencia, se simplifica el pie (hoy lleva una caja blanca detrás)
  y se puede usar un favicon cuadrado en vez del logo apaisado.
- **Precios e inventario.** El catálogo de `app.js` es de muestra.
- **Inicio de sesión.** El modal es solo la interfaz; no hay backend detrás.
