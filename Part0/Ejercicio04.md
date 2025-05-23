```mermaid
sequenceDiagram
    participant user as Usuario
    participant browser as Navegador
    participant server as Servidor

    Note right of user: Escribe una nota en el campo de texto

    user->>browser: Clic en "Save"

    browser->>server: POST /exampleapp/new_note (form-urlencoded)
    activate server
    server-->>browser: HTTP 302 Found (Location: /exampleapp/notes)
    deactivate server

    browser->>server: GET /exampleapp/notes
    activate server
    server-->>browser: HTML del documento principal
    deactivate server

    browser->>server: GET /exampleapp/main.css
    activate server
    server-->>browser: CSS
    deactivate server

    browser->>server: GET /exampleapp/main.js
    activate server
    server-->>browser: JavaScript
    deactivate server

    Note right of browser: El navegador ejecuta `main.js`, que hace una petición para obtener las notas

    browser->>server: GET /exampleapp/data.json
    activate server
    server-->>browser: Respuesta JSON con todas las notas
    deactivate server

    Note right of browser: El navegador recibe las notas en formato JSON y las renderiza en la página
