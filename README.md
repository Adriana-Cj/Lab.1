# Lucrare de laborator nr. 1. Bazele HTTP

### Scop
Scopul acestei lucrări de laborator este studierea principiilor de bază ale protocolului HTTP, prin analizarea cererilor HTTP și crearea unor cereri HTTP specifice.

### Descrierea lucrării individuale
Această lucrare de laborator se bazează pe analiza cererilor și răspunsurilor HTTP în cadrul unei aplicații web. Se explorează metodele HTTP precum GET, POST, PUT, DELETE și codurile de stare asociate. Pe lângă analiza cererilor reale, se exersează crearea manuală a unor cereri HTTP prin intermediul unor instrumente dedicate.

### Documentație scurtă a proiectului
#### Proiectul este structurat pe două sarcini principale:
1.	Analiza cererilor HTTP - folosirea unui site de test pentru a analiza cererile trimise la server, pe baza autentificării corecte și incorecte.
2.	Crearea cererilor HTTP - scrierea unor cereri HTTP specifice (GET, POST, PUT, DELETE) către un server fictiv, cu utilizarea corectă a anteturilor și parametrilor.
#### Tehnologii utilizate:
 - HTTP – Protocolul pentru trimiterea cererilor și răspunsurilor
 - Developer Tools – Unelte de analiză a cererilor și răspunsurilor în browser
 - Postman/cURL – Pentru testarea manuală a cererilor HTTP


### Exemple de utilizare a proiectului
## Sarcina nr. 1. Analiza cererilor HTTP
#### Cazul in care sunt introduse date incorecte pentru autentificare
 - URL: **http://sandbox.usm.md/login**
 - Metoda HTTP utilizată: **POST**
 - Anteturi trimise: 
 - Parametri trimiși: 
 - Cod de stare returnat: **401 Unauthorized**
 - Anteturi trimise în răspuns:
#### Cazul in care sunt introduse date corecte pentru autentificare
 - URL: **http://sandbox.usm.md/login**
 - Metoda HTTP utilizată: **POST**
 - Anteturi trimise: 
 - Parametri trimiși: 
 - Cod de stare returnat: **200 OK**
 - Anteturi trimise în răspuns:

## Sarcina nr. 2. Crearea cererilor HTTP

## Sarcina nr. 3. Sarcina suplimentară. HTTP_Quest


### Răspunsuri la întrebările de control
#### Ce este protocolul HTTP?
HTTP este un protocol pentru transferul de hipertext, adică un ansamblu de reguli care stabilesc cum se realizează schimbul de date între un client și un server. Hipertextul reprezintă textul ce conține legături către alte texte, similar cu atunci când citiți un articol online și puteți face clic pe anumite cuvinte pentru a deschide alte pagini.
Un protocol este un set de reguli și convenții care reglementează modul în care dispozitivele comunică între ele. În cazul HTTP, acesta definește modul în care clientul și serverul interacționează pentru a face schimb de informații.
#### Pentru ce folosim antetul **User-Agent**?
Antetul User-Agent este un antet dintr-o cerere HTTP care oferă informații despre aplicația client care face cererea, cum ar fi tipul și versiunea browserului sau sistemul de operare. Serverele pot folosi acest antet pentru a personaliza răspunsurile în funcție de client sau pentru a înregistra detalii despre dispozitivul care accesează resursele.
#### Care este diferența dintre metodele **PUT** și **PATCH**?
**PUT**:
 - Se folosește pentru a înlocui complet o resursă de pe server. Când trimiți o cerere PUT, datele existente sunt șterse și înlocuite cu cele noi. Aceasta presupune că furnizezi o reprezentare completă a resursei pe care o actualizezi.
 - Dacă resursa nu există, uneori poate crea una nouă.
**PATCH**:
 - Se folosește pentru a modifica parțial o resursă de pe server. Cu PATCH, nu trebuie să trimiți o reprezentare completă a resursei, ci doar câmpurile pe care dorești să le actualizezi.
 - Este util atunci când ai de făcut doar o mică modificare fără a afecta întreaga resursă.

### Lista surselor utilizate
