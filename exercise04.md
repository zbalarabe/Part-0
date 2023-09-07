sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_notes
    activate server
    server-->>browser: GET https://studies.cs.helsinki/exampleapp/notes
    deactivate server
    Note left of server: Server asks browser to do new GET Request

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    Note right of browser: The browser reloads notes page
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: reloads the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: reloads the JavaScript file
    deactivate server

    Note right of browser: The JavaScript is code that fetches the JSON from the server is executed again, including the new note

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "Hello there", "date": "2023-09-07T09:32:11.998Z" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function which rerenders the notes