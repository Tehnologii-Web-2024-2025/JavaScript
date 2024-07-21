# Lecția 8: Gestionarea erorilor, framework-uri și biblioteci populare, Best Practices și standarde de codare

## 12. Gestionarea erorilor

Gestionarea erorilor este esențială pentru a crea aplicații robuste și fiabile. JavaScript oferă mai multe mecanisme pentru a gestiona erorile, inclusiv try...catch, throw și obiectul Error.

### 12.1. Try...Catch

Blocul `try...catch` este utilizat pentru a prinde și gestiona erorile care apar în timpul execuției codului.

#### Exemplu de utilizare:

```javascript
try {
    let rezultat = 10 / 0; // Operațiune care ar putea genera o eroare
    console.log(rezultat);
} catch (eroare) {
    console.error("A apărut o eroare:", eroare);
}
```

### 12.2. Throw

Instrucțiunea `throw` este folosită pentru a genera manual o eroare.

#### Exemplu de utilizare:

```javascript
function verificaVarsta(varsta) {
    if (varsta < 18) {
        throw new Error("Trebuie să ai cel puțin 18 ani.");
    }
    return "Acces permis.";
}

try {
    let mesaj = verificaVarsta(15);
    console.log(mesaj);
} catch (eroare) {
    console.error("Eroare:", eroare.message);
}
```

### 12.3. Obiectul Error

Obiectul `Error` este utilizat pentru a crea noi erori. Acesta poate fi personalizat prin adăugarea de mesaje și proprietăți suplimentare.

#### Exemplu de utilizare:

```javascript
try {
    throw new Error("A apărut o eroare personalizată.");
} catch (eroare) {
    console.error(eroare.name); // "Error"
    console.error(eroare.message); // "A apărut o eroare personalizată."
}
```

### 12.4. Promises și gestionarea erorilor

Pentru a gestiona erorile în Promises, se folosește metoda `catch`.

#### Exemplu de utilizare:

```javascript
let promisiune = new Promise((resolve, reject) => {
    reject(new Error("Promisiunea a eșuat."));
});

promisiune
    .then(result => {
        console.log(result);
    })
    .catch(eroare => {
        console.error("Eroare în promisiune:", eroare.message);
    });
```

### 12.5. Async/Await și gestionarea erorilor

Pentru a gestiona erorile în funcții asincrone, se folosește `try...catch`.

#### Exemplu de utilizare:

```javascript
async function obtineDate() {
    try {
        let response = await fetch("https://api.example.com/data");
        let data = await response.json();
        console.log(data);
    } catch (eroare) {
        console.error("A apărut o eroare:", eroare);
    }
}

obtineDate();
```

## 13. Framework-uri și biblioteci populare

JavaScript are numeroase framework-uri și biblioteci care facilitează dezvoltarea aplicațiilor web. Printre cele mai populare se numără React, Angular, Vue.js, și jQuery.

### 13.1. React

React este o bibliotecă JavaScript pentru construirea interfețelor de utilizator. Este dezvoltată de Facebook și folosește o abordare bazată pe componente.

#### Exemplu simplu de componentă React:

```javascript
import React from 'react';
import ReactDOM from 'react-dom';

function Salut(props) {
    return <h1>Salut, {props.nume}!</h1>;
}

ReactDOM.render(<Salut nume="Lume" />, document.getElementById('root'));
```

### 13.2. Angular

Angular este un framework dezvoltat de Google pentru construirea aplicațiilor web complexe. Folosește TypeScript și are o arhitectură bazată pe module și componente.

#### Exemplu simplu de componentă Angular:

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-salut',
  template: `<h1>Salut, {{ nume }}!</h1>`,
})
export class SalutComponent {
  nume: string = 'Lume';
}
```

### 13.3. Vue.js

Vue.js este un framework progresiv pentru construirea interfețelor de utilizator. Este ușor de integrat și folosit pentru a crea aplicații web interactive.

#### Exemplu simplu de componentă Vue:

```javascript
<template>
  <div>
    <h1>Salut, {{ nume }}!</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nume: 'Lume'
    };
  }
};
</script>
```

### 13.4. jQuery

jQuery este o bibliotecă JavaScript care simplifică manipularea DOM și gestionarea evenimentelor. Este ușor de utilizat și foarte popular pentru proiectele web mai mici.

#### Exemplu simplu de utilizare jQuery:

```html
<!DOCTYPE html>
<html>
<head>
  <title>jQuery Exemplu</title>
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
  <script>
    $(document).ready(function() {
      $("button").click(function() {
        $("p").text("Salut, lume!");
      });
    });
  </script>
</head>
<body>
  <button>Click me</button>
  <p></p>
</body>
</html>
```

## 14. Best Practices și standarde de codare

Adoptarea celor mai bune practici și a standardelor de codare în JavaScript este esențială pentru a crea cod de înaltă calitate, ușor de întreținut și scalabil.

### 14.1. Utilizarea `const` și `let` în loc de `var`

Utilizează `const` pentru variabilele care nu se schimbă și `let` pentru cele care se schimbă. Evită utilizarea `var` deoarece are scop de funcție și poate duce la erori neintenționate.

### 14.2. Evitarea utilizării globale a variabilelor

Declarează variabilele doar în scopul lor necesar pentru a evita conflictele și poluarea spațiului global de nume.

### 14.3. Folosirea funcțiilor arrow (=>)

Funcțiile arrow sunt mai concise și nu au propriul context `this`, ceea ce le face utile în anumite situații.

#### Exemplu:

```javascript
let salut = () => console.log("Salut, lume!");
salut();
```

### 14.4. Utilizarea destructuring

Destructuring face codul mai curat și mai ușor de citit atunci când extragi valori din obiecte sau array-uri.

#### Exemplu:

```javascript
let persoana = { nume: "Alice", varsta: 25 };
let { nume, varsta } = persoana;
console.log(nume, varsta);
```

### 14.5. Evitarea callback-urilor profund înlanțuite

Utilizează Promises și `async`/`await` pentru a evita callback-urile profund înlanțuite, care pot face codul dificil de citit și de întreținut.

### 14.6. Comentarii și documentație

Scrie comentarii clare și concise pentru a explica logica complexă și utilizează instrumente de documentație, cum ar fi JSDoc, pentru a descrie funcțiile și parametrii.

#### Exemplu:

```javascript
/**
 * Adună două numere.
 * @param {number} a - Primul număr.
 * @param {number} b - Al doilea număr.
 * @returns {number} Suma celor două numere.
 */
function aduna(a, b) {
    return a + b;
}
```

### 14.7. Structurarea și organizarea codului

Organizează codul în module și fișiere separate pentru a facilita întreținerea și scalabilitatea proiectului. Utilizarea modulelor ES6 pentru a importa și exporta funcționalități este o practică recomandată.

### 14.8. Testare și Debugging

Scrie teste pentru codul tău folosind biblioteci precum Jest sau Mocha pentru a asigura funcționalitatea corectă și pentru a facilita debugging-ul.

Adoptarea acestor best practices și respectarea standardelor de codare vor contribui la dezvoltarea unor aplicații web de înaltă calitate, ușor de întreținut și scalabile.