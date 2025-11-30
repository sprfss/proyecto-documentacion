## 📄 HTML Básico: Estructura y Elementos Fundamentales

**HTML** (HyperText Markup Language) es el **lenguaje de marcado** fundamental utilizado para estructurar y presentar el contenido de una página web. No es un lenguaje de programación, sino un lenguaje que le dice al navegador cómo debe mostrar el texto, imágenes y otros elementos.

-----

## 🏗️ La Estructura Básica de un Documento HTML

Todo documento HTML debe seguir una estructura base para ser válido.

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Título de la Página</title>
</head>
<body>
    </body>
</html>
```

| Elemento | Descripción |
| :--- | :--- |
| `<!DOCTYPE html>` | Define que el documento es de tipo HTML5. Siempre debe ir al inicio. |
| `<html>` | El elemento raíz que envuelve todo el contenido de la página. |
| `<head>` | Contiene metadatos (información sobre el documento, como la codificación y el título). **No es visible** para el usuario. |
| `<body>` | Contiene el contenido visible: textos, imágenes, enlaces, listas, etc. |

### Metadatos Clave en `<head>`

  * `<meta charset="UTF-8">`: Establece la codificación de caracteres, crucial para mostrar correctamente caracteres especiales (como acentos o la `ñ`).
  * `<title>...</title>`: El texto que aparece en la pestaña del navegador.

-----

## 🏷️ Elementos Comunes de Contenido

Estos son los elementos que se utilizan dentro del `<body>` para dar estructura y semántica al contenido:

### 1\. Títulos y Párrafos

Se utilizan para organizar el texto en secciones jerárquicas y bloques de texto.

  * **Títulos:** Se definen con etiquetas `<h1>` a `<h6>`. `<h1>` es el más importante y solo debe haber uno por página.
    ```html
    <h1>Título Principal (el más importante)</h1>
    <h2>Subtítulo de una sección</h2>
    <h3>Título de una subsección</h3>
    ```
  * **Párrafos:** Se definen con la etiqueta `<p>`.
    ```html
    <p>Este es un bloque de texto que contiene información.</p>
    ```

### 2\. Listas

Para organizar la información en viñetas o pasos numerados.

| Tipo de Lista | Etiqueta | Descripción |
| :--- | :--- | :--- |
| **No Ordenada** (Viñetas) | `<ul>` (Unordered List) | Usada para listar elementos sin un orden específico. |
| **Ordenada** (Numerada) | `<ol>` (Ordered List) | Usada para pasos o elementos que deben seguir una secuencia. |
| **Elemento de Lista** | `<li>` (List Item) | Va dentro de `<ul>` o `<ol>`. |

```html
<ul>
    <li>Elemento A</li>
    <li>Elemento B</li>
</ul>
```

### 3\. Enlaces e Imágenes

Estos elementos son fundamentales para la navegación y el contenido multimedia.

  * **Enlaces (`<a>`):** Usados para conectar a otras páginas o secciones. El atributo clave es `href` (destino).
    ```html
    <a href="https://www.google.com" target="_blank">Ir a Google</a>
    ```
  * **Imágenes (`<img>`):** Usados para insertar gráficos. Es una etiqueta de **cierre automático** (no tiene etiqueta de cierre `</img>`).
      * `src`: Ruta del archivo de imagen.
      * `alt`: Texto alternativo esencial para accesibilidad (si la imagen no carga, este texto se muestra).
    <!-- end list -->
    ```html
    <img src="ruta/a/mi-imagen.jpg" alt="Descripción de una imagen relevante" width="300">
    ```

-----

## 🏷️ Atributos

Los atributos proporcionan información adicional sobre los elementos y siempre se especifican en la etiqueta de apertura.

  * **Sintaxis:** `nombre_atributo="valor_atributo"`

| Atributo | Uso | Ejemplo |
| :--- | :--- | :--- |
| **`href`** | Especifica la URL de destino de un enlace. | `<a href="index.html">` |
| **`src`** | Especifica la ruta de un recurso (imagen, script). | `<img src="logo.png">` |
| **`class`** | Se usa para aplicar estilos CSS o seleccionar elementos con JavaScript. | `<p class="destacado">` |
| **`id`** | Identificador único para un elemento (solo debe haber uno por página). | `<section id="contacto">` |

-----

¿Te gustaría que te preparara otro documento Markdown con los conceptos básicos de **CSS** para dar estilo a estos elementos HTML?