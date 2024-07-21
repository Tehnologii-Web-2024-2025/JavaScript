Lectia 1

# Introducere în JavaScript

## Ce este JavaScript?

JavaScript este un limbaj de programare de nivel înalt, interpretat, folosit în principal pentru dezvoltarea web. Este unul dintre limbajele fundamentale ale web-ului, alături de HTML și CSS. JavaScript permite dezvoltatorilor să creeze pagini web interactive și dinamice, având capacitatea de a manipula DOM-ul (Document Object Model), de a gestiona evenimente, de a face apeluri asincrone (prin AJAX) și de a lucra cu API-uri.

### Caracteristici principale:
- **Interpretat**: JavaScript este executat direct de browser, fără a necesita o etapă de compilare.
- **Dinamic**: Permite tipuri de date dinamice, ceea ce înseamnă că variabilele pot schimba tipul la runtime.
- **Event-driven**: Suportă programarea bazată pe evenimente, ceea ce permite reacția la acțiunile utilizatorilor.
- **Multiplatformă**: Rulează pe orice dispozitiv care are un browser web.

## Istoria și evoluția JavaScript

JavaScript a fost creat de Brendan Eich în 1995, în timp ce lucra pentru Netscape Communications Corporation. Inițial, limbajul a fost numit Mocha, apoi LiveScript, și în final JavaScript. Evoluția JavaScript poate fi împărțită în mai multe etape:

1. **1995**: Crearea inițială sub numele de Mocha.
2. **1996**: Lansarea sub numele de JavaScript 1.0 de Netscape Navigator.
3. **1997**: Standardizarea de către ECMA International, sub numele ECMAScript.
4. **2009**: ECMAScript 5 (ES5) aduce îmbunătățiri semnificative, inclusiv strict mode.
5. **2015**: ECMAScript 6 (ES6/ES2015) introduce funcții moderne precum `let`, `const`, funcțiile de săgeată, clase și template literals.
6. **2016-prezent**: Lansări anuale aduc îmbunătățiri continue, cum ar fi async/await, module, și multe altele.

## Setarea mediului de dezvoltare

Pentru a începe să scrii și să rulezi JavaScript, ai nevoie de un editor de text și un browser web. Iată pașii pentru a seta mediul de dezvoltare:

1. **Instalează un editor de text**: 
   - Recomandate: Visual Studio Code, Sublime Text, Atom.
   
2. **Instalează un browser modern**:
   - Recomandate: Google Chrome, Mozilla Firefox, Microsoft Edge.

3. **Setează editorul**:
   - Deschide editorul de text și creează un fișier nou cu extensia `.html`.
   - În acest fișier HTML, vei adăuga codul JavaScript.

Exemplu de structură HTML de bază pentru a include JavaScript:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First JavaScript</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <script src="script.js"></script>
</body>
</html>
```

Creează un fișier `script.js` în aceeași locație și adaugă primul tău script JavaScript în el.

## Primul script JavaScript

Vom începe cu un script simplu care va afișa un mesaj în consola browser-ului.

1. **Creează fișierul `script.js`**:
   - Adaugă următorul cod:
   ```javascript
   console.log("Hello, World!");
   ```

2. **Deschide fișierul HTML în browser**:
   - Deschide `index.html` în browser și apasă `F12` sau `Ctrl+Shift+I` pentru a deschide DevTools.
   - Mergi la tab-ul `Console` și vei vedea mesajul "Hello, World!".

### Explicație

- `console.log()` este o funcție încorporată în JavaScript care afișează mesaje în consola web a browserului. Este utilă pentru debug și pentru a vedea output-ul scripturilor.

# Elemente de bază ale JavaScript

## 2. Elemente de bază ale JavaScript

### 2.1. Sintaxă de bază

JavaScript este un limbaj relativ simplu de învățat, iar sintaxa sa de bază include:

- **Declarații**: Includ comenzi și instrucțiuni care sunt executate secvențial.
- **Comentarii**: Pot fi adăugate folosind `//` pentru comentarii pe o singură linie sau `/* ... */` pentru comentarii pe mai multe linii.
- **Case Sensitivity**: JavaScript este sensibil la majuscule și minuscule.

Exemplu de declarații și comentarii:
```javascript
// Aceasta este o declarație
var mesaj = "Salut, lume!"; // Comentariu pe o singură linie

/*
  Acesta este un comentariu
  pe mai multe linii
*/
console.log(mesaj); // Afișează mesajul în consolă
```

### 2.2. Tipuri de date

JavaScript suportă mai multe tipuri de date primitive, inclusiv:

- **String**: Text delimitat de ghilimele simple sau duble (`"Salut"` sau `'Salut'`).
- **Number**: Numere întregi sau cu virgulă mobilă (`42` sau `3.14`).
- **Boolean**: Valori logice adevărat sau fals (`true` sau `false`).
- **Undefined**: O variabilă declarată dar fără valoare.
- **Null**: Reprezintă intenționat absența unei valori.
- **Symbol**: Un tip de date unic, introdus în ECMAScript 6.
- **Object**: O colecție de perechi cheie-valoare.

Exemple:
```javascript
var nume = "John"; // String
var varsta = 30; // Number
var esteStudent = true; // Boolean
var necunoscut; // Undefined
var nimic = null; // Null
```

### 2.3. Declarația variabilelor

În JavaScript, variabilele pot fi declarate folosind `var`, `let` sau `const`.

