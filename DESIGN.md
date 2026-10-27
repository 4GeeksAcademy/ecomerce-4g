# Design System — LadyBug Shop

> Dirección visual elegida: **Boulevard Bohème**

---

## 1. Paleta de colores

### 1.1 Colores primarios

| Token             | Hex       | Tailwind         | Uso principal                              | Contraste WCAG AA (sobre blanco) |
|-------------------|-----------|------------------|--------------------------------------------|----------------------------------|
| `--color-rojo`    | `#C73E3A` | `red-700`        | Botones primarios, acentos, enlaces activos | 4.7:1 (AA para texto ≥14px)     |
| `--color-marron`  | `#5C4033` | `amber-900`      | Títulos principales, texto del logo         | 9.2:1 (AAA)                      |
| `--color-beige`   | `#D4A373` | `amber-300`/`400`| Acentos secundarios, bordes decorativos     | 2.3:1 (solo decorativo)          |
| `--color-terracota| `#A65D4D` | `red-600`/`700`  | Hover de botones, variante secundaria       | 4.5:1 (AA para texto ≥14px)     |

### 1.2 Colores neutros

| Token                | Hex       | Tailwind         | Uso                                         | Contraste (sobre fondo propio) |
|----------------------|-----------|------------------|---------------------------------------------|-------------------------------|
| `--color-crema`      | `#FFF9F0` | `orange-50`      | Fondo general de página, fondos de card     | —                             |
| `--color-crema-oscuro| `#F5EDE0` | `orange-100`     | Fondo de footer, secciones alternas         | —                             |
| `--color-texto`      | `#2B1D14` | `stone-900`      | Texto corporal                              | 12.0:1 (AAA) sobre crema      |
| `--color-texto-suave`| `#7F6B5E` | `stone-500`      | Texto secundario, placeholders, metadatos   | 5.4:1 (AA) sobre crema        |
| `--color-borde`      | `#D6C9BC` | `stone-300`      | Bordes de inputs, separadores, líneas       | 2.9:1 (solo decorativo)       |

### 1.3 Colores funcionales

| Token            | Hex       | Tailwind    | Uso                                        | Contraste WCAG |
|------------------|-----------|-------------|--------------------------------------------|----------------|
| `--color-exito`  | `#2B6B3F` | `green-800` | Mensajes de confirmación, stock disponible | 7.4:1 (AAA)    |
| `--color-error`  | `#A1302D` | `red-800`   | Errores de formulario, stock agotado       | 6.8:1 (AA)     |
| `--color-info`   | `#2C5F7A` | `cyan-800`  | Notificaciones informativas                | 7.1:1 (AAA)    |

### 1.4 Mapeo a clases Tailwind

Cuando se aplique la paleta, se usará el nombre de color de Tailwind más cercano. Ejemplos:

- Fondo página → `bg-orange-50`
- Fondo alterno → `bg-orange-100`
- Texto principal → `text-stone-900`
- Texto secundario → `text-stone-500`
- Botón primario → `bg-red-700 text-white hover:bg-red-800`
- Acento decorativo → `text-amber-400` o `border-amber-300`
- Bordes de input → `border-stone-300`
- Éxito → `text-green-800` / `bg-green-50`
- Error → `text-red-800` / `bg-red-50`

> **Nota:** Hasta que se aplique la paleta definitiva a las vistas existentes, estas siguen usando la base `zinc`/`white` neutra del prototipo inicial. Esta sección de DESIGN.md es la fuente de verdad para la migración.

---

## 2. Tipografía

### 2.1 Fuentes

| Rol               | Fuente            | Peso                         | Carga                                |
|--------------------|-------------------|------------------------------|--------------------------------------|
| Títulos (h1–h3)   | **Lora**          | `400` (regular), `600` (semi-bold) | Google Fonts vía enlace CDN    |
| Texto corporal    | **Poppins**       | `300` (light), `400` (regular), `500` (medium), `600` (semi-bold) | Google Fonts vía enlace CDN |

### 2.2 Escala tipográfica

| Elemento   | Tamaño (móvil)   | Tamaño (md+)     | Tailwind            | Font              |
|------------|------------------|------------------|---------------------|-------------------|
| h1         | `text-2xl` (1.5rem) | `text-4xl` (2.25rem) | `text-2xl md:text-4xl` | Lora 600      |
| h2         | `text-xl` (1.25rem) | `text-3xl` (1.875rem) | `text-xl md:text-3xl` | Lora 600      |
| h3         | `text-lg` (1.125rem)| `text-2xl` (1.5rem)   | `text-lg md:text-2xl`  | Lora 600      |
| Cuerpo     | `text-sm` (0.875rem)| `text-base` (1rem)    | `text-sm md:text-base` | Poppins 400   |
| Pequeño    | `text-xs` (0.75rem) | `text-sm` (0.875rem)  | `text-xs md:text-sm`   | Poppins 400   |
| Label      | `text-sm` (0.875rem)| `text-sm`             | `text-sm`              | Poppins 500   |

