## 🌐 Servidores Web: Fundamentos y Funcionamiento

Un **Servidor Web** es un *software* o un sistema informático diseñado para almacenar, procesar y entregar páginas web y otros contenidos a clientes (navegadores) que los solicitan, utilizando principalmente el protocolo **HTTP** (Protocolo de Transferencia de Hipertexto).

---

## 🧠 1. Conceptos Clave

| Concepto | Definición |
| :--- | :--- |
| **Cliente** | El dispositivo que inicia la comunicación y solicita un recurso (generalmente un navegador web como Chrome o Firefox). |
| **Petición (Request)** | El mensaje enviado por el cliente al servidor, solicitando un archivo o recurso específico (Ej: `GET /index.html`). |
| **Respuesta (Response)** | El mensaje enviado por el servidor al cliente, que contiene el recurso solicitado o un código de estado (Ej: `HTTP/1.1 200 OK`). |
| **Protocolo HTTP** | El conjunto de reglas que gobierna la transferencia de datos entre el cliente y el servidor. |
| **Puerto 80/443** | Los puertos por defecto: **80** para HTTP (no seguro) y **443** para HTTPS (seguro, con TLS/SSL). |

---

## ⚙️ 2. Tipos de Contenido y Flujo de Trabajo

### Contenido Estático vs. Dinámico

El servidor web maneja dos tipos principales de contenido:

1.  **Contenido Estático:** Archivos listos para ser entregados sin procesamiento (Ej: `.html`, `.css`, `.js`, `.jpg`). El servidor web los busca en el disco y los envía directamente.
2.  **Contenido Dinámico:** Contenido que debe ser generado en el momento de la petición (Ej: una página de perfil de usuario o resultados de una búsqueda). El servidor web pasa la petición a un **Servidor de Aplicaciones** (Ej: Node.js, Python/Django, PHP/Laravel) para que procese la lógica de negocio y acceda a la base de datos, y luego devuelve la página HTML generada al cliente.

### Flujo de la Petición

1.  El usuario escribe una URL en el navegador (Cliente).
2.  El navegador pide la IP del servidor a un servidor **DNS**.
3.  El navegador envía una **petición HTTP** a esa IP (Ej: Puerto 80 o 443).
4.  El **Servidor Web** recibe la petición.
5.  Si el recurso es **estático**, lo envía de vuelta.
6.  Si el recurso es **dinámico**, pasa la petición al **Servidor de Aplicaciones**.
7.  El Servidor de Aplicaciones genera la respuesta y la devuelve al Servidor Web.
8.  El Servidor Web envía la respuesta final al navegador.

---

## 🛡️ 3. Servidores Web Populares

Aunque existen muchos, estos son los más utilizados globalmente:

| Servidor Web | Creador | Características Principales | Uso Típico |
| :--- | :--- | :--- | :--- |
| **Apache HTTP Server** | Apache Software Foundation | Modular, potente, robusto, maduro. Se usa con el archivo `.htaccess`. | Hosting tradicional, sitios con PHP/MySQL. |
| **Nginx** (Engine-X) | Igor Sysoev | **Ligero**, alto rendimiento, asíncrono. Excelente para servir archivos estáticos. | **Proxy inverso** (Reverse Proxy), balanceo de carga, *microservicios*. |
| **Microsoft IIS** | Microsoft | Integrado con el entorno Windows y .NET. | Aplicaciones basadas en tecnologías Microsoft. |
| **Apache Tomcat** | Apache Software Foundation | Especializado en servir contenido dinámico de Java Servlets y JSP. | Aplicaciones empresariales basadas en Java. |

---

## ⚡ 4. Proxy Inverso y Balanceo de Carga

En arquitecturas modernas, el Servidor Web (a menudo **Nginx**) no solo entrega archivos, sino que actúa como una capa frontal:

* **Proxy Inverso (Reverse Proxy):** Es la puerta de entrada pública. Recibe todas las peticiones y las redirige al servidor interno de aplicaciones adecuado. Esto oculta la infraestructura interna al cliente.
* **Balanceo de Carga (Load Balancing):** Distribuye el tráfico de entrada entre múltiples Servidores de Aplicaciones para evitar que un solo servidor se sobrecargue y garantizar la alta disponibilidad.