## 🗄️ Bases de Datos: Estructura, Almacenamiento y Consulta

Una **Base de Datos** (BD) es una colección organizada de información estructurada o datos, típicamente almacenados de forma electrónica en un sistema de computadoras. Su principal propósito es permitir la gestión, almacenamiento y acceso eficiente a grandes volúmenes de datos.

---

## 1. 💡 Conceptos Fundamentales

| Concepto | Descripción |
| :--- | :--- |
| **DBMS** | **Sistema de Gestión de Bases de Datos** (Database Management System). Es el *software* que interactúa con la BD física y permite a los usuarios definir, crear, mantener y controlar el acceso a los datos (Ej: MySQL, PostgreSQL). |
| **SQL** | **Structured Query Language**. El lenguaje estándar utilizado para gestionar y manipular bases de datos relacionales (crear tablas, insertar, actualizar y consultar datos). |
| **Esquema** | La estructura formal o el diseño de la BD. Define cómo se organizan los datos, incluyendo tablas, campos (columnas) y las relaciones entre ellos. |
| **Transacción** | Una secuencia de una o más operaciones que se ejecutan como una única unidad lógica de trabajo. Sigue las propiedades **ACID** para garantizar la integridad de los datos. |

---

## 2. 🔠 Tipos de Bases de Datos

Las bases de datos se dividen principalmente en dos grandes categorías: Relacionales y NoSQL.

### A. Bases de Datos Relacionales (SQL)

Se basan en el **modelo relacional** propuesto por E.F. Codd. Almacenan datos en **tablas** con filas y columnas, donde las relaciones entre las tablas se definen mediante **claves**.

| Característica | Descripción |
| :--- | :--- |
| **Estructura** | Esquema estricto y predefinido (se debe definir la estructura de las tablas antes de insertar datos). |
| **Integridad** | Alta integridad de datos garantizada por las propiedades **ACID** (Atomicidad, Consistencia, Aislamiento, Durabilidad). |
| **Escalabilidad** | Principalmente **escalabilidad vertical** (mejorar el *hardware* del servidor, más potencia). |
| **Ejemplos** | **MySQL**, **PostgreSQL**, **Oracle**, **SQL Server**. |

### B. Bases de Datos NoSQL (No solo SQL)

Una categoría diversa de sistemas que están diseñados para manejar grandes volúmenes de datos y esquemas flexibles. No utilizan el modelo de tablas, filas y relaciones fijas.

| Tipo de NoSQL | Estructura de Datos | Uso Principal | Ejemplo |
| :--- | :--- | :--- | :--- |
| **Clave-Valor** | *Key-Value* | Caching, sesiones de usuario. | Redis, Memcached |
| **Documentales** | *JSON/BSON* (Documentos) | Gestión de contenido, catálogos flexibles. | **MongoDB**, Couchbase |
| **Columnares** | *Wide-Column* | Almacenamiento masivo para análisis de *Big Data*. | Cassandra, HBase |
| **Grafo** | *Nodos y Aristas* | Relaciones complejas, redes sociales, sistemas de recomendación. | Neo4j |

---

## 3. 🛡️ Propiedades ACID (Relacionales)

Las propiedades ACID son el estándar para garantizar que las transacciones en una base de datos relacional sean procesadas de manera confiable.

1.  **Atomicidad (Atomicity):** Una transacción debe completarse **totalmente o no completarse en absoluto**. Si falla un paso, todos los cambios se revierten (*rollback*).
2.  **Consistencia (Consistency):** Una transacción válida solo puede llevar la BD de un estado válido a otro. Se mantiene la integridad de los datos.
3.  **Aislamiento (Isolation):** Las transacciones concurrentes deben ejecutarse de forma independiente. Los cambios realizados por una transacción no deben ser visibles para otra hasta que la primera se complete.
4.  **Durabilidad (Durability):** Una vez que una transacción ha sido confirmada (*commit*), sus cambios son permanentes, incluso en caso de fallo del sistema.

---

## 4. 📈 Escalabilidad (Vertical vs. Horizontal)

* **Escalabilidad Vertical:** Aumentar la capacidad de un **solo servidor** (más RAM, más CPU). Es simple, pero tiene límites físicos. (Típico en bases de datos SQL tradicionales).
* **Escalabilidad Horizontal:** Distribuir la carga de trabajo entre **múltiples servidores** (crear un *cluster*). Es la base de las bases de datos NoSQL, que pueden crecer casi indefinidamente.