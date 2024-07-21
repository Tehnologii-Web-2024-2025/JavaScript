# Lecția 6: Promises și Async/Await în JavaScript

## 10. Promises și Async/Await

Gestionarea codului asincron este esențială în JavaScript pentru a crea aplicații web eficiente și responsive. Promises și Async/Await sunt două concepte fundamentale în acest context.

### 10.1. Introducere în Promises

O promisiune (`Promise`) este un obiect care reprezintă o operațiune care nu a fost completată încă, dar care va fi completată în viitor. O promisiune poate fi într-una din următoarele stări:
- **Pending**: Inițială, încă în curs de desfășurare.
- **Fulfilled**: Operațiunea a avut succes.
- **Rejected**: Operațiunea a eșuat.

#### Crearea unei Promises

```javascript
let promisiune = new Promise((resolve, reject) => {
    // operațiune asincronă
    let succes = true; // să presupunem că operațiunea a avut succes

    if (succes) {
        resolve("Operațiunea a avut succes!");
    } else {
        reject("Operațiunea a eșuat.");
    }
});
```

#### Utilizarea unei Promises

```javascript
promisiune
    .then(result => {
        console.log(result); // "Operațiunea a avut succes!"
    })
    .catch(error => {
        console.error(error); // "Operațiunea a eșuat."
    });
```

### 10.2. Crearea și utilizarea Promises

Să vedem un exemplu complet în care utilizăm Promises pentru a simula o operațiune asincronă, cum ar fi o cerere de date de la un server.

#### Exemplu de Promises

```javascript
function obtineDate() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            let succes = true; // Să presupunem că operațiunea a avut succes
            if (succes) {
                resolve("Datele au fost obținute cu succes!");
            } else {
                reject("Eroare la obținerea datelor.");
            }
        }, 2000); // Operațiunea durează 2 secunde
    });
}

obtineDate()
    .then(result => {
        console.log(result); // "Datele au fost obținute cu succes!"
    })
    .catch(error => {
        console.error(error); // "Eroare la obținerea datelor."
    });
```

În acest exemplu, funcția `obtineDate` returnează o promisiune care se rezolvă după 2 secunde.

### 10.3. Async/Await pentru gestionarea codului asincron

`async` și `await` sunt cuvinte cheie în JavaScript care fac mai ușoară lucrul cu promisiuni și cod asincron. `async` este folosit pentru a declara o funcție asincronă, iar `await` este folosit pentru a aștepta finalizarea unei promisiuni.

#### Crearea unei funcții asincrone

```javascript
async function obtineDateAsync() {
    return "Datele au fost obținute cu succes!";
}
```

#### Utilizarea `await` în interiorul unei funcții `async`

```javascript
async function executa() {
    try {
        let result = await obtineDateAsync();
        console.log(result); // "Datele au fost obținute cu succes!"
    } catch (error) {
        console.error(error);
    }
}

executa();
```

#### Exemplu complet folosind Async/Await

Să vedem un exemplu în care utilizăm `async` și `await` pentru a gestiona o operațiune asincronă.

```javascript
function obtineDate() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            let succes = true; // Să presupunem că operațiunea a avut succes
            if (succes) {
                resolve("Datele au fost obținute cu succes!");
            } else {
                reject("Eroare la obținerea datelor.");
            }
        }, 2000); // Operațiunea durează 2 secunde
    });
}

async function executa() {
    try {
        let result = await obtineDate();
        console.log(result); // "Datele au fost obținute cu succes!"
    } catch (error) {
        console.error(error); // "Eroare la obținerea datelor."
    }
}

executa();
```

În acest exemplu, `executa` este o funcție asincronă care așteaptă finalizarea funcției `obtineDate` și gestionează rezultatul sau eroarea.

### Compararea Promises cu Async/Await

- **Promises**: Oferă o modalitate clară de a gestiona operațiunile asincrone, dar pot deveni greu de citit și de întreținut atunci când există mai multe promisiuni în lanț.
- **Async/Await**: Simplifică gestionarea codului asincron, făcându-l să arate și să se comporte mai mult ca un cod sincron. Este mai ușor de citit și de înțeles, mai ales pentru operațiuni complexe.

