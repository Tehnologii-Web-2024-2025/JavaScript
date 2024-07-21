 Funcții, Obiecte și Arrays în JavaScript

## 5. Funcții

### 5.1. Definirea funcțiilor

Funcțiile sunt blocuri de cod reutilizabile care pot fi apelate ori de câte ori este nevoie. O funcție este definită folosind cuvântul-cheie `function`, urmat de un nume, o listă de parametri între paranteze și un bloc de cod între acolade.

Exemplu de funcție simplă:
```javascript
function salut() {
    console.log("Salut, lume!");
}

salut(); // Apelează funcția și afișează "Salut, lume!" în consolă
```

### 5.2. Funcții cu parametri

Funcțiile pot accepta parametri care sunt valori furnizate funcției atunci când este apelată.

Exemplu de funcție cu parametri:
```javascript
function salut(nume) {
    console.log("Salut, " + nume + "!");
}

salut("John"); // Afișează "Salut, John!"
salut("Jane"); // Afișează "Salut, Jane!"
```

### 5.3. Funcții cu valoare de retur

Funcțiile pot returna valori folosind cuvântul-cheie `return`.

Exemplu de funcție cu valoare de retur:
```javascript
function aduna(a, b) {
    return a + b;
}

let suma = aduna(5, 10);
console.log(suma); // Afișează 15
```

### 5.4. Funcții anonime și funcții de săgeată

Funcțiile anonime nu au un nume și sunt adesea folosite ca expresii. Funcțiile de săgeată (`arrow functions`) sunt o sintaxă scurtată pentru funcțiile anonime, introdusă în ECMAScript 6.

Exemplu de funcție anonimă:
```javascript
let salut = function(nume) {
    console.log("Salut, " + nume + "!");
};

salut("John");
```

Exemplu de funcție de săgeată:
```javascript
let salut = (nume) => {
    console.log("Salut, " + nume + "!");
};

salut("Jane");
```

## 6. Obiecte și Arrays

### 6.1. Obiecte

Obiectele sunt colecții de perechi cheie-valoare, unde cheile sunt nume de proprietăți și valorile pot fi de orice tip.

#### Crearea unui obiect

Un obiect poate fi creat folosind notația cu acolade `{}`.

Exemplu de obiect:
```javascript
let persoana = {
    nume: "John",
    varsta: 30,
    salut: function() {
        console.log("Salut, numele meu este " + this.nume);
    }
};

console.log(persoana.nume); // Afișează "John"
console.log(persoana.varsta); // Afișează 30
persoana.salut(); // Afișează "Salut, numele meu este John"
```

### 6.2. Arrays

Arrays (tablouri) sunt liste ordonate de valori. Fiecare valoare are un indice numeric, începând de la 0.

#### Crearea unui array

Un array poate fi creat folosind notația cu paranteze pătrate `[]`.

Exemplu de array:
```javascript
let numere = [1, 2, 3, 4, 5];

console.log(numere[0]); // Afișează 1
console.log(numere[2]); // Afișează 3
```

### 6.3. Metode și proprietăți ale obiectelor și arrays

#### Metode ale obiectelor

Obiectele pot avea metode, care sunt funcții stocate ca proprietăți.

Exemplu de metodă:
```javascript
let masina = {
    marca: "Toyota",
    model: "Corolla",
    detalii: function() {
        return this.marca + " " + this.model;
    }
};

console.log(masina.detalii()); // Afișează "Toyota Corolla"
```

#### Metode și proprietăți ale arrays

Arrays au numeroase metode și proprietăți utile.

Exemplu de metode și proprietăți ale arrays:
```javascript
let fructe = ["mere", "banane", "cireșe"];

console.log(fructe.length); // Afișează 3
fructe.push("portocale"); // Adaugă "portocale" la sfârșitul array-ului
console.log(fructe); // Afișează ["mere", "banane", "cireșe", "portocale"]
fructe.pop(); // Elimină ultimul element
console.log(fructe); // Afișează ["mere", "banane", "cireșe"]
```

### 6.4. Iterarea prin arrays și obiecte

#### Iterarea prin arrays

Poți parcurge elementele unui array folosind o buclă `for` sau metoda `forEach`.

Exemplu de buclă `for`:
```javascript
let numere = [1, 2, 3, 4, 5];

for (let i = 0; i < numere.length; i++) {
    console.log(numere[i]);
}
```

Exemplu de metodă `forEach`:
```javascript
let numere = [1, 2, 3, 4, 5];

numere.forEach(function(numar) {
    console.log(numar);
});
```

#### Iterarea prin obiecte

Poți parcurge proprietățile unui obiect folosind o buclă `for-in`.

Exemplu de buclă `for-in`:
```javascript
let persoana = {
    nume: "John",
    varsta: 30,
    oras: "București"
};

for (let cheie in persoana) {
    console.log(cheie + ": " + persoana[cheie]);
}
```


