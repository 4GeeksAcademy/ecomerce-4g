# Spec — Plantilla base de layout (`base-layout`)

> Proyecto: **LadyBug Shop** · Dirección visual: **Boulevard Bohème**
> Rama: `feature/layout-base`
> Entregable: `docs/reference/base.html`
> Fuentes: [AGENTS.md](../../AGENTS.md) (vinculante), [DESIGN.md](../../DESIGN.md) (fuente de verdad visual), [CONTEXT.md](../../CONTEXT.md)

---

## 1. Objetivo

Definir una plantilla HTML común que sirva de punto de partida para las 5 vistas del prototipo (`index.html`, `catalogo.html`, `producto.html`, `carrito.html`, `checkout.html`). La plantilla contiene:

- `<head>` común (metadatos, Tailwind v4 por CDN, Google Fonts).
- **Navbar** (`<header>`) compartida.
- `<main>` **vacío**, donde cada vista añadirá su contenido.
- **Footer** compartido.

La navbar y el footer de esta plantilla son la **única versión canónica**: se copian literalmente en todas las vistas y no se modifican dentro de la tarea de una vista concreta.

## 2. Alcance

### Incluido
- Estructura HTML5 semántica del documento completo.
- Marcado y clases Tailwind de navbar y footer según DESIGN.md §4 y §5.
- Requisitos de rendimiento, accesibilidad y SEO base.

### Excluido
- Contenido específico de cualquier vista (hero, catálogo, producto, carrito, checkout).
- JSON-LD (`Organization` y `Product` pertenecen a `index.html` y `producto.html`).
- Lógica funcional (búsqueda, carrito, cuenta): el prototipo es solo visual.
- Páginas de destino legales.

## 3. Restricciones técnicas

| ID    | Requisito |
|-------|-----------|
| RT-01 | Solo HTML5 + Tailwind CSS v4 vía CDN `https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4`. |
| RT-02 | Único `<script>` permitido: el de Tailwind. Google Fonts se carga con `<link>`, no con script. |
| RT-03 | Sin JavaScript propio, frameworks, librerías de componentes ni build tools. |
| RT-04 | Sin CSS personalizado (ni `<style>` ni atributos `style`), salvo acuerdo explícito del equipo. |
| RT-05 | Sin imágenes externas ni fotografías. El logo es texto (Lora). Los iconos, si los hay, son SVG inline. |
| RT-06 | El archivo debe abrirse correctamente tanto directamente en el navegador como servido por `server.py` (rutas relativas). |
| RT-07 | No modificar `server.py`, `learn.json` ni los `README*`. |

## 4. Requisitos del documento (`<html>` / `<head>` / `<body>`)

| ID    | Requisito |
|-------|-----------|
| RD-01 | `<!DOCTYPE html>` y `<html lang="es">`. |
| RD-02 | `<meta charset="UTF-8">` como primer elemento del `<head>`. |
| RD-03 | `<meta name="viewport" content="width=device-width, initial-scale=1">`. |
| RD-04 | `<title>` con patrón `Página — LadyBug Shop` (placeholder a sustituir por cada vista). |
| RD-05 | `<meta name="description">` con contenido placeholder, marcado como obligatorio de personalizar en cada vista. |
| RD-06 | Google Fonts según DESIGN.md §2.3: `preconnect` a `fonts.googleapis.com` y `fonts.gstatic.com` (`crossorigin`), hoja con Lora 400/600 y Poppins 300/400/500/600 y `display=swap`. |
| RD-07 | `<body class="flex min-h-screen flex-col overflow-x-hidden bg-orange-50 font-['Poppins'] text-stone-900">`. |
| RD-08 | Orden de hijos del `<body>`: enlace "Saltar al contenido" → `<header>` → `<main>` → `<footer>`. |
| RD-09 | La plantilla **no** contiene `<h1>`; cada vista aporta exactamente uno dentro de `<main>`. |

## 5. Navbar (`<header>`)

### 5.1 Estructura

