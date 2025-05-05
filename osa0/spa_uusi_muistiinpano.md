```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: Käyttäjä kirjoittaa tekstikenttään ja painaa "Save"-nappia

    Note right of browser: JavaScript (spa.js) muodostaa uuden muistiinpanon objektin

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of server: Palvelin tallentaa muistiinpanon ja vastaa JSON-muotoisella vastauksella
    server-->>browser: JSON { "message": "note created" }
    deactivate server

    Note right of browser: Selain päivittää muistiinpanolistan näyttämättä sivua uudelleen
    Note right of browser: Uusi muistiinpano lisätään näkyviin käyttöliittymässä JavaScriptin avulla