- **var**: Are o rază de acțiune la nivel de funcție.
- **let**: Are o rază de acțiune la nivel de bloc și este recomandat pentru variabilele care pot fi reasignate.
- **const**: Este folosit pentru constante care nu pot fi reasignate.

Exemplu:
```javascript
var nume = "John";
let varsta = 30;
const pi = 3.14;

nume = "Jane"; // Permis
varsta = 31; // Permis
pi = 3.14159; // Eroare: Assignment to constant variable
```

## 3. Variabile și Operatori

### 3.1. Variabile

Variabilele sunt utilizate pentru a stoca date pe care le putem folosi și modifica pe parcursul programului.

#### Declarație și Inițializare

- **Declarație**: Specifică numele variabilei folosind `var`, `let` sau `const`.
- **Inițializare**: Atribuie o valoare variabilei.

Exemple:
```javascript
var nume = "John"; // Declarație și inițializare
let varsta = 25; // Declarație și inițializare
const pi = 3.14; // Declarație și inițializare
```

### 3.2. Operatori

Operatorii sunt simboluri care efectuează operațiuni asupra variabilelor și valorilor. JavaScript are diferite tipuri de operatori:

#### Operatori aritmetici

- **Adunare (+)**: `a + b`
- **Scădere (-)**: `a - b`
- **Înmulțire (*)**: `a * b`
- **Împărțire (/)**: `a / b`
- **Modul (%)**: `a % b`
- **Exponentiere (**)**: `a ** b`

Exemplu:
```javascript
let x = 10;
let y = 5;

console.log(x + y); // 15
console.log(x - y); // 5
console.log(x * y); // 50
console.log(x / y); // 2
console.log(x % y); // 0
console.log(x ** y); // 100000
```

#### Operatori de atribuire

- **Atribuire simplă (=)**: `x = y`
- **Atribuire cu adunare (+=)**: `x += y` (echivalent cu `x = x + y`)
- **Atribuire cu scădere (-=)**: `x -= y`
- **Atribuire cu înmulțire (*=)**: `x *= y`
- **Atribuire cu împărțire (/=)**: `x /= y`

Exemplu:
```javascript
let x = 10;

x += 5; // x = 15
x -= 3; // x = 12
x *= 2; // x = 24
x /= 4; // x = 6
```

#### Operatori de comparare

- **Egalitate (==)**: `x == y`
- **Egalitate strictă (===)**: `x === y`
- **Diferență (!=)**: `x != y`
- **Diferență strictă (!==)**: `x !== y`
- **Mai mare (>)**: `x > y`
- **Mai mic (<)**: `x < y`
- **Mai mare sau egal (>=)**: `x >= y`
- **Mai mic sau egal (<=)**: `x <= y`

Exemplu:
```javascript
let a = 5;
let b = 10;

console.log(a == b); // false
console.log(a != b); // true
console.log(a < b); // true
console.log(a > b); // false
console.log(a <= b); // true
console.log(a >= b); // false
```

## 4. Structuri de control

### 4.1. If-Else

Instrucțiunea `if` este folosită pentru a executa un bloc de cod dacă o condiție specificată este adevărată. Instrucțiunea `else` poate fi utilizată pentru a executa un bloc de cod dacă condiția este falsă.

Exemplu:
```javascript
let varsta = 18;

if (varsta >= 18) {
    console.log("Ești adult.");
} else {
    console.log("Ești minor.");
}
```

### 4.2. Else-If

Instrucțiunea `else if` adaugă condiții suplimentare.

Exemplu:
```javascript
let scor = 75;

if (scor >= 90) {
    console.log("Nota: A");
} else if (scor >= 80) {
    console.log("Nota: B");
} else if (scor >= 70) {
    console.log("Nota: C");
} else if (scor >= 60) {
    console.log("Nota: D");
} else {
    console.log("Nota: F");
}
```

### 4.3. Switch

Instrucțiunea `switch` evaluează o expresie și execută blocul de cod corespunzător cazului specificat.

Exemplu:
```javascript
let ziua = 3;
let numeZi;

switch (ziua) {
    case 1:
        numeZi = "Luni";
        break;
    case 2:
        numeZi = "Marți";
        break;
    case 3:
        numeZi = "Miercuri";
        break;
    case 4:
        numeZi = "Joi";
        break;
    case 5:
        numeZi = "Vineri";
        break;
    case 6:
        numeZi = "Sâmbătă";
        break;
    case 7:
        numeZi = "Duminică";
        break;
    default:
        numeZi = "Zi invalidă";
}

console.log(numeZi); // Miercuri
```

### 4.4. Bucla For

Bucla `for` este folosită pentru a repeta un bloc de cod de un anumit număr de ori.

Exemplu:
```javascript
for (let i = 0; i < 5; i++) {
    console.log("Numărul este " + i);
}
```

### 4.5. Bucla While

Bucla `while` execută un bloc de cod atâta timp cât o condiție specificată este adevărată.

Exemplu:
```javascript
let i = 0;

while (i < 5) {
    console.log("Numărul este " + i);
    i++;
}
```

### 4.6. Bucla Do-While

Bucla `do-while` este similară cu bucla `while`, dar garantează că blocul de cod este executat cel puțin o dată.

Exemplu:
```javascript
let i = 0;

do {
    console.log("Numărul este " + i);
    i++;
} while (i <

 5);
```