### 2.3 Enlace CDN

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Lora:wght@400;600&family=Poppins:wght@300;400;500;600&display=swap" rel="stylesheet" />
```

### 2.4 Clases base (para aplicar en `<body>`)

```html
<body class="font-['Poppins'] text-stone-900">
  <h1 class="font-['Lora'] font-semibold">...</h1>
</body>
```

---

## 3. Espaciado

### 3.1 Sistema de espaciado

Se usan los valores nativos de Tailwind (`p-{n}`, `m-{n}`, `gap-{n}`, `space-y-{n}`).

| Contexto               | Espaciado   | Tailwind             |
|------------------------|-------------|----------------------|
| Padding lateral página | 1rem / 1.5rem / 2rem | `px-4 sm:px-6 lg:px-8` |
| Entre secciones (gap vertical) | 3rem – 5rem | `py-12` / `py-16` / `py-20` |
| Entre cards (grid)     | 1rem – 1.5rem | `gap-4 sm:gap-6`    |
| Padding interno de card | 1rem – 1.5rem | `p-4 sm:p-6`        |
| Entre líneas de formulario | 1rem – 1.5rem | `space-y-4` / `gap-4` |
| Entre navbar y contenido | 2rem – 3rem | `py-8 sm:py-12` en `<main>` |

### 3.2 Alto mínimo de página

```html
<body class="flex min-h-screen flex-col">
  <main class="flex-1">
```

---

## 4. Navbar

### 4.1 Estructura visual

- **Fondo:** `bg-crema` / `bg-orange-50` (igual que la página) o blanco puro.
- **Borde inferior:** `border-b border-stone-200`.
- **Padding vertical:** `py-3` móvil, `py-4` escritorio.
- **Logo:** Lora 600, color `text-stone-900`, tamaño `text-lg sm:text-xl`.
- **Enlaces de navegación:** Poppins 400, `text-sm`, `hover:text-red-700`.
- **Barra de búsqueda:** Input `border-stone-300`, `rounded`, `px-3 py-2`, fondo `bg-white`. Botón de búsqueda `bg-stone-100 hover:bg-stone-200 text-stone-700`, `border border-stone-300`.
- **Menú cuenta:** Implementado con `<details>` nativo:
  - `summary`: Poppins 500, `text-sm`, cursor pointer, borde sutil.
  - Dropdown: `bg-white`, `border-stone-200`, `shadow-sm`, `rounded`, enlaces `hover:text-red-700`.

### 4.2 Maqueta conceptual (HTML/Tailwind)

```html
<header class="border-b border-stone-200 bg-orange-50">
  <nav class="mx-auto flex w-full max-w-7xl flex-wrap items-center gap-4 px-4 py-3 sm:px-6 sm:py-4 lg:px-8">
    <a href="index.html" class="shrink-0 font-['Lora'] text-lg font-semibold text-stone-900 sm:text-xl">LadyBug Shop</a>
    <!-- enlaces, búsqueda, cuenta… -->
  </nav>
</header>
```

---

## 5. Footer

### 5.1 Estructura visual

- **Fondo:** `bg-orange-100` (crema oscuro).
- **Borde superior:** `border-t border-stone-200`.
- **Padding:** `py-10` – `py-12`.
- **Distribución:** Grid responsive: 1 columna móvil, 2 columnas `sm:`, 3–4 columnas `lg:`.
- **Títulos de sección:** Poppins 600, `text-sm`, `uppercase`, `tracking-wider`, `text-stone-700`.
- **Enlaces:** Poppins 400, `text-sm`, `text-stone-600`, `hover:text-red-700`.
- **Contacto:** Texto plano, `text-sm text-stone-600`.

### 5.2 Columnas

| Sección      | Contenido                                                                 |
|--------------|---------------------------------------------------------------------------|
| Categorías   | Calzado, Camisas, Pantalones, Accesorios (enlaces a `catalogo.html?categoria=...`) |
| Legal        | Términos y condiciones, Política de privacidad, Sobre la marca (sin páginas) |
| Contacto     | Texto pendiente de definir                                                |

---

## 6. Cards de producto

### 6.1 Estructura visual

- **Fondo:** `bg-white` (o `bg-orange-50` para variante sobre fondo alterno).
- **Borde:** `border border-stone-200`, `rounded-lg`.
- **Sombra:** `shadow-sm`, hover `shadow-md`.
- **Padding interno:** `p-4`.
- **Transición hover:** `transition-shadow duration-200` (la sombra se intensifica).

### 6.2 Contenido de la card

1. **Bloque de imagen** (ver sección 7).
2. **Nombre del producto:** Poppins 500, `text-sm`, `text-stone-900`.
3. **Precio:** Poppins 400, `text-sm`, `text-stone-600`.
4. **Botón "Añadir" / enlace:** Botón secundario o primario pequeño.

```html
<article class="rounded-lg border border-stone-200 bg-white p-4 shadow-sm transition-shadow duration-200 hover:shadow-md">
  <div class="mb-3 aspect-[3/4] w-full rounded-md bg-gradient-to-br from-amber-100 to-stone-200 flex items-center justify-center">
    <span class="text-stone-400 text-xs">Imagen del producto</span>
  </div>
  <h3 class="font-['Poppins'] text-sm font-medium text-stone-900">Nombre del producto</h3>
  <p class="mt-1 text-sm text-stone-500">39,99 €</p>
  <a href="producto.html" class="mt-3 inline-block rounded bg-red-700 px-4 py-2 text-xs font-medium text-white hover:bg-red-800">Ver producto</a>
