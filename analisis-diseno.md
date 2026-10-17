# Mini CSS 1.0 — análisis y patrón de diseño

## 1. Mini como origen visual
Las cinco fotografías muestran pelaje blanco crema, manchas negras, naranja/caramelo, nariz rosada y collar frambuesa. La luz interior es cálida: los HEX son una interpretación visual normalizada para interfaces, no valores medidos con carta de color ni una extracción estadística de todos los píxeles (que incluiría suelo y muebles). No se atribuyen al pelaje los colores ambientales de la habitación.

Concepto: pequeña y ágil → archivos compactos, dependencias cero, tipografía del sistema, controles claros, transiciones de 140 ms, componentes componibles y espacios generosos. Bordes de .75rem y curvas moderadas evocan suavidad; la asimetría calicó se reserva para identidad, no para alterar la lectura. Reparto recomendado: 70% superficies claras, 20% tinta/neutral, 10% acentos. Es una pauta compositiva, no una medición del pelaje.

## 2. Paleta completa y compatibilidad
7 familias × 11 tonos = 77 tokens base. Crema, tinta y jengibre vienen del pelaje; frambuesa del collar (no del pelaje). Salvia, azul pizarra y ámbar son extensiones funcionales armonizadas para éxito, información y advertencia. Danger y accent comparten frambuesa: el texto, icono y contexto deben distinguirlos.
Los tonos 50–400 mezclan el base con blanco al 95%, 88%, 72%, 52%, 28%; 500 es el base; 600–950 mezclan con negro al 12%, 26%, 42%, 60%, 74%. Mezcla de canales sRGB redondeados, no escala perceptualmente uniforme. Se guardan valores HEX estáticos: no requiere color-mix ni Sass.

Cada token `--mn-{familia}-{tono}` tiene `--mn-{familia}-{tono}-on` (blanco o tinta), elegido por mayor contraste. La utilidad `mn-bg-{familia}-{tono}` aplica ambos. `mn-text-*` solo aplica texto: su contraste depende del fondo. La tabla lista TODOS los pares de fondo/texto soportados por las utilidades; no significa que los 77×77 cruces sean accesibles.

