sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_notes_spa
    activate server
    Note left of server: This time the server does not ask for a redirect, the browser stays on the same page
    deactivate server