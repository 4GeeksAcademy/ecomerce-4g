# Plan de implementación — Base Layout

> Proyecto: **LadyBug Shop** · Dirección visual: **Boulevard Bohème**

---

## 🔷 FASE 0 — Criterios previos (acuerdos del equipo)

> **Antes de escribir cualquier código**, el equipo debe consensuar:

| # | Tarea | Propuesta basada en docs |
|---|-------|--------------------------|
| 0.1 | **Acordar orden del checkout** | La documentación ya lo define: *Información de envío → Método de pago → Resumen* (AGENTS.md). Confirmar y documentar. |
| 0.2 | **Definir versión exacta de Tailwind CDN** | Proponer una versión concreta (ej. `@4.0.0` o la última estable). Se fijará en `spec.md` RP-02. |
| 0.3 | **Acordar cómo se permite JSON-LD** | AGENTS.md dice que JSON-LD va dentro de `<script type="application/ld+json">`. Es un script técnico (datos estructurados), no funcional. Confirmar que se permite como excepción a RT-02 (el único script es Tailwind). |
| 0.4 | **Definir contenido del footer (Contacto)** | Actualmente dice "Pendiente de definir". Proponer: "contacto@ladybug.fr" o similar hasta que el cliente decida. |
| 0.5 | **Acordar el color de borde** | `spec.md` §12 menciona discrepancia: DESIGN.md usa `border-stone-200`, AGENTS.md usa `stone-300`. Propuesta del spec: `stone-200` para layout, `stone-300` para inputs. |
| 0.6 | **Definir método de publicación para PageSpeed** | Decidir si se despliega en GitHub Pages, Codespace público o similar para ejecutar PageSpeed Insights. |

---

## 🔷 FASE 1 — Plantilla base compartida (`feature/layout-base`)

> **Objetivo:** Crear `docs/reference/base.html` con todo el HTML compartido.

| # | Tarea | Descripción | Ref. spec.md |
|---|-------|-------------|--------------|
| 1.1 | **Estructura del documento** | `<!DOCTYPE html>`, `<html lang="es">`, `<head>` con charset, viewport, title placeholder, meta description placeholder. | RD-01 a RD-05 |
| 1.2 | **Google Fonts** | Precargas (`preconnect`) a `fonts.googleapis.com` y `fonts.gstatic.com`, hoja de estilos con Lora 400/600 + Poppins 300/400/500/600, `display=swap`. | RD-06 |
| 1.3 | **Body base** | `class="flex min-h-screen flex-col overflow-x-hidden bg-orange-50 font-['Poppins'] text-stone-900"`. | RD-07 |
| 1.4 | **Skip-to-content link** | Enlace "Saltar al contenido" → `#contenido`, clases `sr-only focus:not-sr-only`. | RM-03, RD-08 |
| 1.5 | **Navbar — estructura** | `<header>` con `<nav aria-label="Principal">`, contenedor responsive, logo texto "LadyBug Shop" → `index.html`. | RN-01 a RN-03 |
| 1.6 | **Navbar — búsqueda** | `<form role="search" action="catalogo.html" method="get">`, input con label `sr-only`, botón submit. Estilos según DESIGN.md §4.1. | RN-04 a RN-06 |
| 1.7 | **Navbar — enlaces** | `<ul>` con 5 enlaces: Inicio, Catálogo, Producto, Carrito, Checkout. Estilo `text-sm hover:text-red-700`. Comentario HTML para `aria-current`. | RN-07, RN-10 |
| 1.8 | **Navbar — menú cuenta** | `<details>`/`<summary>` nativo, panel con enlaces a carrito y checkout. Posicionamiento `absolute` para no desplazar layout (evitar CLS). | RN-08, RN-09, RP-06 |
| 1.9 | **Navbar — responsive** | Móvil: logo + menú cuenta fila 1, búsqueda fila 2, enlaces fila 3. `md:`/`lg:` todo en una fila. Sin overflow a 320px. | RN-11, RN-12 |
| 1.10 | **`<main>` vacío** | `<main id="contenido" class="flex-1">` vacío con comentarios de uso. Sin `<h1>`. | RM-01, RM-02, RD-09 |
| 1.11 | **Footer — estructura** | `<footer>` con grid responsive: 1 col (base), 2 (`sm:`), 3 (`lg:`). | RF-01, RF-02 |
| 1.12 | **Footer — Categorías** | Columna con enlaces a `catalogo.html?categoria=calzado|camisas|pantalones|accesorios`. | RF-04 |
| 1.13 | **Footer — Legal** | Texto plano: Términos, Privacidad, Sobre la marca (sin enlaces). | RF-05 |
| 1.14 | **Footer — Contacto** | Texto pendiente (acordado en Fase 0). | RF-06 |
| 1.15 | **Footer — Copyright** | Línea inferior con "© LadyBug Shop · París". | RF-07 |
| 1.16 | **Rendimiento** | Preconnect a jsDelivr + versión fija de Tailwind. DOM ligero (< 150 nodos navbar+footer). HTML < 15 KB. | RP-01 a RP-10 |
| 1.17 | **Accesibilidad** | Contraste AA, foco visible (`focus-visible:ring-2`), landmarks semánticos, áreas táctiles ≥ 24px. | RA-01 a RA-06 |
| 1.18 | **Validación y PageSpeed** | Validar HTML (W3C), testear 320-1440px (sin scroll horizontal), publicar y medir PageSpeed ≥ 80. Adjuntar capturas en PR. | §8.3, §11 |

