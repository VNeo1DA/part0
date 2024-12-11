sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_notes
	activate server
    Note right of browser: Send data
    server->>server: Store data to notes
    server-->>browser: Response 302 Redirect
    deactivate server
    Note right of browser: browser to reload the Notes page
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server
    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server
    browser->> GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->> browser: [{"content": "HTML is easy", "date": "2024-1-1"}, ...]
    deactivate server
    Note right of browser: The browser executes the callback function that renders the notes