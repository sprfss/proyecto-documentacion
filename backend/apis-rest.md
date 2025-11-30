## 💻 APIs REST: Arquitectura y Comunicación Web

Una **API** (Application Programming Interface) es un conjunto de reglas que permite a diferentes *software* comunicarse entre sí. **REST** (Representational State Transfer) es un **estilo arquitectónico** que define cómo se deben crear y usar las APIs web, aprovechando las características del protocolo HTTP.

-----

## 1\. 💡 Conceptos Fundamentales de REST

| Concepto | Descripción |
| :--- | :--- |
| **Recurso (Resource)** | Es la pieza clave de información a la que se accede. En REST, todo es un recurso (Ej: un usuario, un producto, un comentario). Se identifica con una **URL única** (URI). |
| **URI (Uniform Resource Identifier)** | La dirección única que identifica un recurso (Ej: `/api/v1/usuarios/123`). |
| **Stateless (Sin estado)** | Cada petición del cliente al servidor debe contener **toda** la información necesaria para que el servidor la entienda. El servidor no guarda información de la sesión entre peticiones. |
| **Interfaz Uniforme** | Uso consistente de los métodos HTTP estándar (GET, POST, PUT, DELETE) para realizar operaciones CRUD (Crear, Leer, Actualizar, Borrar). |

-----

## 2\. ⚡ Verbos HTTP y Operaciones CRUD

La API REST utiliza los **verbos HTTP** para indicar la **intención** de la operación que el cliente quiere realizar sobre un recurso. Esta es la base de su diseño uniforme.

| Verbo HTTP | Operación CRUD | Uso Típico | URI de Ejemplo |
| :--- | :--- | :--- | :--- |
| **GET** | **READ** (Leer) | Solicita la representación de un recurso o una colección. Es seguro e *idempotente*. | `GET /api/productos` (Todos los productos) |
| **POST** | **CREATE** (Crear) | Envía datos para crear un **nuevo recurso** en el servidor. No es *idempotente*. | `POST /api/productos` (Crear un nuevo producto) |
| **PUT** | **UPDATE** (Actualizar) | Reemplaza o **actualiza por completo** un recurso existente con los datos proporcionados. Es *idempotente*. | `PUT /api/productos/456` (Reemplazar el producto 456) |
| **DELETE** | **DELETE** (Borrar) | Elimina un recurso específico del servidor. Es seguro e *idempotente*. | `DELETE /api/productos/456` (Borrar el producto 456) |
| **PATCH** | **UPDATE** (Parcial) | Aplica **modificaciones parciales** a un recurso existente. No es *idempotente*. | `PATCH /api/productos/456` (Cambiar solo el precio del producto) |

> **Nota:** Un método es **Idempotente** si múltiples llamadas con los mismos parámetros tienen el mismo resultado final. (Ej: Borrar el recurso una vez o cinco veces resulta en que el recurso está borrado).

-----

## 3\. 🚦 Códigos de Estado

El servidor utiliza los códigos de estado HTTP en la respuesta para informar al cliente sobre el resultado de la petición.

| Rango de Código | Significado | Ejemplos Comunes |
| :--- | :--- | :--- |
| **1xx** | Informativo | |
| **2xx** | **Éxito** | `200 OK` (Petición exitosa), `201 Created` (Nuevo recurso creado). |
| **3xx** | Redirección | `301 Moved Permanently`. |
| **4xx** | **Error del Cliente** | `400 Bad Request` (Datos enviados incorrectos), `401 Unauthorized` (Falta autenticación), `403 Forbidden` (No tiene permisos), `404 Not Found` (El recurso no existe). |
| **5xx** | **Error del Servidor** | `500 Internal Server Error` (Error en la lógica del servidor). |

-----

## 4\. 🗂️ Formatos de Datos

Las APIs REST modernas utilizan principalmente dos formatos para enviar y recibir datos en el cuerpo de la petición y la respuesta:

  * **JSON (JavaScript Object Notation):** Es el formato dominante hoy en día debido a su ligereza, legibilidad y facilidad de uso con JavaScript.
  * **XML (Extensible Markup Language):** Más antiguo y verboso, todavía se usa en sistemas heredados o en entornos empresariales específicos.

<!-- end list -->

```json
// Ejemplo de JSON devuelto por GET /api/usuarios/1
{
  "id": 1,
  "nombre": "Elena",
  "email": "elena@ejemplo.com",
  "pedidos": "/api/usuarios/1/pedidos"
}
```

-----