| Familia | Tono | Fondo HEX | Texto HEX | Contraste |
|---|---:|---|---|---:|
| cream | 50 | #FEFEFE | #24211F | 15.87:1 |
| cream | 100 | #FEFDFC | #24211F | 15.75:1 |
| cream | 200 | #FCFBF7 | #24211F | 15.45:1 |
| cream | 300 | #FAF7F2 | #24211F | 14.97:1 |
| cream | 400 | #F8F3EC | #24211F | 14.50:1 |
| cream | 500 | #F5EFE4 | #24211F | 13.98:1 |
| cream | 600 | #D8D2C9 | #24211F | 10.65:1 |
| cream | 700 | #B5B1A9 | #24211F | 7.49:1 |
| cream | 800 | #8E8B84 | #24211F | 4.71:1 |
| cream | 900 | #62605B | #FFFFFF | 6.28:1 |
| cream | 950 | #403E3B | #FFFFFF | 10.66:1 |
| ink | 50 | #F4F4F4 | #24211F | 14.55:1 |
| ink | 100 | #E5E4E4 | #24211F | 12.61:1 |
| ink | 200 | #C2C1C0 | #24211F | 8.90:1 |
| ink | 300 | #969493 | #24211F | 5.30:1 |
| ink | 400 | #615F5E | #FFFFFF | 6.35:1 |
| ink | 500 | #24211F | #FFFFFF | 16.00:1 |
| ink | 600 | #201D1B | #FFFFFF | 16.76:1 |
| ink | 700 | #1B1817 | #FFFFFF | 17.65:1 |
| ink | 800 | #151312 | #FFFFFF | 18.52:1 |
| ink | 900 | #0E0D0C | #FFFFFF | 19.42:1 |
| ink | 950 | #090908 | #FFFFFF | 19.92:1 |
| ginger | 50 | #FBF6F4 | #24211F | 14.93:1 |
| ginger | 100 | #F6EAE4 | #24211F | 13.57:1 |
| ginger | 200 | #EBCFC1 | #24211F | 10.84:1 |
| ginger | 300 | #DCAC95 | #24211F | 7.91:1 |
| ginger | 400 | #CA8360 | #24211F | 5.28:1 |
| ginger | 500 | #B65322 | #FFFFFF | 4.94:1 |
| ginger | 600 | #A0491E | #FFFFFF | 6.06:1 |
| ginger | 700 | #873D19 | #FFFFFF | 7.74:1 |
| ginger | 800 | #6A3014 | #FFFFFF | 10.27:1 |
| ginger | 900 | #49210E | #FFFFFF | 13.93:1 |
| ginger | 950 | #2F1609 | #FFFFFF | 16.94:1 |
| rose | 50 | #FBF5F7 | #24211F | 14.86:1 |
| rose | 100 | #F5E6EB | #24211F | 13.26:1 |
| rose | 200 | #E8C5D1 | #24211F | 10.16:1 |
| rose | 300 | #D79CAF | #24211F | 7.06:1 |
| rose | 400 | #C36B87 | #000000 | 5.77:1 |
| rose | 500 | #AC3159 | #FFFFFF | 6.29:1 |
| rose | 600 | #972B4E | #FFFFFF | 7.58:1 |
| rose | 700 | #7F2442 | #FFFFFF | 9.40:1 |
| rose | 800 | #641C34 | #FFFFFF | 11.95:1 |
| rose | 900 | #451424 | #FFFFFF | 15.23:1 |
| rose | 950 | #2D0D17 | #FFFFFF | 17.77:1 |
| sage | 50 | #F5F7F6 | #24211F | 14.87:1 |
| sage | 100 | #E7EDE9 | #24211F | 13.48:1 |
| sage | 200 | #C6D5CC | #24211F | 10.51:1 |
| sage | 300 | #9EB7A8 | #24211F | 7.46:1 |
| sage | 400 | #6E927D | #24211F | 4.63:1 |
| sage | 500 | #35684A | #FFFFFF | 6.50:1 |
| sage | 600 | #2F5C41 | #FFFFFF | 7.70:1 |
| sage | 700 | #274D37 | #FFFFFF | 9.53:1 |
| sage | 800 | #1F3C2B | #FFFFFF | 12.07:1 |
| sage | 900 | #152A1E | #FFFFFF | 15.20:1 |
| sage | 950 | #0E1B13 | #FFFFFF | 17.72:1 |
| sky | 50 | #F4F7F8 | #24211F | 14.86:1 |
| sky | 100 | #E6EDEF | #24211F | 13.51:1 |
| sky | 200 | #C4D4DA | #24211F | 10.50:1 |
| sky | 300 | #9AB5C0 | #24211F | 7.43:1 |
| sky | 400 | #6790A1 | #24211F | 4.63:1 |
| sky | 500 | #2C657C | #FFFFFF | 6.44:1 |
| sky | 600 | #27596D | #FFFFFF | 7.68:1 |
| sky | 700 | #214B5C | #FFFFFF | 9.44:1 |
| sky | 800 | #1A3B48 | #FFFFFF | 11.91:1 |
| sky | 900 | #122832 | #FFFFFF | 15.27:1 |
| sky | 950 | #0B1A20 | #FFFFFF | 17.75:1 |
| amber | 50 | #FAF7F2 | #24211F | 14.97:1 |
| amber | 100 | #F2ECE0 | #24211F | 13.60:1 |
| amber | 200 | #E1D2B8 | #24211F | 10.75:1 |
| amber | 300 | #CBB385 | #24211F | 7.87:1 |
| amber | 400 | #B18D47 | #24211F | 5.16:1 |
| amber | 500 | #936000 | #FFFFFF | 5.37:1 |
| amber | 600 | #815400 | #FFFFFF | 6.56:1 |
| amber | 700 | #6D4700 | #FFFFFF | 8.23:1 |
| amber | 800 | #553800 | #FFFFFF | 10.76:1 |
| amber | 900 | #3B2600 | #FFFFFF | 14.35:1 |
| amber | 950 | #261900 | #FFFFFF | 17.19:1 |

### Roles y mezclas recomendadas

| Rol | Familia | Solid | Soft fondo/texto |
|---|---|---|---|
| primary | ginger | #B65322 / #FFFFFF | #FBF6F4 / #6A3014 |
| secondary | ink | #24211F / #FFFFFF | #F4F4F4 / #151312 |
| accent | rose | #AC3159 / #FFFFFF | #FBF5F7 / #641C34 |
| success | sage | #35684A / #FFFFFF | #F5F7F6 / #1F3C2B |
| info | sky | #2C657C / #FFFFFF | #F4F7F8 / #1A3B48 |
| warning | amber | #936000 / #FFFFFF | #FAF7F2 / #553800 |
| danger | rose | #AC3159 / #FFFFFF | #FBF5F7 / #641C34 |

