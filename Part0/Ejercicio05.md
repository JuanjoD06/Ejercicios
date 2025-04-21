```mermaid
sequenceDiagram
    participant user as Usuario
    participant browser as Navegador
    participant server as Servidor

    Note right of user: El usuario accede a la versión SPA de la aplicación de notas

    user->>browser: Carga inicial de la SPA (/exampleapp/spa)
    browser->>server: GET /exampleapp/spa (carga la estructura HTML y los archivos de recursos)
    activate server
    server-->>browser: HTML, CSS y JavaScript
    deactivate server

    Note right of browser: El navegador carga la estructura HTML, los estilos y el script JavaScript.

    browser->>server: GET /exampleapp/data.json (solicita las notas)
    activate server
    server-->>browser: Respuesta JSON con las notas
    deactivate server

    Note right of browser: El navegador recibe las notas y las renderiza dinámicamente sin recargar la página.

