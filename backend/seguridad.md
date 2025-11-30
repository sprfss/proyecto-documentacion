## 🔒 Seguridad Backend: Protegiendo la Lógica y los Datos

La **Seguridad Backend** se enfoca en proteger la lógica del negocio, los datos sensibles (credenciales de usuario, información financiera) y la infraestructura del servidor de accesos no autorizados, ataques maliciosos o fallos de integridad.

---

## 1. 🛑 El Top 10 de Vulnerabilidades (OWASP)

La lista **OWASP Top 10** es un estándar de concienciación sobre las vulnerabilidades de seguridad más críticas para las aplicaciones web. Las siguientes son algunas de las más relevantes para el backend:

| Vulnerabilidad | Descripción | Prevención Clave |
| :--- | :--- | :--- |
| **Inyección (Injection)** | Ocurre cuando datos no confiables se envían a un intérprete (SQL, OS), cambiando el comando. | **Consultas Parametrizadas** (Prepared Statements) y Validación estricta de entradas. |
| **Pérdida de Autenticación** | Implementaciones deficientes que permiten a los atacantes asumir la identidad de un usuario (robo de sesión, contraseñas débiles). | Uso de **Tokens Seguros** (JWT), gestión adecuada de sesiones y *hashing* de contraseñas. |
| **Exposición de Datos Sensibles** | Fallos al proteger datos sensibles (tarjetas de crédito, PII) en reposo o en tránsito. | **Cifrado** de datos en tránsito (HTTPS/TLS) y en reposo (cifrado de bases de datos). |
| **Entidades Externas XML (XXE)** | Vulnerabilidades al procesar XML que permiten inyecciones de código local o ataques de denegación de servicio (DoS). | **Desactivar** el procesamiento de entidades externas y DTDs en los *parsers* XML. |
| **Deserialización Insegura** | Los atacantes pueden manipular objetos serializados que contienen lógica maliciosa. | Usar formatos de datos simples (JSON) y validar la integridad de los datos. |

---

## 2. 🔑 Autenticación y Autorización Segura

Estos son pilares fundamentales para garantizar que solo los usuarios correctos accedan a los recursos apropiados.

### Almacenamiento de Contraseñas

* **Hashing (No Cifrado):** Las contraseñas nunca deben guardarse como texto plano. Deben ser **hasheadas** usando algoritmos lentos y resistentes a la fuerza bruta, como **Bcrypt** o **Argon2**.
* **Salting (Salt):** Añadir una cadena de caracteres aleatoria (`salt`) a la contraseña antes del *hashing*. Esto garantiza que dos usuarios con la misma contraseña tengan *hashes* diferentes, frustrando los ataques de tablas *rainbow*.

### Gestión de Sesiones y Tokens

* **JSON Web Tokens (JWT):** Un estándar para crear *tokens* de acceso. Deben ser manejados de forma segura (ej. no almacenarlos en el *localStorage* si no es necesario) y deben tener una **fecha de expiración** corta.
* **Autorización (Authorization):** Definir y aplicar reglas de acceso. Incluso si un usuario está autenticado, el backend debe verificar que **tenga permiso** para realizar la acción solicitada (Ej: Un usuario normal no puede acceder a `/api/admin/borrar-usuario`).

---

## 3. 🛡️ Protección de API y Servidor

### Validación de Entradas

* **Principio de Confianza Cero:** Nunca confíes en los datos que vienen del cliente (frontend).
* **Validación Estricta:** Validar el tipo de datos, el formato, la longitud y el rango de todos los *inputs* en el backend, incluso si ya fueron validados en el frontend.

### CORS y Rate Limiting

* **CORS (Cross-Origin Resource Sharing):** Configuración para permitir solo a los dominios autorizados (frontends legítimos) realizar peticiones a tu API.
* **Rate Limiting (Límite de Tasa):** Limitar el número de peticiones que un cliente puede hacer a un *endpoint* en un periodo de tiempo. Esto previene ataques de fuerza bruta, *scrapping* y DoS ligeros.

### Headers de Seguridad

El backend debe configurar *headers* de respuesta HTTP para guiar el navegador en la aplicación de seguridad:

* **`Strict-Transport-Security` (HSTS):** Fuerza al navegador a usar siempre HTTPS.
* **`Content-Security-Policy` (CSP):** Controla qué recursos externos (scripts, imágenes) puede cargar el navegador, mitigando ataques XSS.

---

## 4. 🗃️ Seguridad de Bases de Datos

* **Principio de Mínimo Privilegio:** La cuenta de usuario que usa tu aplicación para conectarse a la base de datos **solo debe tener los permisos que necesita** (Ej: solo `SELECT`, `INSERT`, `UPDATE`, no permisos de administración o de eliminación de bases de datos).
* **Auditoría y Logs:** Mantener registros detallados (*logs*) de todos los accesos, errores y operaciones críticas.