Composiciones: crema + tinta + jengibre para marca; crema + tinta + frambuesa para acentos; superficies neutras + salvia para confirmaciones; superficies neutras + azul para información. No superponer naranja y frambuesa para texto pequeño. Los tonos muy claros sirven como superficies, no como texto sobre blanco. Los roles usan solid/base 500, soft/50 y bold/800; soft conserva fondo claro en modo oscuro para mantener pares previsibles, en vez de invertirlos automáticamente.

## 3. Análisis de Bulma y requisitos del patrón
Consulta: 16 de octubre de 2026, documentación oficial. Síntesis propia; no se copia su CSS. Bulma sirve de referencia arquitectónica, no de dependencia. Mini no es compatible directamente con sus nombres de clase ni ofrece paridad total.

| Área observada / requerida | Decisión para Mini |
|---|---|
| CSS utilizable desde un archivo | mini.css y mini.min.css sin instalación |
| Composición componente/modificador | mn-button + mn-primary + mn-soft; prefijo para reducir colisiones |
| Variables CSS y personalización | Primitivos cromáticos, roles locales, tema, fuente, espacios, radios y duración |
| Mobile-first | Base de una columna; rejilla de 12 desde 48rem; helper desktop desde 64rem |
| Flexbox y Grid | cluster, level, media, columns y grid automático |
| Tipografía / contenido | title 1–6, subtitle, display, content, código, listas y citas |
| Elementos | box, button, image, avatar, tag, alert, progress, table, skeleton estático |
| Componentes | breadcrumb, card, dropdown, menu, message, modal, navbar, pagination, panel y navegación en pestañas |
| Formularios | label, input, textarea, select, check, radio, file, range, fieldset, help y error |
| Helpers | Espaciado, color, alineación, flex, visibilidad, tamaño y lector de pantalla |
| Temas | Sistema por defecto; atributo data-mn-theme=light/dark para forzar |
| Modularidad | Fuente separada por secciones comentadas; un archivo distribuible. Sin pipeline Sass modular |
| Comportamientos | CSS independiente; details nativo; dialog con JS mínimo del consumidor |
| Accesibilidad | HTML semántico, labels, foco visible, texto de estados, reduce motion, skip link |
| Documentación | Demo real + snippet por sección + catálogo exhaustivo de clases |
| Distribución | CSS fuente/minificado, palette.json, HTML, análisis, README y licencia |
| Calidad | Pruebas de contraste numérico, referencias, navegador, temas y anchos; informe incluido |

Fuentes oficiales:
- https://bulma.io/ — presentación general y composición.
- https://bulma.io/documentation/ — inventario de elementos, componentes, formularios, layout y helpers.
- https://bulma.io/documentation/start/overview/ — un archivo CSS, doctype y viewport.
- https://bulma.io/documentation/features/color-palettes/ — variables, tonos y pares soft/bold/invert.
- https://bulma.io/documentation/start/responsiveness/ — enfoque mobile-first.

### Alcance y límites concretos
Mini cubre el inventario de la tabla con una implementación compacta propia. No replica cada variante de Bulma, su Sass, mixins, generador HSL, Smart Grid completo, extensiones ni compatibilidad con sus clases. Los breakpoints de Mini son propios. No hay router, validación de negocio, backend, tooltip, datepicker ni motor JavaScript. Las pestañas son enlaces de navegación, no paneles dinámicos. El dropdown nativo no implementa un menú ARIA de aplicación ni cierre al pulsar fuera. El skeleton es estático. El framework contiene un reset global pequeño (box-sizing, body y elementos nativos); no es un estilo aislado para insertar sin revisión en una aplicación existente.

