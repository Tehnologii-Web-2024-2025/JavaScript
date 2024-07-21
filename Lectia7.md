# Lecția 7: ES6 și caracteristici avansate în JavaScript

ECMAScript 6 (ES6), cunoscut și sub numele de ECMAScript 2015, a introdus numeroase îmbunătățiri și caracteristici noi în JavaScript. Acestea fac codul JavaScript mai ușor de scris, de citit și de întreținut. În această lecție, vom explora principalele noutăți aduse de ES6.

## 11. ES6 și caracteristici avansate

### 11.1. Introducere în ES6

ES6 reprezintă cea mai semnificativă actualizare a limbajului JavaScript de la crearea sa. Aceasta introduce noi concepte și caracteristici care îmbunătățesc modul de scriere a codului JavaScript. Printre cele mai importante noutăți se numără `let` și `const`, template literals, destructuring, modules, class și inheritance, symbol și iterators.

### 11.2. Noutăți ES6: let și const, template literals, destructuring

#### `let` și `const`

Înainte de ES6, variabilele erau declarate folosind `var`. ES6 introduce două noi moduri de a declara variabile: `let` și `const`.

- `let` este similar cu `var`, dar are scop de bloc (block-scoped) și nu permite redeclararea în același bloc.
- `const` este folosit pentru a declara variabile constante, care nu pot fi reasignate.

Exemplu:
```javascript
let numar = 10;
numar = 20; // OK

const PI = 3.14;
// PI = 3.15; // Eroare: Assignment to constant variable.
```

#### Template literals

Template literals sunt stringuri care permit interpolarea expresiilor și includerea de caractere speciale fără a fi nevoie de concatenări complexe.

Exemplu:
```javascript
let nume = "John";
let mesaj = `Salut, ${nume}!`;
console.log(mesaj); // "Salut, John!"

let multiLine = `Aceasta este o linie.
Aceasta este o altă linie.`;
console.log(multiLine);
```

#### Destructuring

Destructuring permite extragerea valorilor din array-uri sau obiecte și atribuirea lor unor variabile distincte.

Exemplu cu array:
```javascript
let [a, b, c] = [1, 2, 3];
console.log(a); // 1
console.log(b); // 2
console.log(c); // 3
```

Exemplu cu obiect:
```javascript
let persoana = { nume: "Alice", varsta: 25 };
let { nume, varsta } = persoana;
console.log(nume); // "Alice"
console.log(varsta); // 25
```

### 11.3. Modules (import/export)

ES6 introduce module, care permit organizarea codului în fișiere separate și reutilizarea acestuia prin import și export.

#### Export

Exemplu de modul (file: `module.js`):
```javascript
export const salut = () => {
    console.log("Salut, lume!");
};

export const aduna = (a, b) => a + b;
```

#### Import

Exemplu de utilizare a modulului (file: `main.js`):
```javascript
import { salut, aduna } from './module.js';

salut(); // "Salut, lume!"
console.log(aduna(5, 3)); // 8
```

### 11.4. Class și Inheritance

ES6 introduce sintaxa pentru clase, oferind o modalitate mai clară și mai concisă de a defini obiecte și moștenire.

#### Definirea unei clase

Exemplu:
```javascript
class Animal {
    constructor(nume) {
        this.nume = nume;
    }

    vorbeste() {
        console.log(`${this.nume} face un sunet.`);
    }
}

let caine = new Animal("Câine");
caine.vorbeste(); // "Câine face un sunet."
```

#### Moștenirea unei clase

Exemplu:
```javascript
class Caine extends Animal {
    vorbeste() {
        console.log(`${this.nume} latră.`);
    }
}

let rex = new Caine("Rex");
rex.vorbeste(); // "Rex latră."
```

### 11.5. Symbol și Iterators

#### Symbol

Symbol este un tip de date primitiv introdus în ES6, folosit pentru a crea identificatori unici pentru proprietăți de obiecte.

Exemplu:
```javascript
let simbol1 = Symbol("simbol");
let simbol2 = Symbol("simbol");

console.log(simbol1 === simbol2); // false

let obj = {
    [simbol1]: "valoare"
};

console.log(obj[simbol1]); // "valoare"
```

#### Iterators

Iterators sunt obiecte care permit accesul la elementele unei colecții (de exemplu, array-uri) în mod secvențial.

Exemplu de iterator personalizat:
```javascript
let range = {
    from: 1,
    to: 5
};

range[Symbol.iterator] = function() {
    let current = this.from;
    let last = this.to;

    return {
        next() {
            if (current <= last) {
                return { done: false, value: current++ };
            } else {
                return { done: true };
            }
        }
    };
};

for (let num of range) {
    console.log(num); // 1, 2, 3, 4, 5
}
```