</article>
```

### 6.3 Grid de cards

```html
<div class="grid grid-cols-2 gap-4 sm:grid-cols-3 lg:grid-cols-4">
  <!-- cards aquí -->
</div>
```

---

## 7. Bloques de imagen (placeholders sin fotos)

### 7.1 Principios

- No se usan imágenes reales ni externas.
- Cada bloque de imagen es un `div` con fondo gradiente o color sólido.
- Lleva un texto indicativo dentro (ej. "Imagen del producto", "Foto próx.").
- Relación de aspecto definida: `aspect-[3/4]` para productos, `aspect-video` para hero, `aspect-square` para thumbnails.
- Atributos HTML de accesibilidad: `role="img"` + `aria-label` descriptivo.

### 7.2 Variantes de bloque

| Uso                  | Aspecto      | Gradiente / Color                                            |
|----------------------|--------------|--------------------------------------------------------------|
| Hero (Home)          | `aspect-video` (16:9) | `bg-gradient-to-br from-amber-100 via-orange-100 to-stone-200` |
| Card de producto     | `aspect-[3/4]` (4:3 vertical) | `bg-gradient-to-br from-amber-100 to-stone-200`        |
| Detalle de producto  | `aspect-[4/5]` | `bg-gradient-to-br from-amber-50 via-orange-50 to-stone-100` |
| Thumbnail carrito    | `aspect-square` | `bg-stone-100` con borde `border border-stone-200`      |

### 7.3 Etiqueta de estado

```html
<div class="aspect-[3/4] w-full rounded-md bg-gradient-to-br from-amber-100 to-stone-200 flex items-center justify-center" role="img" aria-label="Lugar reservado para imagen del producto">
  <svg class="h-8 w-8 text-stone-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M2.25 15.75l5.159-5.159a2.25 2.25 0 013.182 0l5.159 5.159m-1.5-1.5l1.409-1.409a2.25 2.25 0 013.182 0l2.909 2.909M3.75 21h16.5A2.25 2.25 0 0022.5 18.75V5.25A2.25 2.25 0 0020.25 3H3.75A2.25 2.25 0 001.5 5.25v13.5A2.25 2.25 0 003.75 21z" />
  </svg>
  <span class="ml-2 text-xs text-stone-400">Foto próximamente</span>
</div>
```

---

## 8. Botones

### 8.1 Variantes

| Variante      | Clases Tailwind                                                      | Uso                            |
|---------------|----------------------------------------------------------------------|--------------------------------|
| Primario      | `bg-red-700 text-white hover:bg-red-800 rounded px-5 py-2.5 text-sm font-medium transition-colors duration-150` | Añadir al carrito, checkout, confirmar |
| Secundario    | `border border-stone-300 text-stone-700 hover:bg-stone-100 rounded px-5 py-2.5 text-sm font-medium transition-colors duration-150` | Volver, continuar comprando     |
| Outline       | `border border-red-700 text-red-700 hover:bg-red-50 rounded px-5 py-2.5 text-sm font-medium transition-colors duration-150` | Acciones secundarias destacadas |
| Texto         | `text-red-700 hover:text-red-800 underline underline-offset-2 text-sm` | Enlaces de acción dentro de texto |

### 8.2 Tamaños

| Tamaño   | Clases                     |
|----------|----------------------------|
| Pequeño  | `px-3 py-1.5 text-xs`      |
| Normal   | `px-5 py-2.5 text-sm`      |
| Grande   | `px-7 py-3 text-base`      |

---

## 9. Formularios

### 9.1 Estilo de inputs

- **Fondo:** `bg-white`.
- **Borde:** `border border-stone-300`, `rounded`, `rounded-md` o `rounded-lg` según contexto.
- **Padding:** `px-3 py-2.5`.
- **Texto:** `text-sm text-stone-900`.
- **Placeholder:** `placeholder:text-stone-400`.
- **Focus:** `outline-none ring-2 ring-red-700/30 border-red-700`.
- **Label:** Poppins 500, `text-sm text-stone-700`, `mb-1`.

### 9.2 Grupos de formulario

```html
<div class="space-y-1">
  <label for="email" class="font-['Poppins'] text-sm font-medium text-stone-700">Correo electrónico</label>
  <input
    id="email"
    type="email"
    placeholder="tu@correo.com"
    class="w-full rounded-md border border-stone-300 bg-white px-3 py-2.5 text-sm text-stone-900 placeholder:text-stone-400 focus:border-red-700 focus:outline-none focus:ring-2 focus:ring-red-700/30"
  />