## 4. Contrato de componentes
1. `mn-button`: siempre button para acciones o a con href para navegación. Para impedir clics usa disabled nativo, no solo mn-loading; añade aria-busy y un texto de carga. aria-disabled solo describe estado y requiere impedir navegación si se usa en enlaces.
2. `mn-alert` y `mn-message`: color + etiqueta textual; role=status o alert solo para avisos dinámicos apropiados.
3. `mn-card`: header/body/footer opcionales; imagen con alt y medidas.
4. `mn-input` / textarea / select: label con for/id; error con aria-invalid y aria-describedby. Las validaciones de negocio corresponden al consumidor.
5. `mn-table`: caption, th y scope; envolver para overflow.
6. `mn-modal`: usar dialog.showModal(), nombre accesible y cierre visible. El navegador maneja modalidad; probar teclado y lector de pantalla en los destinos reales.
7. `mn-dropdown` / `mn-details`: details + summary nativos; no añadir role=menu sin implementar su navegación.
8. `mn-tabs`: nav de enlaces y aria-current, sin simular tabs ARIA.
9. `mn-navbar`: cluster adaptable; no requiere menú hamburguesa. Los links pueden envolver.
10. `mn-columns`: hijo mn-col y mn-col-N (N=1..12); todos se apilan antes de 48rem.

## 5. Tokens, escala y estados
- Espacios 0–8: 0, .25, .5, .75, 1, 1.5, 2, 3, 4 rem.
- Radio base .75rem; redondo 999px. Fuente system-ui; interlineado base 1.6.
- Superficies y texto: --mn-bg, --mn-surface, --mn-subtle, --mn-text, --mn-muted, --mn-border, --mn-link.
- Otros: --mn-font, --mn-radius, --mn-shadow, --mn-speed, --mn-space-0..8.
- Color por componente: --_color, --_on, --_soft, --_bold (variables internas).
- Estados: hover, active, focus-visible, disabled, loading, invalid, details[open], dialog abierto y aria-current.
- Variantes de botón: mn-soft, mn-outline, mn-ghost, mn-small, mn-large, mn-rounded, mn-full. Outline/ghost usan el color de enlace del tema (decisión de accesibilidad); el modificador semántico afecta solid y soft.
- Temas automáticos por prefers-color-scheme si no hay atributo; manual por data-mn-theme en html. El atributo se aplica a la raíz, no a subárboles.
- Visibilidad: mn-hide-mobile <48rem; mn-hide-tablet >=48rem (incluye desktop); mn-hide-desktop >=64rem; mn-hidden siempre; mn-sr-only solo visual.
- Navegadores objetivo: versiones modernas con CSS Grid, custom properties y dialog. Sin garantía para IE o WebViews antiguos. No se declara certificación WCAG: los pares se verifican numéricamente; la accesibilidad final depende del contenido, la interacción y las pruebas reales.

## 6. Catálogo exhaustivo de clases
Las clases de la guía sin prefijo mn- son exclusivas de documentación, no forman parte del framework. Todas las clases mn- distribuidas se listan a continuación (el archivo minificado ofrece el mismo contrato).

Total: 402 clases.

### mn-bg-*

`mn-bg-amber-100`, `mn-bg-amber-200`, `mn-bg-amber-300`, `mn-bg-amber-400`, `mn-bg-amber-50`, `mn-bg-amber-500`, `mn-bg-amber-600`, `mn-bg-amber-700`, `mn-bg-amber-800`, `mn-bg-amber-900`, `mn-bg-amber-950`, `mn-bg-cream-100`, `mn-bg-cream-200`, `mn-bg-cream-300`, `mn-bg-cream-400`, `mn-bg-cream-50`, `mn-bg-cream-500`, `mn-bg-cream-600`, `mn-bg-cream-700`, `mn-bg-cream-800`, `mn-bg-cream-900`, `mn-bg-cream-950`, `mn-bg-ginger-100`, `mn-bg-ginger-200`, `mn-bg-ginger-300`, `mn-bg-ginger-400`, `mn-bg-ginger-50`, `mn-bg-ginger-500`, `mn-bg-ginger-600`, `mn-bg-ginger-700`, `mn-bg-ginger-800`, `mn-bg-ginger-900`, `mn-bg-ginger-950`, `mn-bg-ink-100`, `mn-bg-ink-200`, `mn-bg-ink-300`, `mn-bg-ink-400`, `mn-bg-ink-50`, `mn-bg-ink-500`, `mn-bg-ink-600`, `mn-bg-ink-700`, `mn-bg-ink-800`, `mn-bg-ink-900`, `mn-bg-ink-950`, `mn-bg-rose-100`, `mn-bg-rose-200`, `mn-bg-rose-300`, `mn-bg-rose-400`, `mn-bg-rose-50`, `mn-bg-rose-500`, `mn-bg-rose-600`, `mn-bg-rose-700`, `mn-bg-rose-800`, `mn-bg-rose-900`, `mn-bg-rose-950`, `mn-bg-sage-100`, `mn-bg-sage-200`, `mn-bg-sage-300`, `mn-bg-sage-400`, `mn-bg-sage-50`, `mn-bg-sage-500`, `mn-bg-sage-600`, `mn-bg-sage-700`, `mn-bg-sage-800`, `mn-bg-sage-900`, `mn-bg-sage-950`, `mn-bg-sky-100`, `mn-bg-sky-200`, `mn-bg-sky-300`, `mn-bg-sky-400`, `mn-bg-sky-50`, `mn-bg-sky-500`, `mn-bg-sky-600`, `mn-bg-sky-700`, `mn-bg-sky-800`, `mn-bg-sky-900`, `mn-bg-sky-950`

