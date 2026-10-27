# Reglas del proyecto — LadyBug Shop

> Dirección visual elegida: **Boulevard Bohème**

---

## Tecnología

- **Solo HTML5 y Tailwind CSS v4 vía CDN.**
  - CDN: `https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4`
- **Prohibido:** React, Vue, cualquier framework de JavaScript, librerías de componentes, build tools.
- **Prohibido cualquier `<script>`** salvo el de Tailwind y, si se aplica, el de Google Fonts.
- **Sin CSS personalizado** salvo que sea estrictamente indispensable y se acuerde con el equipo.
- **Sin imágenes reales:** usar bloques de color con `aspect-*`, `role="img"` y `aria-label` (ver DESIGN.md §7).
- **Sin fotografías externas** ni de stock.

## Vistas

| # | Vista                     | Archivo            | Rama ejemplo           |
|---|---------------------------|--------------------|------------------------|
| 1 | Home (inicio)             | `index.html`       | `feature/home`         |
| 2 | Catálogo                  | `catalogo.html`    | `feature/catalogo`     |
| 3 | Vista de producto         | `producto.html`    | `feature/producto`     |
| 4 | Carrito                   | `carrito.html`     | `feature/carrito`      |
| 5 | Checkout (3 pasos)        | `checkout.html`    | `feature/checkout`     |

Los 3 pasos del checkout son: **Información de envío → Método de pago → Resumen**.

## Estructura compartida

- **Navbar y footer idénticos en todas las vistas.** No modificarlos dentro de la tarea de una vista concreta.
- **Navbar:** logo (enlace a `index.html`), barra de búsqueda (`<form role="search">` hacia `catalogo.html` vía GET), menú de cuenta (`<details>` nativo sin JS), enlaces a las 5 vistas.
- **Footer:** Categorías (calzado, camisas, pantalones, accesorios con enlace `?categoria=`), Legal (términos, privacidad, sobre la marca — texto plano, sin páginas), Contacto (pendiente).

## Marcado HTML

- **HTML semántico:** `header`, `nav`, `main`, `section`, `article`, `footer`, `form`.
- **Un solo `<h1>` por página.**
- **Mobile-first:** breakpoints `sm:`, `md:`, `lg:`. Sin scroll horizontal en móvil (`overflow-x-hidden` en `<body>` si es necesario).
- **`lang="es"`** y una `meta description` propia en cada página.
- **Bloques de imagen** (placeholders sin fotos): `aspect-[3/4]` o `aspect-video` según contexto, `role="img"` + `aria-label`, gradiente o color sólido (ver DESIGN.md §7).

## Schema.org / JSON-LD

- **`index.html`:** `Organization` (nombre: LadyBug Shop, url: https://ladybug.fr).
- **`producto.html`:** `Product` (nombre pendiente de definir).
- JSON-LD válido y dentro de un `<script type="application/ld+json">`.

## Diseño visual (Boulevard Bohème)

| Elemento           | Especificación                                          |
|--------------------|---------------------------------------------------------|
| Fondo página       | `bg-orange-50` (#FFF9F0)                                |
| Fondo footer       | `bg-orange-100` (#F5EDE0)                               |
| Texto principal    | `text-stone-900` (#2B1D14)                              |
| Texto secundario   | `text-stone-500` (#7F6B5E)                              |
| Bordes             | `border-stone-300` (#D6C9BC)                            |
| Botón primario     | `bg-red-700 text-white hover:bg-red-800` (#C73E3A)      |
| Acento decorativo  | `text-amber-400` o `border-amber-300` (#D4A373)         |
| Input focus        | `ring-2 ring-red-700/30 border-red-700`                 |
| Error              | `text-red-800` / `bg-red-50` (#A1302D)                  |
| Éxito              | `text-green-800` / `bg-green-50` (#2B6B3F)              |
| Tipografía títulos | **Lora** 400/600 — `<h1 class="font-['Lora'] font-semibold">` |
| Tipografía cuerpo  | **Poppins** 300/400/500/600 — `<body class="font-['Poppins']">` |

> **Nota:** Las vistas existentes (`index.html`, `catalogo.html`, etc.) aún usan la paleta `zinc`/`white` del prototipo inicial. La migración a la paleta Boulevard Bohème se hará cuando se aborden las tareas de cada vista. Ver DESIGN.md §12 para la tabla de reemplazo.

## Archivos que no deben modificarse

- `server.py`
- `learn.json`
- `README.md`, `README.es.md`, `README.cn.md`

## Referencias

Para detalles completos de componentes (cards, botones, formularios, bloques de imagen, checkout, espaciado, responsive), consultar:

1. **DESIGN.md** — guía de estilo detallada (fuente de verdad visual)
2. **CONTEXT.md** — contexto de cliente, equipo y alcance
3. **AGENTS.md** — este archivo (reglas vinculantes del proyecto)
