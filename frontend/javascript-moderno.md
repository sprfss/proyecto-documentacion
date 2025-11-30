## ✨ JavaScript Moderno (ES6+): Características Clave

El estándar ECMAScript 2015 (ES6) y las versiones subsiguientes transformaron JavaScript en un lenguaje más potente, legible y apto para aplicaciones a gran escala.

-----

## 1\. 🔑 Variables y Funciones

Las formas de declarar variables y funciones se han renovado para mejorar el alcance (scope) y la claridad.

### Declaración de Variables: `let` y `const`

Reemplazaron a `var` para resolver problemas con el *hoisting* y el alcance de bloque.

  * **`const` (Constante):** Se usa para valores que **no cambiarán**. Debe ser inicializada al declararla.
  * **`let` (Variable):** Se usa para valores que **pueden cambiar** (re-asignarse).

Ambas tienen **alcance de bloque** (`{...}`), a diferencia de `var` que tiene alcance de función.

```javascript
// Scope de Bloque: 'i' no existe fuera del for
for (let i = 0; i < 5; i++) {
    // ...
}
// console.log(i); // Error
```

### Funciones Flecha (Arrow Functions)

Una sintaxis más concisa para escribir funciones que ofrece un manejo léxico del valor de `this`.

  * **Sintaxis Concisa:** Ideal para funciones anónimas y *callbacks*.
  * **Alcance Léxico de `this`:** Hereda el valor de `this` del contexto donde fue creada, resolviendo un problema clásico de JavaScript.

<!-- end list -->

```javascript
// Sintaxis tradicional
const sumar = function(a, b) {
    return a + b;
};

// Sintaxis de Función Flecha
const sumarFlecha = (a, b) => a + b; // Implícito return
```

-----

## 2\. 🧩 Estructuras de Datos y Desestructuración

Estas características facilitan la manipulación y extracción de datos de arrays y objetos.

### Desestructuración (Destructuring)

Permite extraer valores de arrays u objetos directamente a variables.

```javascript
const usuario = { nombre: 'Alice', edad: 30 };
// Desestructuración de objeto
const { nombre, edad } = usuario; 
console.log(nombre); // Alice

const colores = ['rojo', 'verde', 'azul'];
// Desestructuración de array
const [primero, segundo] = colores; 
console.log(primero); // rojo
```

### Operadores Spread (`...`) y Rest (`...`)

  * **Spread (`...`):** Expande un iterable (array o string) en sus elementos individuales. Útil para copiar arrays u objetos sin mutarlos.

    ```javascript
    const arr1 = [1, 2];
    const arr2 = [...arr1, 3, 4]; // [1, 2, 3, 4] (Copia y añade)
    ```

  * **Rest (`...`):** Recolecta el resto de los argumentos o propiedades en un array.

    ```javascript
    function mostrarDatos(a, ...restantes) {
        console.log(restantes); // [2, 3, 4]
    }
    mostrarDatos(1, 2, 3, 4);
    ```

-----

## 3\. ⏳ Asincronía Moderna

La gestión de operaciones asíncronas (como la obtención de datos de una API) se ha vuelto mucho más legible.

### Promesas (Promises)

Objetos que representan la finalización (o el fracaso) eventual de una operación asíncrona. Reemplazaron a los *callbacks* anidados (*callback hell*).

### `async`/`await`

Sintaxis construida sobre Promesas que permite escribir código asíncrono que se ve y se comporta como código síncrono, mejorando la legibilidad.

  * **`async`:** Convierte una función en una función asíncrona, obligándola a devolver una Promesa.
  * **`await`:** Solo puede usarse dentro de una función `async`. Pausa la ejecución hasta que la Promesa se resuelva (o se rechace).

<!-- end list -->

```javascript
async function obtenerDatos() {
    try {
        // Pausa aquí hasta que fetch termine
        const respuesta = await fetch('api/data'); 
        const datos = await respuesta.json();
        return datos;
    } catch (error) {
        console.error('Error al obtener datos:', error);
    }
}
```

-----

## 4\. 📚 Módulos y Clases

### Módulos (Import/Export)

ES6 introdujo un sistema de módulos estándar para organizar el código en archivos reutilizables, reemplazando sistemas propietarios (como CommonJS o AMD).

  * **`export`:** Se usa para hacer que funciones, variables o clases sean accesibles fuera del archivo.
  * **`import`:** Se usa para acceder al contenido exportado desde otro archivo.

<!-- end list -->

```javascript
// archivo utils.js
export const PI = 3.14; 
export function calcularArea() { /* ... */ }

// archivo main.js
import { PI, calcularArea } from './utils.js';
```

### Clases (Classes)

Aunque JavaScript ya usaba herencia prototípica, ES6 introdujo la sintaxis `class` para una programación orientada a objetos más familiar.

  * **Sintaxis:** Utiliza `constructor` y `extends` para la herencia.

<!-- end list -->

```javascript
class Animal {
    constructor(nombre) {
        this.nombre = nombre;
    }
    saludar() {
        return `Hola, soy ${this.nombre}`;
    }
}

class Perro extends Animal {
    ladrar() {
        return 'Guau!';
    }
}
```