### mn-text-*

`mn-text-amber-100`, `mn-text-amber-200`, `mn-text-amber-300`, `mn-text-amber-400`, `mn-text-amber-50`, `mn-text-amber-500`, `mn-text-amber-600`, `mn-text-amber-700`, `mn-text-amber-800`, `mn-text-amber-900`, `mn-text-amber-950`, `mn-text-center`, `mn-text-cream-100`, `mn-text-cream-200`, `mn-text-cream-300`, `mn-text-cream-400`, `mn-text-cream-50`, `mn-text-cream-500`, `mn-text-cream-600`, `mn-text-cream-700`, `mn-text-cream-800`, `mn-text-cream-900`, `mn-text-cream-950`, `mn-text-ginger-100`, `mn-text-ginger-200`, `mn-text-ginger-300`, `mn-text-ginger-400`, `mn-text-ginger-50`, `mn-text-ginger-500`, `mn-text-ginger-600`, `mn-text-ginger-700`, `mn-text-ginger-800`, `mn-text-ginger-900`, `mn-text-ginger-950`, `mn-text-ink-100`, `mn-text-ink-200`, `mn-text-ink-300`, `mn-text-ink-400`, `mn-text-ink-50`, `mn-text-ink-500`, `mn-text-ink-600`, `mn-text-ink-700`, `mn-text-ink-800`, `mn-text-ink-900`, `mn-text-ink-950`, `mn-text-muted`, `mn-text-right`, `mn-text-rose-100`, `mn-text-rose-200`, `mn-text-rose-300`, `mn-text-rose-400`, `mn-text-rose-50`, `mn-text-rose-500`, `mn-text-rose-600`, `mn-text-rose-700`, `mn-text-rose-800`, `mn-text-rose-900`, `mn-text-rose-950`, `mn-text-sage-100`, `mn-text-sage-200`, `mn-text-sage-300`, `mn-text-sage-400`, `mn-text-sage-50`, `mn-text-sage-500`, `mn-text-sage-600`, `mn-text-sage-700`, `mn-text-sage-800`, `mn-text-sage-900`, `mn-text-sage-950`, `mn-text-sky-100`, `mn-text-sky-200`, `mn-text-sky-300`, `mn-text-sky-400`, `mn-text-sky-50`, `mn-text-sky-500`, `mn-text-sky-600`, `mn-text-sky-700`, `mn-text-sky-800`, `mn-text-sky-900`, `mn-text-sky-950`

### mn-col-*

`mn-col-1`, `mn-col-10`, `mn-col-11`, `mn-col-12`, `mn-col-2`, `mn-col-3`, `mn-col-4`, `mn-col-5`, `mn-col-6`, `mn-col-7`, `mn-col-8`, `mn-col-9`

### Espaciado

