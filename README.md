# Lucrare de laborator nr. 1. Bazele HTTP

### Scop
Scopul acestei lucrări de laborator este studierea principiilor de bază ale protocolului HTTP, prin analizarea cererilor HTTP și crearea unor cereri HTTP specifice.

### Descrierea lucrarii individuale
Aceasta lucrare de laborator se bazează pe analiza cererilor și răspunsurilor HTTP în cadrul unei aplicații web. Se exploreaza metodele HTTP precum GET, POST, PUT, DELETE si codurile de stare asociate.

### Documentatie scurtă a proiectului
#### Proiectul este structurat pe două sarcini principale:
1.	Analiza cererilor HTTP - folosirea unui site de test pentru a analiza cererile trimise la server, pe baza autentificării corecte și incorecte.
2.	Crearea cererilor HTTP - scrierea unor cereri HTTP specifice (GET, POST, PUT, DELETE) către un server fictiv, cu utilizarea corecta a anteturilor si parametrilor.




## Sarcina nr. 1. Analiza cererilor HTTP
### Cazul in care sunt introduse date incorecte pentru autentificare
 - URL: **http://sandbox.usm.md/login**
 - Metoda HTTP utilizată: **POST**
   
   ![image](https://github.com/user-attachments/assets/16b30b05-69f0-437c-a8c8-18b97fa5c304)

 - Anteturi trimise: **Accept, Accept-Encoding, Accept-Language, Connection, Content-Length, Content-Type, Host, Origin, Referer, User-Agent, X-Requested-With**
   
   ![image](https://github.com/user-attachments/assets/24f6b4bc-1b92-41c2-b591-625c7045086b)

 - Parametri trimisi: **username = "student", password = "studentpass"**
   
   ![image](https://github.com/user-attachments/assets/2ca5e9f2-56c8-4975-9dec-ecb218dd2ae7)

 - Cod de stare returnat: **401 Unauthorized**
   
   ![image](https://github.com/user-attachments/assets/7119a758-f8e0-4f95-967e-0b6521b90bce)

 - Anteturi trimise în raspuns: **Connection, Content-Type, Date, Server, Transfer-Encoding**
   
   ![image](https://github.com/user-attachments/assets/09c10ea2-fabc-4bdb-9c6d-7b43e8a96615)

### Cazul in care sunt introduse date corecte pentru autentificare
 - URL: **http://sandbox.usm.md/login**
 - Metoda HTTP utilizată: **POST**

   ![image](https://github.com/user-attachments/assets/0116d145-df99-4a8b-9198-a02f94e8baa5)
   
 - Anteturi trimise: **Accept, Accept-Encoding, Accept-Language, Connection, Content-Length, Content-Type, Host, Origin, Referer, User-Agent, X-Requested-With**
   
   ![image](https://github.com/user-attachments/assets/4de9da8a-6371-4470-a696-80d87c3ff1e1)
 - Parametri trimisi: **username = "admin", password = "password"**
   
   ![image](https://github.com/user-attachments/assets/efa3ccda-d9ae-446b-9adc-feebd8190f9b)
 - Cod de stare returnat: **200 OK**
   
   ![image](https://github.com/user-attachments/assets/869edae7-534f-452b-b76f-73412d2bb670)
 - Anteturi trimise în raspuns: **Connection, Content-Type, Date, Server, Transfer-Encoding**
   
   ![image](https://github.com/user-attachments/assets/30f5f02c-4790-4cbb-9a45-f382512f3bea)





## Sarcina nr. 2. Crearea cererilor HTTP
#### 1. Scriem o cerere de tip GET către server la adresa http://sandbox.com, indicând în antetul User-Agent numele și prenumele nostru:

![image](https://github.com/user-attachments/assets/00c58a27-489a-465d-8858-a76ac5ce65b8)

#### 2. Scriem o cerere de tip POST către server la adresa http://sandbox.com/cars, indicând în corpul cererii parametri: make: Toyota, model: Corolla, year: 2020
![image](https://github.com/user-attachments/assets/15bbf8d5-95b6-4895-af6a-2084976b052e)
Daca serverul este configurat corect si accepta datele în format JSON, raspunsul ar trebui sa fie un mesaj care confirma primirea datelor. 
Daca totul este corect, masina Toyota Corolla 2020 va fi adaugata pe server.
![image](https://github.com/user-attachments/assets/6124059c-5de9-478a-a446-350d82973f4d)
404 Not Found semnaleaza ca serverul nu poate găsi resursa solicitata.

#### 3. Scriem o cerere de tip PUT către server la adresa http://sandbox.com/cars/1, indicând în antetul User-Agent numele și prenumele nostru, în antetul Content-Type valoarea application/json, iar în corpul cererii următorii parametri: json { "make": "Toyota", "model": "Corolla", "year": 2021 }
![image](https://github.com/user-attachments/assets/7f66f276-85c0-462f-89c9-b435897c82cb)
Prin aceasta cerere PUT, actualizam masina cu ID-ul 1 pentru a reflecta faptul că este un model Toyota Corolla din anul 2021.
Daca masina cu ID-ul 1 nu exista, serverul ar putea returna codul 404 Not Found, semnaland că resursa nu a fost gasită.
![image](https://github.com/user-attachments/assets/41f84d4c-2c45-4da6-8059-a27f75883685)
In cazul dat, masina cu ID-ul 1 nu exista.


#### 4. Scriem unul dintre posibilele raspunsuri ale serverului la cererea anterioara. 
{
    "id": 1,
    "make": "Toyota",
    "model": "Corolla",
    "year": 2020,
    "message": "Car created successfully"
}

#### Presupunem situatiile în care serverul poate returna codurile de stare HTTP 200, 201, 400, 401, 403, 404, 500. http POST /cars HTTP/1.1 Host: sandbox.com Content-Type: application/json User-Agent: John Doe model=Corolla&make=Toyota&year=2020
**200 OK** - Dacă serverul accepta datele și le proceseaza, dar nu creeaza o noua resursa (poate a fost deja inregistrata).

**201 Created** - Cererea POST trimisa creează o noua masina în sistem si serverul confirma crearea resursei.

**400 Bad Request** - Daca trimitem un corp al cererii incomplet sau nevalid, cum ar fi fara campurile make, model, sau year.

**401 Unauthorized** - Daca incercam să facem o cerere fara sa fim autentificat sau fara token de acces corespunzator.

**403 Forbidden** - Daca utilizatorul încearca să creeze sau sa modifice resurse la care nu are acces.

**404 Not Found** - Daca trimitem o cerere la un endpoint inexistent, cum ar fi /cars/9999, unde nu exista nicio masina cu acest ID.

**500 Internal Server Error** - Daca serverul are o eroare interna, cum ar fi o problema cu baza de date.



#### 5. Scriem o cerere de tip DELETE la alegere. De ce, în acest caz, este potrivit să utilizam metoda DELETE?
![image](https://github.com/user-attachments/assets/7cf0e83f-8aca-4137-9f86-0d4b7f58a5ba)

Aceasta cerere trimite o solicitare de stergere a resursei asociate cu masina care are ID-ul 1 de pe serverul sandbox.com.

DELETE /cars/1 HTTP/1.1
Host: sandbox.com
User-Agent: John Doe
Content-Type: application/json

Metoda DELETE este utilizata pentru a solicita stergerea unei resurse de pe server. În acest caz, vrem sa eliminăm masina cu ID-ul 1 din baza de date sau din sistemul de gestionare a masinilor.

Este potrivit să folosim DELETE atunci când intentia este să îndepartam definitiv o resursa, iar cererea semnalizeaza serverului ca nu mai dorim ca acea resursa sa existe.



## Sarcina nr. 3. Sarcina suplimentară. HTTP_Quest
#### Trimitem o cerere de tip POST către server la adresa http://sandbox.usm.md/quest, indicând în antetul User-Agent numele și prenumele nostru. Urmam instrucțiunile de pe server, îndeplinindu-le în ordine.
#### PASUL 1
![image](https://github.com/user-attachments/assets/bfad1456-2978-4e9f-af38-41b1c91ddf67)
![image](https://github.com/user-attachments/assets/7a6e45f0-2322-4540-865c-877dca3d8d07)
#### PASUL 2
![image](https://github.com/user-attachments/assets/10b20227-43b2-417a-a214-c63ff80c6919)
![image](https://github.com/user-attachments/assets/5ad48057-5811-4d23-b87d-d15f61fd575d)
#### PASUL 3
![image](https://github.com/user-attachments/assets/600bdad5-d296-4150-a481-ffe5156ed1bc)
#### PASUL 4
![image](https://github.com/user-attachments/assets/e8541783-82f3-4007-b971-4eed97d5a056)
![image](https://github.com/user-attachments/assets/92241ae3-ac19-4382-acb5-075bc2645b9b)
#### La finalul quest-ului, ni s-a afișat un cuvânt secret: KiMFGQYoEQxsIBAGDEAHLUJEVA==


### Răspunsuri la întrebările de control
#### Ce este protocolul HTTP?
HTTP este un protocol pentru transferul de hipertext, adică un ansamblu de reguli care stabilesc cum se realizeaza schimbul de date între un client și un server. 
Un protocol este un set de reguli și conventii care reglementează modul în care dispozitivele comunică între ele. În cazul HTTP, acesta defineste modul în care clientul și serverul interactioneaza pentru a face schimb de informatii.
#### Pentru ce folosim antetul **User-Agent**?
Antetul User-Agent este un antet dintr-o cerere HTTP care ofera informatii despre aplicația client care face cererea, cum ar fi tipul și versiunea browserului sau sistemul de operare. Serverele pot folosi acest antet pentru a personaliza raspunsurile în functie de client sau pentru a înregistra detalii despre dispozitivul care acceseaza resursele.
#### Care este diferența dintre metodele **PUT** și **PATCH**?

**PUT**:
 - Se foloseste pentru a înlocui complet o resursa de pe server. Când trimitem o cerere PUT, datele existente sunt șterse și înlocuite cu cele noi. 
 - Daca resursa nu exista, uneori poate crea una noua.
   
**PATCH**:
 - Se foloseste pentru a modifica parțial o resursă de pe server. Cu PATCH, nu trebuie să trimitem o reprezentare completa a resursei, ci doar campurile pe care dorim să le actualizam.
 - Este util atunci când avem de făcut doar o mica modificare fara a afecta întreaga resursa.

### Lista surselor utilizate
 - https://moodle.usm.md/pluginfile.php/727758/mod_resource/content/1/Client-Server.%20Ce%20este%20HTTP_.pdf