</div>
```

### 9.3 Estados de error

```html
<div class="space-y-1">
  <label for="email" class="font-['Poppins'] text-sm font-medium text-stone-700">Correo electrónico</label>
  <input
    id="email"
    type="email"
    aria-invalid="true"
    aria-describedby="email-error"
    class="w-full rounded-md border border-red-800 bg-white px-3 py-2.5 text-sm text-stone-900 placeholder:text-stone-400 focus:border-red-800 focus:outline-none focus:ring-2 focus:ring-red-800/30"
  />
  <p id="email-error" class="text-xs text-red-800" role="alert">Este campo es obligatorio</p>
</div>
```

---

## 10. Checkout (3 pasos)

### 10.1 Estructura visual

- **Paso actual:** Label "Paso X de 3" + indicador visual (barras de progreso, números circulares o similar).
- **Paso completado:** Color éxito (`text-green-800`), icono check o marcado visual.
- **Paso activo:** Color primario (`text-red-700` / `bg-red-700`).
- **Paso pendiente:** Color neutro (`text-stone-400` / `bg-stone-200`).

### 10.2 Layout del formulario

- Cada paso es una sección dentro de `checkout.html` con `display: none` / `block` (simulado con CSS o simplemente markup secuencial para el prototipo visual).
- Los botones de navegación entre pasos son solo markup (sin funcionalidad real).

---

## 11. Responsive

### 11.1 Breakpoints

| Breakpoint | Tailwind  | Orientación                       |
|------------|-----------|-----------------------------------|
| Móvil      | — (base)  | vertical, 320px–639px             |
| Tablet     | `sm:`     | 640px–1023px                      |
| Escritorio | `md:`     | 1024px+ (con `lg:` para ajustes)  |

### 11.2 Reglas específicas

- **Contenedor máximo:** `max-w-7xl` (`mx-auto` centrado).
- **Padding lateral:** `px-4` móvil, `px-6` tablet, `px-8` escritorio.
- **Grids:** `grid-cols-2` móvil, `sm:grid-cols-3`, `lg:grid-cols-4` para catálogo.
- **Navbar:** En móvil los enlaces de navegación pueden colapsar debajo de la fila del logo + búsqueda (flex wrap). El menú cuenta siempre es un `details`.
- **Footer:** `grid-cols-1` móvil, `sm:grid-cols-2`, `lg:grid-cols-3` o `4`.
- **Prohibido el scroll horizontal:** `overflow-x-hidden` en `<body>` si es necesario; asegurar que ningún elemento desborde sin `max-w-full`.

---

## 12. Migración desde el prototipo inicial

Las vistas existentes (`index.html`, `catalogo.html`, etc.) usan una paleta `zinc`/`white` neutra. Cuando se aplique este design system:

| Elemento actual       | Reemplazar por             |
|-----------------------|----------------------------|
| `bg-white`            | `bg-orange-50`             |
| `text-zinc-900`       | `text-stone-900`           |
| `text-zinc-700`       | `text-stone-600`           |
| `border-zinc-200`     | `border-stone-200`         |
| `border-zinc-300`     | `border-stone-300`         |
| `bg-zinc-50`          | `bg-orange-100`            |
| `hover:bg-zinc-100`   | `hover:bg-stone-100`       |
| Tipografía sistema    | `font-['Poppins']` / `font-['Lora']` |

---

## 13. Resumen visual (mock conceptual)

> **Nota:** No hay mockup en Figma ni diseño de referencia. Este documento sirve como guía de estilo escrita para que cada miembro del equipo desarrolle su vista de forma consistente. Ante cualquier ambigüedad, priorizar:
> 1. Este documento (DESIGN.md)
> 2. CONTEXT.md
> 3. AGENTS.md
