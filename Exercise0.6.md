sequenceDiagram
   	participant browser
	participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of browser: Send JSON
    Note right of browser: rerender notes list on the page
    server->>server: Store JSON data
    server-->>browser: Respond 201 Created
    deactivate server
    Note right of browser: No redirect