| ID    | Requisito |
|-------|-----------|
| RN-01 | `<header class="border-b border-stone-200 bg-orange-50">` con un `<nav aria-label="Principal">` interior. |
| RN-02 | Contenedor: `mx-auto flex w-full max-w-7xl flex-wrap items-center gap-4 px-4 py-3 sm:px-6 sm:py-4 lg:px-8`. |
| RN-03 | **Logo:** enlace de texto "LadyBug Shop" a `index.html`, `font-['Lora'] font-semibold text-lg sm:text-xl text-stone-900`. |
| RN-04 | **Búsqueda:** `<form role="search" action="catalogo.html" method="get">` con `<input type="search" name="q">`, `<label>` asociado (puede ser `sr-only`) y botón `type="submit"` con texto accesible. |
| RN-05 | Input de búsqueda: `bg-white border border-stone-300 rounded px-3 py-2 text-sm placeholder:text-stone-400` + focus `focus:outline-none focus:ring-2 focus:ring-red-700/30 focus:border-red-700`. |
| RN-06 | Botón de búsqueda: `bg-stone-100 hover:bg-stone-200 text-stone-700 border border-stone-300`. |
| RN-07 | **Enlaces de navegación** (lista `<ul>`): Inicio (`index.html`), Catálogo (`catalogo.html`), Producto (`producto.html`), Carrito (`carrito.html`), Checkout (`checkout.html`). Estilo `text-sm hover:text-red-700`. |
| RN-08 | **Menú de cuenta** con `<details>`/`<summary>` nativo (sin JS). `summary`: Poppins 500, `text-sm`, `cursor-pointer`, borde sutil. Panel: `bg-white border border-stone-200 shadow-sm rounded`, enlaces `hover:text-red-700`. Opciones: Mi carrito (`carrito.html`), Checkout (`checkout.html`). |
| RN-09 | El panel desplegable del menú de cuenta se posiciona de forma que **no desplace** el layout ni genere scroll horizontal en móvil. |
| RN-10 | Marcado de página activa: la plantilla documenta (en comentario HTML de una línea) que cada vista añade `aria-current="page"` y `text-red-700` a su enlace. |

### 5.2 Responsive

| ID    | Requisito |
|-------|-----------|
| RN-11 | Móvil (base): fila 1 = logo + menú de cuenta; fila 2 = búsqueda a ancho completo; fila 3 = enlaces (con `flex-wrap`). Sin desbordamiento a 320 px. |
| RN-12 | `md:`/`lg:` todos los elementos en una sola fila cuando el ancho lo permita. |

## 6. `<main>`

| ID    | Requisito |
|-------|-----------|
| RM-01 | `<main id="contenido" class="flex-1">` **vacío**, salvo un comentario HTML indicando dónde insertar el contenido de la vista. |
| RM-02 | Se documenta (comentario) el contenedor recomendado para el contenido: `mx-auto w-full max-w-7xl px-4 py-8 sm:px-6 sm:py-12 lg:px-8`. |
| RM-03 | Debe existir un enlace "Saltar al contenido" (`href="#contenido"`) visible solo al recibir foco (`sr-only focus:not-sr-only`). |

## 7. Footer (`<footer>`)

| ID    | Requisito |
|-------|-----------|
| RF-01 | `<footer class="border-t border-stone-200 bg-orange-100">` con contenedor `mx-auto max-w-7xl px-4 py-10 sm:px-6 lg:px-8 lg:py-12`. |
| RF-02 | Grid: `grid grid-cols-1 gap-8 sm:grid-cols-2 lg:grid-cols-3`. |
| RF-03 | Títulos de columna: `<h2>` con `text-sm font-semibold uppercase tracking-wider text-stone-700` (Poppins). |
| RF-04 | **Categorías:** Calzado, Camisas, Pantalones, Accesorios → `catalogo.html?categoria=calzado|camisas|pantalones|accesorios`. Estilo `text-sm text-stone-600 hover:text-red-700`. |
| RF-05 | **Legal:** Términos y condiciones, Política de privacidad, Sobre la marca como **texto plano** (no enlaces, sin páginas de destino). |
| RF-06 | **Contacto:** texto plano "Pendiente de definir", `text-sm text-stone-600`. |
| RF-07 | Línea inferior de copyright: `© LadyBug Shop · París`, `text-xs text-stone-500`, separada por `border-t border-stone-300`. |
| RF-08 | Cada columna es una `<section>` (o `<nav aria-label="…">` en el caso de Categorías). |

## 8. Rendimiento — PageSpeed Insights ≥ 80

**Criterio de aceptación:** la puntuación de **Rendimiento** en PageSpeed Insights (móvil **y** escritorio) es **≥ 80** para `docs/reference/base.html` publicada, y no debe bajar de 80 en ninguna vista construida a partir de ella.

### 8.1 Riesgo conocido

`@tailwindcss/browser@4` es un script que genera el CSS en tiempo de ejecución: bloquea el renderizado y penaliza FCP/LCP/TBT. Los requisitos siguientes buscan compensarlo sin infringir RT-01/RT-02.

### 8.2 Requisitos

