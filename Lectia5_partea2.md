# Lectia 5 - partea 2: Microservicii și Comunicare între Microservicii

## Microservicii
### Ce sunt microserviciile?
Microserviciile sunt o abordare arhitecturală pentru dezvoltarea unei aplicații ca un set de servicii mici, independente, care rulează fiecare în propriul său proces și comunică între ele folosind protocoale ușor de înțeles, cum ar fi HTTP sau mesageria. Aceste servicii sunt construite în jurul nevoilor de afaceri și sunt proiectate pentru a fi scalabile și ușor de întreținut.

### Avantaje ale microserviciilor:
- **Scalabilitate**: Fiecare serviciu poate fi scalat independent, ceea ce permite gestionarea eficientă a cererilor de trafic mare.
- **Flexibilitate**: Schimbările și actualizările pot fi făcute la nivel de serviciu fără a afecta întreaga aplicație.
- **Reziliență**: Dacă un serviciu eșuează, celelalte servicii pot continua să funcționeze fără probleme.

### Dezavantaje ale microserviciilor:
- **Complexitate**: Gestionarea mai multor servicii poate fi dificilă și necesită o infrastructură solidă.
- **Comunicare între servicii**: Asigurarea unei comunicări eficiente între servicii poate fi o provocare.

### Rolul API-urilor în arhitectura microserviciilor
API-urile joacă un rol crucial în arhitectura microserviciilor, deoarece permit serviciilor să comunice între ele și să ofere acces la funcționalități și date. API-urile pot fi folosite pentru a defini interfețe clare și contracte între servicii, facilitând integrarea și colaborarea între ele.

- **Interfata intre microservicii**: API-urile definesc modul în care serviciile pot comunica între ele, inclusiv formatele de date și protocoalele utilizate.
- **Acces la date și funcționalități**: API-urile permit serviciilor să ofere și să acceseze date și funcționalități de la alte servicii.
- **Standardizare și documentare**: API-urile pot fi standardizate și documentate pentru a facilita integrarea și dezvoltarea de noi servicii.
- **Securitate și autorizare**: API-urile pot fi utilizate pentru a gestiona securitatea și autorizarea accesului la date și funcționalități.


## Comunicare între microservicii

### Comunicarea sincrona
În comunicarea sincronă, un serviciu așteaptă un răspuns de la un alt serviciu înainte de a continua execuția. Acest lucru poate duce la întârzieri și blocări în aplicație, deoarece serviciile trebuie să aștepte unul pe celălalt pentru a finaliza operațiunile.

#### Exemplu de comunicare sincronă:
```javascript
function serviciu1() {
    let rezultat = serviciu2();
    console.log(rezultat);
}

function serviciu2() {
    return "Rezultatul serviciului 2";
}

serviciu1();
```
Avantaje:
- Simplu de implementat și de înțeles.
- Util pentru operațiuni simple și secvențiale.
- Ușor de urmărit fluxul de execuție.

Dezavantaje:
- Poate duce la blocări și întârzieri în aplicație.
- Nu este scalabil pentru operațiuni complexe sau cu timp de răspuns mare.
- Poate duce la dependențe strânse între servicii.

### Comunicarea asincrona

În comunicarea asincronă, serviciile pot trimite și primi mesaje fără a aștepta un răspuns imediat. Acest lucru permite serviciilor să continue execuția fără a bloca sau aștepta alte servicii.

#### Exemplu de comunicare asincronă:
```javascript
function serviciu1() {
    serviciu2((rezultat) => {
        console.log(rezultat);
    });
}

function serviciu2(callback) {
    setTimeout(() => {
        callback("Rezultatul serviciului 2");
    }, 2000); // Operațiunea durează 2 secunde
}

serviciu1();
```

Avantaje:

- Permite serviciilor să continue execuția fără a aștepta un răspuns imediat.
- Scalabil pentru operațiuni complexe sau cu timp de răspuns mare.
- Reduce blocările și întârzierile în aplicație.

Dezavantaje:

