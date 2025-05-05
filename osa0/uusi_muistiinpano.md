```mermaid
  info

    sequenceDiagram
        participant browser
        participant server

        Note right of browser: Käyttäjä kirjoittaa tekstikenttään ja painaa "Tallenna"-painiketta

        browser->>browser: Estetään oletustoiminto (esim. lomakkeen uudelleenlataus)
        browser->>browser: Luodaan uusi muistiinpano objekti (sis. tekstin ja päivämäärän)

        browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
        activate server
        Note right of server: Palvelin tallentaa uuden muistiinpanon ja tekee uudelleenohjauksen
        server-->>browser: HTTP 302 Redirect (Location: /exampleapp/notes)
        deactivate server

        Note right of browser: Selain ohjautuu uudestaan alkuperäiselle /notes-sivulle

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

        Note right of browser: JavaScript hakee muistiinpanot JSON-muodossa

        browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
        activate server
        server-->>browser: Päivitetty JSON-lista, jossa uusi muistiinpano mukana
        deactivate server

        Note right of browser: Selain suorittaa callback-funktion ja päivittää näkymän

    ```