| ID    | Requisito |
|-------|-----------|
| RP-01 | `<link rel="preconnect" href="https://cdn.jsdelivr.net" crossorigin>` antes del script de Tailwind. |
| RP-02 | Fijar la versión del CDN de Tailwind (p. ej. `@4.x.y` concreta) para aprovechar caché inmutable de jsDelivr; el equipo decide la versión exacta. |
| RP-03 | Google Fonts: solo los pesos listados en RD-06, `display=swap` y `preconnect`. No añadir pesos ni familias adicionales. |
| RP-04 | Cero imágenes externas; logo en texto; iconos SVG inline pequeños con `width`/`height` explícitos. |
| RP-05 | Sin recursos de terceros adicionales (analytics, iconos web, fuentes extra, iframes). |
| RP-06 | **CLS < 0.1:** dimensiones fijas para elementos de navbar; el `<details>` del menú de cuenta se superpone (`absolute`) sin empujar contenido. |
| RP-07 | **LCP < 2.5 s** (escritorio) y lo más bajo posible en móvil; el elemento LCP de la plantilla debe ser texto. |
| RP-08 | **TBT < 200 ms**: no hay más scripts que el de Tailwind. |
| RP-09 | DOM ligero: navbar + footer < 150 nodos en total; evitar `div` innecesarios. |
| RP-10 | HTML final < 15 KB sin comprimir. |

### 8.3 Verificación

1. Publicar la plantilla en una URL accesible (p. ej. puerto reenviado del Codespace o GitHub Pages).
2. Ejecutar PageSpeed Insights (https://pagespeed.web.dev/) en móvil y escritorio.
3. Adjuntar capturas de ambas puntuaciones en la PR de `feature/layout-base`.
4. Si móvil < 80, documentar métricas (FCP, LCP, TBT, CLS, SI) y proponer al equipo medidas adicionales antes de fusionar.

## 9. Accesibilidad y SEO (objetivos complementarios)

| ID    | Requisito |
|-------|-----------|
| RA-01 | Objetivo ≥ 90 en Accesibilidad, Prácticas recomendadas y SEO de PageSpeed. |
| RA-02 | Contraste WCAG AA en todo el texto (paleta de DESIGN.md §1). |
| RA-03 | Todos los controles accesibles por teclado con foco visible (`focus-visible:ring-2 focus-visible:ring-red-700/30`). |
| RA-04 | Landmarks únicos y etiquetados: `header`, `nav[aria-label="Principal"]`, `main`, `footer`. |
| RA-05 | Áreas táctiles de enlaces y botones ≥ 24×24 px (recomendado 44×44 px en móvil). |
| RA-06 | Jerarquía de encabezados válida: el footer usa `<h2>`, coherente con el `<h1>` que aporte cada vista. |

## 10. Reutilización en las vistas

1. Cada vista parte de una copia de `docs/reference/base.html`.
2. Se personalizan solo: `<title>`, `meta description`, `aria-current` del enlace activo, contenido de `<main>` y, en su caso, el JSON-LD.
3. `<header>` y `<footer>` se copian **sin cambios**. Cualquier cambio en ellos se hace primero en `docs/reference/base.html` (rama `feature/layout-base`) y se propaga a todas las vistas.

## 11. Criterios de aceptación

- [ ] Existe `docs/reference/base.html` y cumple RT-*, RD-*, RN-*, RM-*, RF-*.
- [ ] Solo hay un `<script>` (Tailwind); ningún `<style>` ni atributo `style`.
- [ ] `<main>` vacío (solo comentarios) y sin `<h1>` en la plantilla.
- [ ] Sin scroll horizontal de 320 px a 1440 px.
- [ ] Menú de cuenta funciona solo con `<details>` y no provoca desplazamiento de layout.
- [ ] Búsqueda envía `GET catalogo.html?q=…`; categorías enlazan a `catalogo.html?categoria=…`.
- [ ] HTML válido en el validador W3C sin errores.
- [ ] PageSpeed Insights **Rendimiento ≥ 80** en móvil y escritorio (capturas en la PR).

## 12. Cuestiones abiertas

1. **Versión exacta de Tailwind** a fijar (RP-02).
2. **Color de borde de la navbar:** DESIGN.md §4 usa `border-stone-200`; AGENTS.md define bordes como `border-stone-300`. Propuesta: `stone-200` para separadores de layout y `stone-300` para inputs.
3. **Contacto del footer:** contenido pendiente de definir por el cliente.
4. Si el rendimiento móvil no alcanza 80 con el CDN de runtime, el equipo deberá acordar una alternativa (p. ej. permitir CSS precompilado), lo que requiere actualizar antes AGENTS.md.