- Poate fi mai complex de implementat și de gestionat decât comunicarea sincronă.
- Necesită gestionarea mesajelor și a stării între servicii.
- Poate fi dificil de urmărit fluxul de execuție.

### Tehnologii pentru comunicare între microservicii

Există mai multe tehnologii și protocoale disponibile pentru comunicarea între microservicii, inclusiv:

- **HTTP/REST**: Protocolul HTTP și stilul arhitectural REST sunt frecvent folosite pentru comunicarea între microservicii. Acestea oferă o abordare simplă și ușor de înțeles pentru trimiterea și primirea de date între servicii.
- **Mesagerie**: Sistemele de mesagerie, cum ar fi RabbitMQ sau Apache Kafka, pot fi utilizate pentru a trimite și a primi mesaje între servicii. Acestea oferă o abordare asincronă pentru comunicare și pot gestiona volumul mare de mesaje.
- **gRPC**: gRPC este un framework de comunicare RPC (Remote Procedure Call) dezvoltat de Google. Acesta oferă o abordare eficientă și ușor de utilizat pentru comunicarea între servicii folosind protocolul HTTP/2 și serializarea binară.
- **GraphQL**: GraphQL este un limbaj de interogare pentru API-uri dezvoltat de Facebook. Acesta oferă o abordare flexibilă și eficientă pentru comunicarea între servicii, permițând clienților să solicite doar datele de care au nevoie.


## Orchestrarea vs Coregrafie în arhitectura microserviciilor

### Orchestrarea

În orchestrarea, un serviciu central (de obicei un orchestrator sau un serviciu de orchestrare) coordonează și controlează interacțiunile și fluxul de date între servicii. Acest serviciu central decide cum și când să apeleze fiecare serviciu și să gestioneze starea și fluxul de execuție al aplicației.

Exemplu de orchestrare:
```javascript
function orchestrator() {
    let rezultat1 = serviciu1();
    let rezultat2 = serviciu2(rezultat1);
    let rezultat3 = serviciu3(rezultat2);
    console.log(rezultat3);
}

orchestrator();
```

Exemplu: Un orchestrator ar putea face apeluri secvențiale între microserviciile de plată, facturare și livrare.

Avantaje:

- Simplifică gestionarea și controlul fluxului de execuție.
- Permite centralizarea logicii de coordonare și control.
- Ușor de urmărit și de gestionat.

Dezavantaje:

- Poate duce la dependențe strânse între servicii și la un punct unic de eșec.
- Poate fi dificil de scalat și de extins pentru aplicații complexe.
- Poate duce la blocări și întârzieri în aplicație.

### Coregrafie

În coregrafie, fiecare serviciu este responsabil pentru propria sa execuție și comunică cu alte servicii pentru a coordona acțiunile și operațiunile. Nu există un serviciu central care să controleze sau să coordoneze interacțiunile, ci fiecare serviciu reacționează la evenimente și mesaje primite de la alte servicii.

Exemplu de coregrafie:
```javascript
function serviciu1() {
    let rezultat = serviciu2();
    console.log(rezultat);
}

function serviciu2() {
    return "Rezultatul serviciului 2";
}

serviciu1();
```
Exemplu: Microserviciul de facturare și cel de livrare pot reacționa la un eveniment "comandă finalizată" generat de microserviciul de gestionare a comenzilor.

Avantaje:

- Reduce dependențele strânse între servicii și punctele unice de eșec.
- Permite scalabilitate și extensibilitate pentru aplicații complexe.
- Ușor de gestionat și de extins pentru noi funcționalități.


Dezavantaje:

- Poate fi dificil de urmărit și de gestionat fluxul de execuție.
- Necesită gestionarea mesajelor și a stării între servicii.
- Poate duce la întârzieri și blocări în aplicație.


### Alegerea între orchestrare și coregrafie

Alegerea între orchestrare și coregrafie depinde de nevoile și cerințele specifice ale aplicației și a echipei de dezvoltare. În general:

