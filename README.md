sequenceDiagram
    participant browser
    participant server

    Note right of browser: User enters text into the input field and clicks "Save"

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note with note data
    activate server
    server-->>browser: 302 Redirect to /notes
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: Updated HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated notes JSON including the new note
    deactivate server

    Note right of browser: Browser re-renders the notes with the updated data
