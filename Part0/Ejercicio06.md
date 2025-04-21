```mermaid
sequenceDiagram
    participant user as Usuario
    participant browser as Navegador (SPA)
    participant server as Servidor

    Note right of user: Escribe una nueva nota y hace clic en "Guardar"

    user->>browser: Interacción con el formulario de la nota

    Note right of browser: El evento del formulario es interceptado por JavaScript (SPA)

    browser->>server: POST /exampleapp/new_note_spa con JSON
    activate server
    server-->>browser: HTTP 201 OK 
    deactivate server

    Note right of browser: La nota se añade al arreglo de notas en memoria

    browser-->>browser: Renderiza la nueva nota en el DOM sin recargar la página