`mn-gap-0`, `mn-gap-1`, `mn-gap-2`, `mn-gap-3`, `mn-gap-4`, `mn-gap-5`, `mn-gap-6`, `mn-gap-7`, `mn-gap-8`, `mn-m-0`, `mn-m-1`, `mn-m-2`, `mn-m-3`, `mn-m-4`, `mn-m-5`, `mn-m-6`, `mn-m-7`, `mn-m-8`, `mn-mb-0`, `mn-mb-1`, `mn-mb-2`, `mn-mb-3`, `mn-mb-4`, `mn-mb-5`, `mn-mb-6`, `mn-mb-7`, `mn-mb-8`, `mn-ml-0`, `mn-ml-1`, `mn-ml-2`, `mn-ml-3`, `mn-ml-4`, `mn-ml-5`, `mn-ml-6`, `mn-ml-7`, `mn-ml-8`, `mn-mr-0`, `mn-mr-1`, `mn-mr-2`, `mn-mr-3`, `mn-mr-4`, `mn-mr-5`, `mn-mr-6`, `mn-mr-7`, `mn-mr-8`, `mn-mt-0`, `mn-mt-1`, `mn-mt-2`, `mn-mt-3`, `mn-mt-4`, `mn-mt-5`, `mn-mt-6`, `mn-mt-7`, `mn-mt-8`, `mn-mx-0`, `mn-mx-1`, `mn-mx-2`, `mn-mx-3`, `mn-mx-4`, `mn-mx-5`, `mn-mx-6`, `mn-mx-7`, `mn-mx-8`, `mn-my-0`, `mn-my-1`, `mn-my-2`, `mn-my-3`, `mn-my-4`, `mn-my-5`, `mn-my-6`, `mn-my-7`, `mn-my-8`, `mn-p-0`, `mn-p-1`, `mn-p-2`, `mn-p-3`, `mn-p-4`, `mn-p-5`, `mn-p-6`, `mn-p-7`, `mn-p-8`, `mn-pb-0`, `mn-pb-1`, `mn-pb-2`, `mn-pb-3`, `mn-pb-4`, `mn-pb-5`, `mn-pb-6`, `mn-pb-7`, `mn-pb-8`, `mn-pl-0`, `mn-pl-1`, `mn-pl-2`, `mn-pl-3`, `mn-pl-4`, `mn-pl-5`, `mn-pl-6`, `mn-pl-7`, `mn-pl-8`, `mn-pr-0`, `mn-pr-1`, `mn-pr-2`, `mn-pr-3`, `mn-pr-4`, `mn-pr-5`, `mn-pr-6`, `mn-pr-7`, `mn-pr-8`, `mn-pt-0`, `mn-pt-1`, `mn-pt-2`, `mn-pt-3`, `mn-pt-4`, `mn-pt-5`, `mn-pt-6`, `mn-pt-7`, `mn-pt-8`, `mn-px-0`, `mn-px-1`, `mn-px-2`, `mn-px-3`, `mn-px-4`, `mn-px-5`, `mn-px-6`, `mn-px-7`, `mn-px-8`, `mn-py-0`, `mn-py-1`, `mn-py-2`, `mn-py-3`, `mn-py-4`, `mn-py-5`, `mn-py-6`, `mn-py-7`, `mn-py-8`

### Componentes y otras utilidades

`mn-accent`, `mn-alert`, `mn-avatar`, `mn-between`, `mn-border`, `mn-box`, `mn-brand`, `mn-breadcrumb`, `mn-button`, `mn-card`, `mn-card-body`, `mn-card-footer`, `mn-card-header`, `mn-check`, `mn-close`, `mn-cluster`, `mn-col`, `mn-columns`, `mn-container`, `mn-content`, `mn-danger`, `mn-details`, `mn-display`, `mn-dropdown`, `mn-dropdown-menu`, `mn-eyebrow`, `mn-field`, `mn-fieldset`, `mn-file`, `mn-flex`, `mn-footer`, `mn-full`, `mn-ghost`, `mn-grid`, `mn-grow`, `mn-help`, `mn-hero`, `mn-hidden`, `mn-hide-desktop`, `mn-hide-mobile`, `mn-hide-tablet`, `mn-image`, `mn-info`, `mn-input`, `mn-invalid`, `mn-items-center`, `mn-label`, `mn-large`, `mn-level`, `mn-loading`, `mn-media`, `mn-menu`, `mn-message`, `mn-message-body`, `mn-message-header`, `mn-modal`, `mn-modal-body`, `mn-nav-link`, `mn-nav-list`, `mn-navbar`, `mn-outline`, `mn-pagination`, `mn-panel`, `mn-panel-heading`, `mn-panel-item`, `mn-primary`, `mn-progress`, `mn-radio`, `mn-range`, `mn-rounded`, `mn-secondary`, `mn-section`, `mn-select`, `mn-skeleton`, `mn-skip`, `mn-small`, `mn-soft`, `mn-sr-only`, `mn-stack`, `mn-striped`, `mn-subtitle`, `mn-success`, `mn-surface`, `mn-table`, `mn-table-wrap`, `mn-tabs`, `mn-tag`, `mn-textarea`, `mn-title`, `mn-title-1`, `mn-title-2`, `mn-title-3`, `mn-title-4`, `mn-title-5`, `mn-title-6`, `mn-warning`, `mn-weight-bold`, `mn-wrap`
