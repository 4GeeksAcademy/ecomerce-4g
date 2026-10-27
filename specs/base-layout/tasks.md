# Tareas del proyecto

## Criterios previos
- [ ] Acordar el orden del checkout: datos personales, dirección y tarjeta, o envío, pago y resumen.
- [ ] Definir la versión concreta del CDN de Tailwind.
- [ ] Acordar cómo se permite JSON-LD en Home y Producto, considerando la limitación de scripts de la plantilla.
- [ ] Definir cómo se publicarán las páginas para medir PageSpeed y quién adjuntará los resultados en las PR.

## Plantilla compartida
- [ ] En `feature/layout-base`, crear `docs/reference/base.html` con metadatos, fuentes, navbar, `<main>` vacío, footer y enlace para saltar al contenido.
- [ ] Incluir enlaces a las cinco vistas, búsqueda GET al catálogo, menú nativo `<details>` y enlaces de categorías.
- [ ] Revisar semántica y accesibilidad; validar el HTML, la búsqueda y el layout entre 320 y 1440 px.
- [ ] Publicar la plantilla, medir PageSpeed en móvil y escritorio y abrir una PR con capturas. Alcanzar Rendimiento ≥80.

## Vistas
- [ ] **Home (`feature/home`):** implementar hero, «Nuevos lanzamientos», «Más vendidos» y JSON-LD `Organization`.
- [ ] **Catálogo (`feature/catalogo`):** implementar filtros de categoría y talla, rejilla adaptable de productos y enlaces a las fichas.
- [ ] **Producto (`feature/producto`):** implementar imagen placeholder, datos del artículo, selección de talla y cantidad, descripción y JSON-LD `Product`.
- [ ] **Carrito (`feature/carrito`):** implementar tres artículos de ejemplo, cantidades y totales por línea, resumen y botón que lleva al checkout.
- [ ] **Checkout (`feature/checkout`):** implementar tres pasos visuales y formularios semánticos, sin procesamiento real de pagos.
- [ ] En cada vista, personalizar título, descripción, H1 y enlace activo, manteniendo el header y footer canónicos sin cambios.

## Integración y verificación
- [ ] Actualizar cada rama desde `main` antes de abrir su PR.
- [ ] Usar commits descriptivos y resolver conflictos en equipo, sin force-push.
- [ ] Comprobar enlaces entre vistas, búsqueda GET y parámetros de categoría.
- [ ] Probar las vistas en móvil, tablet y escritorio.
- [ ] Validar HTML, accesibilidad y datos estructurados.
- [ ] Medir PageSpeed en las páginas publicadas; alcanzar Rendimiento ≥80 en móvil y escritorio para la plantilla y las vistas.

## Límites del alcance
- [ ] Mantener el prototipo en HTML y Tailwind, sin JavaScript propio, frameworks, build tools, fotos externas ni CSS personalizado no acordado.
- [ ] Tratar la plantilla base como artefacto de referencia, no como una sexta vista.
- [ ] Definir el contenido de contacto del footer.
