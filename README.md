# 🎵 Music Zone

Applicazione web per la gestione e la visualizzazione di prodotti musicali (strumenti e accessori), con un’area pubblica per la navigazione dei prodotti e un back office per la gestione completa tramite API REST esterna.

***

## 📂 Struttura del progetto

- `index.html`  
  Home del sito con navbar, card delle categorie (Keyboards, Pianos, Guitars, Basses, Drums, Monitors) e link alla pagina dei prodotti filtrata tramite query string (`products.html?description=...`)

- `products.html`  
  Pagina di listing dei prodotti, con spinner di caricamento, gestione degli errori e titolo dinamico in base alla categoria selezionata

- `dettaglio.html`  
  Pagina di dettaglio di un singolo prodotto, popolata via JavaScript leggendo l’`id` dalla query string e recuperando i dati dalla API.

- `backoffice.html`  
  Pagina di amministrazione con form per creare, modificare ed eliminare prodotti (campi: `name`, `description`, `brand`, `imageUrl`, `price`) e pulsanti `Add`, `Update`, `Delete`, `Reset`, oltre a una box per i messaggi di errore.

- `index.js`  
  Script condiviso per la logica comune (es. aggiornamento dinamico dell’anno nel footer tramite elemento `#year`).

- `products.js`  
  Gestisce il recupero dei prodotti dalla API, mostra lo spinner durante il caricamento, gestisce gli errori e renderizza dinamicamente le card nella griglia di `products.html`.

- `dettaglio.js`  
  Recupera i dati di un singolo prodotto dalla API e popola il contenitore `#productDetail` nella pagina `dettaglio.html`.

- `backoffice.js`  
  Implementa tutta la logica CRUD verso l’endpoint Strive School (POST, GET, PUT, DELETE) usando una `apiKey` in `Authorization`, gestisce il form del back office, la precompilazione in modalità modifica (se è presente `id` in query string) e i messaggi di errore nella `errorBox`.[attached_file:file:5]

***

## ✨ Funzionalità

- Navigazione per categorie  
  Dalla home l’utente può cliccare sulle card delle categorie per aprire la lista dei prodotti filtrata per categoria (tramite parametro `description` in query string).

- Listing prodotti responsive  
  I prodotti vengono mostrati in card Bootstrap con immagine, nome, brand e prezzo, recuperati dalla REST API; in caso di caricamento appare uno spinner, in caso di errore viene mostrato un messaggio dedicato.

- Dettaglio prodotto  
  Selezionando un prodotto si accede alla pagina di dettaglio, che mostra tutte le principali informazioni dell’item recuperate dalla API tramite `id`.

- Back office (CRUD completo)  
  Il back office permette di:
  - creare un nuovo prodotto (POST);
  - modificare un prodotto esistente (PUT, con form precompilato se è presente `?id=...` nell’URL);
  - cancellare un prodotto (DELETE, con conferma e redirect alla home).

- Gestione errori e conferme  
  Le operazioni critiche (creazione, modifica, eliminazione, caricamento dati) sono avvolte in blocchi `then/catch` con:
  - log su console;
  - messaggi utente in una box di errore;
  - dialog di conferma (`confirm()`) per update, delete e reset del form.

***

## 🛠️ Stack tecnologico

- HTML5 e CSS3 per il markup e lo stile base delle pagine.
- [Bootstrap 5](https://getbootstrap.com/) via CDN per layout responsive, navbar, card, form, spinner e componenti UI.
- JavaScript vanilla (`fetch`, manipolazione DOM, gestione query string) per la logica di front-end.
- REST API esterna Strive School per la persistenza dei prodotti, autenticata tramite header `Authorization: Bearer <apiKey>`.

***

## 🚀 Avvio del progetto

1. Clonare il repository:
   - `git clone <url-repo>`
   - `cd <nome-repo>`  

2. Avviare un semplice server statico (consigliato):  
   - ad esempio usando l’estensione “Live Server” di VS Code oppure un qualsiasi server HTTP statico.  

3. Aprire le pagine principali nel browser:
   - `index.html` → home e categorie.  
   - `products.html` → lista prodotti filtrata per categoria.
   - `backoffice.html` → area amministrativa per creare, modificare ed eliminare prodotti.

Assicurarsi che il browser possa raggiungere l’endpoint remoto dell’API e che la `apiKey` configurata in `backoffice.js` sia valida e aggiornata.
