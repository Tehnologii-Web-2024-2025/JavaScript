# Lecția 5: AJAX și Fetch API în JavaScript

## 9. AJAX și Fetch API

### 9.1. Introducere în AJAX

AJAX (Asynchronous JavaScript and XML) este o tehnică folosită pentru a crea aplicații web interactive. Prin folosirea AJAX, paginile web pot cere și primi date de la un server fără a reîncărca pagina.

#### Avantajele AJAX:
- Îmbunătățește experiența utilizatorului prin actualizarea părților paginii fără reîncărcare completă.
- Reduce timpul de încărcare și traficul de rețea, deoarece doar datele necesare sunt transferate.
- Permite aplicațiilor web să fie mai dinamice și mai rapide.

### 9.2. Cereri asincrone cu XMLHttpRequest

`XMLHttpRequest` este un obiect JavaScript utilizat pentru a interacționa cu serverele web. Poate fi folosit pentru a trimite și primi date în mod asincron.

#### Exemplu de cerere GET folosind XMLHttpRequest:
```javascript
let xhr = new XMLHttpRequest();
xhr.open("GET", "https://api.example.com/data", true);
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        let response = JSON.parse(xhr.responseText);
        console.log(response);
    }
};
xhr.send();
```

#### Explicația codului:
- `open(method, url, async)`: Inițializează o cerere. `method` este tipul cererii (de exemplu, "GET" sau "POST"), `url` este adresa la care se face cererea, iar `async` specifică dacă cererea este asincronă (`true`) sau sincronă (`false`).
- `onreadystatechange`: Este un handler de eveniment care este apelat ori de câte ori se schimbă starea cererii.
- `readyState`: Indică starea cererii. `4` înseamnă că cererea este completă.
- `status`: Codul de stare al răspunsului HTTP. `200` indică o cerere reușită.
- `responseText`: Conține textul răspunsului primit de la server.

#### Exemplu de cerere POST folosind XMLHttpRequest:
```javascript
let xhr = new XMLHttpRequest();
xhr.open("POST", "https://api.example.com/data", true);
xhr.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        let response = JSON.parse(xhr.responseText);
        console.log(response);
    }
};
let data = JSON.stringify({ key: "value" });
xhr.send(data);
```

### 9.3. Utilizarea Fetch API pentru cereri HTTP

Fetch API este o interfață modernă și mai simplă pentru realizarea cererilor HTTP. Este construită pe promisiuni, ceea ce face mai ușor lucrul cu cererile asincrone.

#### Exemplu de cerere GET folosind Fetch API:
```javascript
fetch("https://api.example.com/data")
    .then(response => {
        if (!response.ok) {
            throw new Error("Rețea de răspuns nu este ok " + response.statusText);
        }
        return response.json();
    })
    .then(data => {
        console.log(data);
    })
    .catch(error => {
        console.error("A existat o problemă cu cererea fetch:", error);
    });
```

#### Explicația codului:
- `fetch(url)`: Inițializează o cerere către `url`.
- `then(response => { ... })`: Primește un obiect `Response`, care trebuie verificat pentru succesul cererii (`response.ok`) și transformat în formatul dorit (de obicei JSON).
- `catch(error => { ... })`: Prinde orice eroare care apare pe parcursul cererii.

#### Exemplu de cerere POST folosind Fetch API:
```javascript
fetch("https://api.example.com/data", {
    method: "POST",
    headers: {
        "Content-Type": "application/json"
    },
    body: JSON.stringify({ key: "value" })
})
.then(response => {
    if (!response.ok) {
        throw new Error("Rețea de răspuns nu este ok " + response.statusText);
    }
    return response.json();
})
.then(data => {
    console.log(data);
})
.catch(error => {
    console.error("A existat o problemă cu cererea fetch:", error);
});
```

### Exemplu complet

Să realizăm un exemplu complet care face o cerere GET și o cerere POST folosind Fetch API și actualizează DOM-ul în consecință.

HTML:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fetch API Exemplu</title>
</head>
<body>
    <h1>Fetch API Exemplu</h1>
    <button id="getDataButton">Obține Date</button>
    <button id="postDataButton">Trimite Date</button>
    <pre id="output"></pre>

    <script src="script.js"></script>
</body>
</html>
```

JavaScript (`script.js`):
```javascript
document.getElementById("getDataButton").addEventListener("click", function() {
    fetch("https://api.example.com/data")
        .then(response => {
            if (!response.ok) {
                throw new Error("Rețea de răspuns nu este ok " + response.statusText);
            }
            return response.json();
        })
        .then(data => {
            document.getElementById("output").textContent = JSON.stringify(data, null, 2);
        })
        .catch(error => {
            console.error("A existat o problemă cu cererea fetch:", error);
        });
});

document.getElementById("postDataButton").addEventListener("click", function() {
    fetch("https://api.example.com/data", {
        method: "POST",
        headers: {
            "Content-Type": "application/json"
        },
        body: JSON.stringify({ key: "value" })
    })
    .then(response => {
        if (!response.ok) {
            throw new Error("Rețea de răspuns nu este ok " + response.statusText);
        }
        return response.json();
    })
    .then(data => {
        document.getElementById("output").textContent = JSON.stringify(data, null, 2);
    })
    .catch(error => {
        console.error("A existat o problemă cu cererea fetch:", error);
    });
});
```

În acest exemplu, avem două butoane: unul pentru a face o cerere GET și unul pentru a face o cerere POST. Răspunsurile sunt afișate într-un element `<pre>` pentru a păstra formatarea JSON.
