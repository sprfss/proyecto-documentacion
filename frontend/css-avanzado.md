## 🎨 CSS Avanzado: Diseño, Estructura y Rendimiento

Si HTML se encarga de la estructura, **CSS** (Cascading Style Sheets) se encarga de la presentación. El CSS avanzado se enfoca en el diseño responsivo, el rendimiento, la organización del código y los sistemas de *layouts* complejos.

-----

## 🏗️ 1. Layouts Avanzados (Flexbox y Grid)

Los *layouts* modernos han reemplazado las técnicas antiguas basadas en `float` y `position` para crear diseños robustos y flexibles.

### Flexbox (Flexible Box)

**Flexbox** se usa principalmente para **diseño unidimensional** (filas o columnas). Es ideal para la alineación de elementos y la distribución de espacio dentro de un contenedor.

  * **Contenedor (`display: flex;`):**
      * `justify-content`: Distribuye el espacio entre/alrededor de los elementos en el eje principal (horizontal).
      * `align-items`: Alinea los elementos en el eje cruzado (vertical).
  * **Ítems:**
      * `flex-grow`: Define cuánto puede crecer un ítem en comparación con otros.
      * `flex-shrink`: Define cuánto puede encogerse un ítem.

### CSS Grid (Grid Layout)

**Grid** se usa para **diseño bidimensional** (filas y columnas simultáneamente). Es la herramienta perfecta para la estructura principal de la página (cabecera, barra lateral, contenido principal, pie de página).

  * **Contenedor (`display: grid;`):**
      * `grid-template-columns` / `grid-template-rows`: Define explícitamente el tamaño de las columnas y filas.
      * `gap`: Establece el espacio entre las celdas (filas y columnas).
  * **Ítems:**
      * `grid-column-start` / `grid-column-end`: Define el inicio y fin de un ítem, permitiendo que un elemento ocupe múltiples celdas.

-----

## 🌐 2. Diseño Responsivo Avanzado

El diseño *mobile-first* es un estándar. Las técnicas avanzadas permiten optimizar el rendimiento y la experiencia en cada dispositivo.

### Media Queries Avanzadas

Además de `min-width` y `max-width`, las *media queries* pueden basarse en aspectos del dispositivo.

  * **Orientación:**
    ```css
    @media (orientation: landscape) { /* Estilos solo en modo horizontal */ }
    ```
  * **Preferencias del Usuario (Dark Mode):**
    ```css
    @media (prefers-color-scheme: dark) { 
        /* Aplica estilos para el modo oscuro */ 
        body { background-color: #333; }
    }
    ```

### Unidades de Vista (Viewport Units)

Las unidades relativas a la ventana del navegador son clave para el diseño dinámico.

  * **`vw`** (Viewport Width): 1% del ancho del *viewport*.
  * **`vh`** (Viewport Height): 1% de la altura del *viewport*.
  * **`vmin` / `vmax`:** El 1% de la dimensión más pequeña / más grande del *viewport*.

-----

## 3\. ⚙️ Organización del Código (BEM y Arquitecturas)

A medida que el CSS crece, su mantenimiento se vuelve crucial. Las metodologías ayudan a nombrar y estructurar las clases.

### Metodología BEM (Block, Element, Modifier)

BEM promueve la modularidad y la reutilización a través de una convención estricta de nomenclatura.

| Componente | Separador | Ejemplo | Descripción |
| :--- | :--- | :--- | :--- |
| **Bloque (Block)** | N/A | `.menu` | Entidad independiente (Ej: un botón o un menú). |
| **Elemento (Element)**| `__` (Doble guion bajo) | `.menu__item` | Parte del bloque que no tiene sentido fuera de él. |
| **Modificador (Modifier)**| `--` (Doble guion) | `.menu--dark` | Variante o estado diferente del bloque o elemento. |

### Procesadores (Preprocesadores)

Los **preprocesadores** (como **Sass/SCSS** o **LESS**) extienden las capacidades de CSS añadiendo características de programación.

  * **Variables:** Para almacenar colores, fuentes, etc. (Ej: `$color-primario`).
  * **Anidamiento:** Permite anidar selectores de CSS, haciendo el código más legible y estructurado.
  * **Mixins:** Funciones reutilizables que agrupan bloques de estilos.

-----

## ⚡ 4. Rendimiento y Animaciones

El rendimiento del CSS impacta directamente en la velocidad de carga.

### Animaciones Basadas en Transformaciones

Para animaciones fluidas, se debe usar **`transform`** y **`opacity`**, ya que el navegador puede acelerarlas directamente en la GPU, minimizando el impacto en el rendimiento.

  * **`transform: translate(x, y);`**: Mover elementos.
  * **`transform: scale(n);`**: Cambiar el tamaño de los elementos.

### `will-change`

Propiedad que se usa como una pista para el navegador, indicándole qué propiedades del elemento se cambiarán en el futuro (ej. en una animación), permitiéndole optimizar el rendimiento por adelantado.

```css
.elemento-animado {
    will-change: transform, opacity; 
    transition: transform 0.3s ease;
}
```