# 🐾 Mini CSS

**Pequeña. Ágil. Calicó.**

Un framework CSS sencillo y ligero inspirado en Mini, una gata calicó de pelaje crema, negro y naranja. Diseñado para construir interfaces cálidas y adaptables con clases fáciles de combinar.

**v1.0.0 · 402 clases · 77 tonos · Sin dependencias · Licencia MIT**

## Contenido

- [Características](#características)
- [Primeros pasos](#primeros-pasos)
- [Instalación](#instalación)
- [Cómo se usan las clases](#cómo-se-usan-las-clases)
- [Paleta de colores](#paleta-de-colores)
- [Componentes](#componentes)
- [Diseño adaptable](#diseño-adaptable)
- [Temas y personalización](#temas-y-personalización)
- [Accesibilidad](#accesibilidad)
- [Estructura del proyecto](#estructura-del-proyecto)
- [Estado y validación](#estado-y-validación)
- [Contribuciones](#contribuciones)
- [Licencia](#licencia)

## Características

- **Ligero:** aproximadamente 32 KB minificado y 6,1 KB con gzip. El tamaño gzip corresponde al transporte y requiere compresión en el servidor.
- **Sin dependencias:** no requiere Bulma, JavaScript, fuentes externas ni compilación para aplicar los estilos.
- **Móvil primero:** layouts con CSS Grid y Flexbox.
- **Identidad calicó:** 7 familias cromáticas con 11 tonos cada una.
- **Temas claro y oscuro:** selección manual o según la preferencia del sistema.
- **Componentes combinables:** botones, alertas, tarjetas, formularios, tablas y navegación.
- **Variables CSS:** colores, espacios, fuente, radios y duración de transiciones personalizables.
- **Guía incluida:** ejemplos visuales y fragmentos HTML copiables.

Mini CSS toma como referencia la composición de clases de [Bulma](https://bulma.io/), con una implementación propia. Sus nombres de clase y su alcance son independientes de Bulma.

## Primeros pasos

Descarga los archivos y abre [`index.html`](index.html) en un navegador moderno.

También puedes abrir [`guia-mini-autonoma.html`](guia-mini-autonoma.html): incorpora el CSS y la fotografía para consultar los ejemplos sin conexión. Sus enlaces a documentos complementarios requieren el resto de los archivos.

Para servir la guía localmente, ejecuta desde la carpeta del proyecto:

```bash
python -m http.server 8000
```

Abre [http://localhost:8000](http://localhost:8000).

## Instalación

Copia `mini.min.css` en tu proyecto e incluye el archivo en el `<head>`:

```html
<link rel="stylesheet" href="mini.min.css">
```

### Plantilla inicial

```html
<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Mi proyecto con Mini CSS</title>
  <link rel="stylesheet" href="mini.min.css">
</head>
<body>
  <main class="mn-container mn-section">
    <h1 class="mn-title">Hola, Mini 🐾</h1>
    <p class="mn-subtitle">Una interfaz pequeña con grandes ideas.</p>
    <a class="mn-button mn-primary" href="#contenido">Comenzar</a>

    <section id="contenido" class="mn-box mn-mt-6">
      <h2 class="mn-title mn-title-4">Tu siguiente proyecto</h2>
      <p>Empieza con un archivo CSS y unas pocas clases.</p>
    </section>
  </main>
</body>
</html>
```

> No se ofrece todavía un paquete npm ni una URL CDN oficial. La instalación de esta versión es mediante archivos locales.

## Cómo se usan las clases

Todas las clases del framework tienen el prefijo `mn-`.

Combina un **componente** con modificadores de **color**, **apariencia** y **tamaño**:

```html
<button class="mn-button mn-primary mn-soft mn-large">
  Guardar cambios
</button>
```

| Clase | Función |
| --- | --- |
| `mn-button` | Define el componente botón |
| `mn-primary` | Aplica el rol principal de la paleta |
| `mn-soft` | Usa fondo suave y texto oscuro |
| `mn-large` | Aumenta tamaño y espaciado del botón |

### Botones

```html
<button class="mn-button mn-primary">Principal</button>
<button class="mn-button mn-accent mn-soft">Acento suave</button>
<button class="mn-button mn-primary mn-outline">Contorno</button>
<button class="mn-button mn-primary mn-ghost">Discreto</button>
<button class="mn-button mn-primary mn-rounded">Redondo</button>
<button class="mn-button mn-primary mn-full">Ancho completo</button>
<button class="mn-button" disabled>Deshabilitado</button>
<button class="mn-button mn-primary mn-loading" disabled aria-busy="true">
  Guardando…
</button>
```

Tamaños: `mn-small`, predeterminado y `mn-large`. Las variantes `mn-outline` y `mn-ghost` usan el color de enlace del tema para mantener una lectura consistente.

### Títulos y texto

```html
<h1 class="mn-title">Título principal</h1>
<h2 class="mn-title mn-title-3">Título de sección</h2>
<p class="mn-subtitle">Texto introductorio</p>
<p class="mn-text-muted">Información secundaria</p>
```

`mn-title-1` a `mn-title-6` controlan el tamaño visual. El nivel HTML (`h1`, `h2`, etc.) debe reflejar la jerarquía del contenido.

### Alertas y etiquetas

```html
<div class="mn-alert mn-success" role="status">
  <strong>Éxito:</strong> los cambios se guardaron.
</div>

<div class="mn-alert mn-danger" role="alert">
  <strong>Error:</strong> no fue posible guardar los cambios.
</div>

<span class="mn-tag mn-info">Información</span>
```

Usa `role="alert"` para errores urgentes y `role="status"` para actualizaciones dinámicas no urgentes. Los avisos estáticos normalmente no requieren estos roles.

### Tarjetas

```html
<article class="mn-card">
  <header class="mn-card-header">Una nueva aventura</header>
  <div class="mn-card-body">
    <h2 class="mn-title mn-title-4">Explora con Mini</h2>
    <p>Una tarjeta con estructura sencilla.</p>
  </div>
  <footer class="mn-card-footer">
    <a class="mn-button mn-primary" href="detalles.html">Ver detalles</a>
  </footer>
</article>
```

Sustituye `detalles.html` por una ruta existente en tu aplicación.

### Formularios

```html
<div class="mn-field">
  <label class="mn-label" for="correo">Correo electrónico</label>
  <input
    class="mn-input"
    id="correo"
    name="correo"
    type="email"
    autocomplete="email"
    aria-describedby="correo-ayuda"
    required
  >
  <p class="mn-help" id="correo-ayuda">Ingresa un correo válido.</p>
</div>
```

Para un campo inválido, añade `aria-invalid="true"` y vincula el mensaje de error con `aria-describedby`. La aplicación debe implementar el envío y la validación de negocio.

### Espaciado

```html
<div class="mn-box mn-p-5 mn-mt-4">
  Contenido con padding y margen superior.
</div>
```

| Patrón | Significado | Ejemplo |
| --- | --- | --- |
| `mn-m-N` / `mn-p-N` | Margen / padding en todos los lados | `mn-p-4` |
| `mn-mx-N` / `mn-px-N` | Eje horizontal | `mn-px-5` |
| `mn-my-N` / `mn-py-N` | Eje vertical | `mn-my-6` |
| `mn-mt-N`, `mn-mr-N`, `mn-mb-N`, `mn-ml-N` | Margen por lado | `mn-mt-4` |
| `mn-pt-N`, `mn-pr-N`, `mn-pb-N`, `mn-pl-N` | Padding por lado | `mn-pb-3` |
| `mn-gap-N` | Separación en flex o grid | `mn-gap-4` |

`N` admite valores de **0 a 8**: `0`, `.25`, `.5`, `.75`, `1`, `1.5`, `2`, `3` y `4 rem`.

## Paleta de colores

Los colores son una interpretación visual de las fotografías de Mini, ajustada para interfaces. La iluminación cálida de las imágenes impide tratarlos como una medición calibrada del pelaje.

| Familia | Color base · 500 | Origen / uso |
| --- | --- | --- |
| `cream` | `#F5EFE4` | Pelaje claro; superficies cálidas |
| `ink` | `#24211F` | Manchas oscuras; texto y contraste |
| `ginger` | `#B65322` | Pelaje naranja; identidad principal |
| `rose` | `#AC3159` | Collar frambuesa; acento y error |
| `sage` | `#35684A` | Extensión funcional para éxito |
| `sky` | `#2C657C` | Extensión funcional para información |
| `amber` | `#936000` | Extensión funcional para advertencia |

Cada familia incluye los tonos **50, 100, 200, 300, 400, 500, 600, 700, 800, 900 y 950**.

```html
<div class="mn-bg-ginger-100 mn-p-4">Fondo suave con texto asignado</div>
<p class="mn-text-ink-800">Texto en tinta oscura</p>
```

```css
.mi-componente {
  background: var(--mn-ginger-100);
  color: var(--mn-ginger-100-on);
}
```

Las utilidades `mn-bg-*` asignan fondo y texto como pareja. Las utilidades `mn-text-*` solo cambian el texto: debes comprobar su contraste con el fondo elegido.

### Roles semánticos

| Clase | Familia | Uso recomendado |
| --- | --- | --- |
| `mn-primary` | `ginger` | Acciones principales |
| `mn-secondary` | `ink` | Acciones secundarias |
| `mn-accent` | `rose` | Acentos visuales |
| `mn-success` | `sage` | Confirmación |
| `mn-info` | `sky` | Información |
| `mn-warning` | `amber` | Advertencia |
| `mn-danger` | `rose` | Error o acción destructiva |

Consulta los 77 tonos y sus pares de contraste en [`analisis-diseno.md`](analisis-diseno.md), o reutiliza los valores de [`palette.json`](palette.json).

## Componentes

| Categoría | Componentes y clases principales |
| --- | --- |
| Estructura | `mn-container`, `mn-section`, `mn-hero`, `mn-footer` |
| Layout | `mn-grid`, `mn-columns`, `mn-col`, `mn-cluster`, `mn-stack`, `mn-level`, `mn-media` |
| Tipografía | `mn-title`, `mn-subtitle`, `mn-display`, `mn-content` |
| Acciones | `mn-button`, `mn-close` |
| Mensajes | `mn-alert`, `mn-message`, `mn-tag` |
| Contenido | `mn-box`, `mn-card`, `mn-image`, `mn-avatar` |
| Datos y carga | `mn-table`, `mn-progress`, `mn-skeleton` |
| Formularios | `mn-input`, `mn-textarea`, `mn-select`, `mn-check`, `mn-radio`, `mn-file`, `mn-range` |
| Navegación | `mn-navbar`, `mn-menu`, `mn-breadcrumb`, `mn-tabs`, `mn-pagination`, `mn-panel` |
| Interacción | `mn-details`, `mn-dropdown`, `mn-modal` |
| Utilidades | Espaciado, colores, flex, alineación, visibilidad y lectores de pantalla |

Los acordeones y desplegables usan `<details>` y `<summary>`. El modal usa `<dialog>` y requiere JavaScript para abrirlo:

```html
<button class="mn-button mn-primary" id="abrir-modal">Abrir modal</button>

<dialog class="mn-modal" id="mi-modal" aria-labelledby="titulo-modal">
  <div class="mn-modal-body">
    <h2 class="mn-title mn-title-4" id="titulo-modal">Hola, Mini</h2>
    <p>Un modal nativo con estilos de Mini CSS.</p>
    <form method="dialog">
      <button class="mn-button mn-primary" autofocus>Cerrar</button>
    </form>
  </div>
</dialog>

<script>
  const modal = document.querySelector('#mi-modal');
  document.querySelector('#abrir-modal').addEventListener('click', () => {
    modal.showModal();
  });
</script>
```

## Diseño adaptable

### Columnas de 12 unidades

```html
<div class="mn-columns">
  <main class="mn-col mn-col-8 mn-box">Contenido principal</main>
  <aside class="mn-col mn-col-4 mn-box">Información adicional</aside>
</div>
```

Las columnas se apilan en pantallas pequeñas. Desde `48rem`, `mn-col-1` a `mn-col-12` definen cuántas unidades ocupa cada elemento.

### Grid automático

```html
<div class="mn-grid">
  <article class="mn-box">Elemento A</article>
  <article class="mn-box">Elemento B</article>
  <article class="mn-box">Elemento C</article>
</div>
```

### Visibilidad

| Clase | Comportamiento |
| --- | --- |
| `mn-hide-mobile` | Oculta por debajo de `48rem` |
| `mn-hide-tablet` | Oculta desde `48rem`, también en escritorio |
| `mn-hide-desktop` | Oculta desde `64rem` |
| `mn-hidden` | Oculta siempre, también para tecnologías de asistencia |
| `mn-sr-only` | Oculta visualmente y conserva el contenido para lectores de pantalla |

## Temas y personalización

Sin atributo de tema, Mini CSS sigue `prefers-color-scheme` del sistema. Para fijar un tema, configura el atributo en la raíz del documento:

```html
<html lang="es" data-mn-theme="light">
```

```html
<html lang="es" data-mn-theme="dark">
```

Elimina el atributo para volver al modo automático. No se admite el tema por subárbol en esta versión.

Incluye tus ajustes **después** de cargar Mini CSS:

```css
:root {
  --mn-font: system-ui, sans-serif;
  --mn-radius: .5rem;
  --mn-speed: 120ms;
  --mn-space-4: 1rem;
}
```

Tokens de superficie y lectura: `--mn-bg`, `--mn-surface`, `--mn-subtle`, `--mn-text`, `--mn-muted`, `--mn-border` y `--mn-link`.

Si cambias colores, actualiza también sus pares `-on` y revisa los contrastes. Las variantes suaves conservan sus pares de fondo claro y texto oscuro en ambos temas.

## Accesibilidad

El framework incluye foco visible, utilidades para lectores de pantalla y reducción de movimiento mediante `prefers-reduced-motion`.

Los **77 pares de fondo y texto asignado** tienen un contraste calculado mínimo de **4,63:1**. Esto no garantiza el contraste de cruces arbitrarios entre colores ni constituye una certificación de accesibilidad del sitio final.

Al integrar Mini CSS:

- Usa HTML semántico y una jerarquía de encabezados coherente.
- Asocia cada campo con su etiqueta y sus mensajes de ayuda o error.
- Acompaña el color con texto para comunicar estados.
- Usa `disabled` nativo en botones inactivos; `aria-disabled` por sí solo no impide acciones.
- Conserva foco visible y prueba las interacciones con teclado.
- Las clases `mn-tabs` representan navegación por enlaces; no implementan paneles ARIA dinámicos.

## Estructura del proyecto

| Archivo | Descripción |
| --- | --- |
| [`mini.css`](mini.css) | CSS fuente organizado en secciones comentadas |
| [`mini.min.css`](mini.min.css) | CSS minificado para distribución |
| [`index.html`](index.html) | Guía visual con ejemplos y código copiable |
| [`guia-mini-autonoma.html`](guia-mini-autonoma.html) | Guía con CSS y foto incorporados |
| [`mini.jpg`](mini.jpg) | Recorte fotográfico de Mini para la guía |
| [`palette.json`](palette.json) | Paleta completa y roles de color |
| [`analisis-diseno.md`](analisis-diseno.md) | Análisis visual, referencia Bulma y catálogo de clases |
| [`pruebas.md`](pruebas.md) | Comprobaciones ejecutadas y pruebas pendientes |
| [`LICENSE.txt`](LICENSE.txt) | Licencia del código y la documentación |

## Estado y validación

**Primera versión funcional para evaluación e integración.**

Comprobaciones realizadas: contraste numérico de la paleta, clases usadas por la guía, identificadores únicos, anclas, asociación de etiquetas y presencia de archivos enlazados.

**Pendiente:** validación visual e interacciones en navegador. El entorno de generación no pudo instalar Chromium. Consulta [`pruebas.md`](pruebas.md) para el detalle y el recorrido de prueba manual.

Se dirige a navegadores modernos con CSS Grid, variables CSS y `<dialog>`. La compatibilidad entre navegadores aún requiere validación; no se garantiza soporte para Internet Explorer o WebViews antiguos.

El framework incluye un reset global pequeño que afecta `body`, `box-sizing` y algunos elementos nativos. Revisa su integración si tu aplicación ya tiene estilos globales.

La guía incluye JavaScript de demostración para cambiar el tema, copiar código, abrir el modal y validar un formulario local. No incorpora backend, almacenamiento, telemetría ni solicitudes a servicios externos.

## Contribuciones

Las mejoras deben conservar la sencillez del framework:

1. Mantén el prefijo `mn-` y reutiliza los tokens existentes.
2. Documenta las clases y los estados nuevos con ejemplos HTML.
3. Verifica móvil, escritorio, temas claro/oscuro y navegación con teclado.
4. Recalcula el contraste cuando cambies la paleta.
5. Actualiza la guía, el catálogo y los archivos de distribución.

## Licencia

El código original y la documentación se distribuyen bajo la [licencia MIT](LICENSE.txt).

La fotografía de Mini queda excluida de esta licencia: su inclusión en la guía no concede derechos de reutilización sobre la imagen.

---

Inspirado en **Mini**, nuestra pequeña directora de curiosidad. 🐈