---

## 🔷 FASE 2 — Vistas

| # | Vista | Rama | Descripción |
|---|-------|------|-------------|
| 2.1 | **Home** | `feature/home` | Hero, «Nuevos lanzamientos», «Más vendidos» y JSON-LD `Organization`. |
| 2.2 | **Catálogo** | `feature/catalogo` | Filtros de categoría y talla, rejilla adaptable de productos y enlaces a las fichas. |
| 2.3 | **Producto** | `feature/producto` | Imagen placeholder, datos del artículo, selección de talla y cantidad, descripción y JSON-LD `Product`. |
| 2.4 | **Carrito** | `feature/carrito` | Tres artículos de ejemplo, cantidades y totales por línea, resumen y botón que lleva al checkout. |
| 2.5 | **Checkout** | `feature/checkout` | Tres pasos visuales y formularios semánticos, sin procesamiento real de pagos. |

---

## 🔷 FASE 3 — Integración y verificación

| # | Tarea | Detalle |
|---|-------|---------|
| 3.1 | **Sincronizar con `main`** | Cada rama de vista debe actualizarse desde `main` antes de abrir su PR. |
| 3.2 | **Commits descriptivos** | Usar mensajes claros, sin force-push. Resolver conflictos en equipo. |
| 3.3 | **Comprobar enlaces entre vistas** | Verificar que todos los enlaces entre las 5 páginas funcionan, incluyendo búsqueda GET (`?q=`) y filtros de categoría (`?categoria=`). |
| 3.4 | **Pruebas responsive** | Probar cada vista en móvil (320px), tablet (768px) y escritorio (1440px). |
| 3.5 | **Validación final** | Validar HTML, contraste de accesibilidad, datos estructurados JSON-LD (Organization + Product). |
| 3.6 | **PageSpeed final** | Medir rendimiento en vistas publicadas. Meta: ≥ 80 en móvil y escritorio para todas. |

---

## 🔷 FASE 4 — Límites del alcance (restricciones)

| # | Regla |
|---|-------|
| 4.1 | No modificar `server.py`, `learn.json`, `README*`. |
| 4.2 | No añadir JavaScript propio, frameworks, build tools, fotos externas ni CSS personalizado no acordado. |
| 4.3 | La plantilla base es un **artefacto de referencia**, no una sexta vista. |
| 4.4 | Cualquier cambio en navbar/footer se hace **primero** en `base.html` y se propaga a todas las vistas. |

---

## 👥 Asignación de vistas para 3 desarrolladores

| Desarrollador | Vistas | Relación entre ellas |
|---------------|--------|---------------------|
| **👤 Dev A** 🏠 | **Home** (`feature/home`) + **Carrito** (`feature/carrito`) | **Relación:** Home es la puerta de entrada a la tienda (hero, novedades, más vendidos). Carrito es donde el usuario revisa su selección antes de comprar. Ambos son **puntos de anclaje** del recorrido — el primero y el penúltimo paso. Además, Home necesita JSON-LD `Organization` (datos de la marca) y Carrito es el único que no requiere JSON-LD, lo que balancea la carga. |
| **👤 Dev B** 🛍️ | **Catálogo** (`feature/catalogo`) + **Checkout** (`feature/checkout`) | **Relación:** Catálogo lista productos con filtros y búsqueda; Checkout es el formulario final de compra. Ambos comparten **patrones de formulario/filtro** (inputs, selects, labels, botones), lo que permite reutilizar estilos y lógica de marcado. Catálogo tiene la rejilla de productos, Checkout tiene los 3 pasos visuales — ambos requieren maquetación estructurada. |
| **👤 Dev C** 👕 | **Producto** (`feature/producto`) | **Relación:** Es la página más densa y autónoma: imagen placeholder, selección de talla, cantidad, descripción, JSON-LD `Product`. Al ser una sola vista, el desarrollador puede **dedicarse en profundidad** a los detalles finos (accesibilidad, datos estructurados, estados hover/focus). Sirve además como **validador** independiente — si hay bugs en navbar/footer, este dev los detecta al copiar la plantilla base. |

### Justificación de la agrupación

```
Home ──→ Catálogo ──→ Producto ──→ Carrito ──→ Checkout
 ①                           ③        ②
 (Dev A)                    (Dev C)   (Dev A)
         (Dev B) →→→→→→→→→→→→→→→→→→ (Dev B)
```

- **Dev A** cubre los **extremos** del recorrido (entrada y revisión final antes de pagar).
- **Dev B** cubre el **"embudo"** central (listado de productos → formulario de compra).
- **Dev C** cubre el **detalle individual** del producto, que es la vista más compleja en solitario.