- Orchestrarea este potrivită pentru aplicații cu fluxuri de lucru complexe și structurate, unde este necesar un control centralizat și o coordonare strânsă între servicii.
- Coregrafia este potrivită pentru aplicații cu fluxuri de lucru flexibile și distribuite, unde este importantă scalabilitatea, extensibilitatea și independența între servicii.

În practică, unele aplicații pot folosi o combinație de orchestrare și coregrafie pentru a gestiona diferite aspecte ale aplicației și a fluxurilor de lucru.

## Autorizare și securitate în arhitectura microserviciilor

### Autorizare în arhitectura microserviciilor

Autorizarea în arhitectura microserviciilor se referă la gestionarea accesului și permisiunilor utilizatorilor la date și funcționalități în cadrul aplicației. Aceasta implică definirea și aplicarea politicilor de acces și control al resurselor pentru a asigura că utilizatorii au acces doar la datele și funcționalitățile la care au dreptul.

Strategii de autorizare în arhitectura microserviciilor:

- **JWT (JSON Web Tokens)**: JWT este un standard deschis pentru transmiterea informațiilor între părți sub formă de obiecte JSON. Acestea pot fi utilizate pentru autentificare și autorizare în aplicații web și API-uri.
- **OAuth 2.0**: OAuth 2.0 este un protocol de autorizare deschis care permite aplicațiilor să acceseze resurse protejate în numele utilizatorilor. Acesta oferă un cadru flexibil pentru gestionarea accesului și autorizării în aplicații web și API-uri.
- **RBAC (Role-Based Access Control)**: RBAC este o metodă de control al accesului care se bazează pe roluri și permisiuni. Utilizatorii sunt atribuiți unul sau mai multe roluri, iar aceste roluri determină accesul la resurse și funcționalități.
- **ABAC (Attribute-Based Access Control)**: ABAC este o metodă de control al accesului care se bazează pe atribute și condiții. Accesul la resurse și funcționalități este determinat de atributele utilizatorului și de condițiile definite în politicile de acces.

### Securitate în arhitectura microserviciilor

Securitatea în arhitectura microserviciilor se referă la protejarea datelor și a serviciilor împotriva accesului neautorizat, a atacurilor și a vulnerabilităților. Aceasta implică implementarea unor măsuri de securitate la nivel de serviciu și de rețea pentru a asigura confidențialitatea, integritatea și disponibilitatea datelor și a aplicației.

Măsuri de securitate în arhitectura microserviciilor:

- **Autentificare**: Verificarea identității utilizatorilor și a serviciilor pentru a asigura că acestea au acces doar la datele și funcționalitățile la care au dreptul.
- **Autorizare**: Gestionarea accesului și permisiunilor utilizatorilor la date și funcționalități pentru a asigura că aceștia au acces doar la resursele la care au dreptul.
- **Criptare**: Protejarea datelor în tranzit și în repaus prin criptare pentru a asigura confidențialitatea și integritatea acestora.
- **Gestionarea cheilor**: Protejarea și gestionarea cheilor de criptare pentru a asigura securitatea datelor și a serviciilor.
- **Monitorizare și jurnalizare**: Monitorizarea și jurnalizarea activităților și a evenimentelor pentru a detecta și a răspunde la incidente de securitate.
- **Securitate la nivel de rețea**: Implementarea măsurilor de securitate la nivel de rețea, cum ar fi firewall-uri, VPN-uri și segmentarea rețelei, pentru a proteja serviciile și datele împotriva atacurilor externe.

Autentificare la nivel de API:
```javascript
function autentificare(req, res, next) {
    let token = req.headers.authorization;
    if (token) {
        // Verifică tokenul și autentifică utilizatorul
        next();
    } else {
        res.status(401).json({ message: "Acces neautorizat" });
    }
}
``` 
 **Service Mesh**: Service Mesh este un model de rețea care oferă un nivel de abstractizare între serviciile individuale și infrastructura de rețea subiacentă. Acesta oferă funcționalități precum monitorizarea, gestionarea traficului și securitatea între servicii.

 


