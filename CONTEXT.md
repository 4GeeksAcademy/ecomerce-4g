# Contexto del proyecto — LadyBug Shop

## Cliente

- **Nombre de la marca:** LadyBug
- **Sede:** París, Francia
- **Producto:** Ropa (calzado, camisas, pantalones, accesorios)
- **Encargo:** Prototipo de tienda online con 5 vistas

## Equipo y flujo de trabajo

- **Tamaño del equipo:** 3 personas
- **Estrategia de ramas:** una rama por vista
- **Integración:** una pull request por cada rama
- **Rama base del layout compartido:** `feature/layout-base` (creada)
- **Pull request:** se abrirán desde cada rama de vista contra `main`

## Vistas del prototipo

| # | Vista             | Archivo            | Rama ejemplo           |
|---|-------------------|--------------------|------------------------|
| 1 | Home              | `index.html`       | `feature/home`         |
| 2 | Catálogo          | `catalogo.html`    | `feature/catalogo`     |
| 3 | Vista de producto | `producto.html`    | `feature/producto`     |
| 4 | Carrito           | `carrito.html`     | `feature/carrito`      |
| 5 | Checkout (3 pasos)| `checkout.html`    | `feature/checkout`     |

Los 3 pasos del checkout son:

1. Información de envío
2. Método de pago
3. Resumen

## Tecnología

- **HTML5** semántico (`header`, `nav`, `main`, `section`, `article`, `footer`, `form`)
- **Tailwind CSS v4** vía CDN: `https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4`
- **Sin JavaScript.** No se escribe JS propio, no se usan frameworks ni librerías de componentes.
- **Sin CSS personalizado** salvo que sea estrictamente indispensable y se acuerde.
- **Sin fotografías.** El prototipo es solo HTML y Tailwind. Las imágenes placeholder pueden generarse con fondos o gradientes CSS si hacen falta.

## Diseño y estilo

### Paleta de colores

**Pendiente de definir por el equipo.** Se recomienda partir de una gama inspirada en la mariquita (*ladybug*): rojo (#E63946), blanco, grises neutros y negro para detalles. Hasta que se decida, los prototipos usarán clases utilitarias de Tailwind (`bg-white`, `text-zinc-*`, `border-zinc-*`, `bg-zinc-50`).

### Tipografía

- Textos generales: **Poppins** (Google Fonts vía `@import` o enlace CDN)
- Títulos o acentos: **Lora** (Google Fonts)

> Si se opta por no cargar fuentes externas, se usará la pila de sistema `font-sans` de Tailwind.

### Enfoque responsive

- **Mobile-first.** Los estilos base son para móvil; se añaden puntos de ruptura con `sm:`, `md:` y `lg:`.
- Sin scroll horizontal en ningún tamaño de pantalla.

## SEO

- Idioma: `lang="es"` en todas las páginas.
- Cada página lleva su propia `meta description`.
- Datos estructurados JSON-LD:
  - `Organization` en `index.html`.
  - `Product` en `producto.html`.
- Datos de ejemplo para JSON-LD:
  - **Nombre de la organización:** LadyBug Shop
  - **URL:** `https://ladybug.fr`
  - **Nombre del producto:** *Pendiente de definir* (placeholder)

## Estructura compartida (navbar y footer)

Todas las vistas comparten exactamente el mismo `header` (navbar) y `footer`. No deben modificarse dentro de la tarea de una vista concreta.

### Navbar (header)

- Logo / nombre de la marca (enlace a `index.html`)
- Barra de búsqueda (`<form role="search">` que apunta a `catalogo.html` vía GET)
- Menú de cuenta de usuario (implementado con `<details>` nativo, sin JS):
  - Mi carrito
  - Checkout
- Enlaces de navegación: Inicio, Catálogo, Producto, Carrito, Checkout

### Footer

- **Categorías:** Calzado, Camisas, Pantalones, Accesorios (enlazan a `catalogo.html` con filtro `?categoria=...`)
- **Legal:** Términos y condiciones, Política de privacidad, Sobre la marca (texto plano; sin páginas de destino)
- **Contacto:** Pendiente de definir

## Reglas de imágenes

Cuando se añadan imágenes en vistas futuras:
- Atributo `alt` descriptivo.
- `width` y `height` explícitos.
- `loading="lazy"` (salvo la imagen hero de Home).
- Si no hay fotografías reales, usar SVG inline o fondos CSS (pero **no** imágenes externas de stock).

## Archivos del proyecto (a fecha de este documento)

```
AGENTS.md
CONTEXT.md                 ← este archivo
index.html
catalogo.html
producto.html
carrito.html
checkout.html
server.py                  ← servidor Flask (dependencia opcional para desarrollo)
README.es.md
README.md
README.cn.md
learn.json
```

## Notas

- El prototipo es exclusivamente visual. No hay lógica de carrito, búsqueda ni checkout funcional.
- Los placeholders de marca, paleta y tipografía deben actualizarse cuando el equipo tome decisiones definitivas.
- Cualquier desviación de estas reglas debe reflejarse primero en `AGENTS.md` y después en `CONTEXT.md`.