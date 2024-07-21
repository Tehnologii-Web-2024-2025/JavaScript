# Lecția 3: Manipularea DOM (Document Object Model) în JavaScript

## 7. Manipularea DOM (Document Object Model)

DOM-ul (Document Object Model) este o reprezentare structurală a documentului HTML care permite accesarea și manipularea elementelor dintr-o pagină web folosind JavaScript.

### 7.1. Accesarea și modificarea elementelor DOM

Pentru a manipula elementele DOM, trebuie să le accesezi mai întâi. Există mai multe metode pentru a accesa elementele:

#### Accesarea elementelor DOM

1. **getElementById**: Accesează un element după ID.
   ```javascript
   let element = document.getElementById("myId");
   ```

2. **getElementsByClassName**: Accesează toate elementele care au o anumită clasă.
   ```javascript
   let elements = document.getElementsByClassName("myClass");
   ```

3. **getElementsByTagName**: Accesează toate elementele de un anumit tip.
   ```javascript
   let elements = document.getElementsByTagName("p");
   ```

4. **querySelector**: Accesează primul element care corespunde unui selector CSS.
   ```javascript
   let element = document.querySelector(".myClass");
   ```

5. **querySelectorAll**: Accesează toate elementele care corespund unui selector CSS.
   ```javascript
   let elements = document.querySelectorAll(".myClass");
   ```

#### Modificarea elementelor DOM

1. **Modificarea textului**:
   ```javascript
   let element = document.getElementById("myId");
   element.textContent = "Text nou";
   ```

2. **Modificarea HTML-ului**:
   ```javascript
   let element = document.getElementById("myId");
   element.innerHTML = "<strong>Text îngroșat</strong>";
   ```

3. **Modificarea stilurilor**:
   ```javascript
   let element = document.getElementById("myId");
   element.style.color = "red";
   element.style.fontSize = "20px";
   ```

4. **Adăugarea și eliminarea claselor**:
   ```javascript
   let element = document.getElementById("myId");
   element.classList.add("nouaClasa");
   element.classList.remove("vecheaClasa");
   ```

### 7.2. Evenimente (click, hover, etc.)

Evenimentele permit interacțiunea utilizatorilor cu pagina web. Poți asculta și răspunde la diferite tipuri de evenimente folosind metodele `addEventListener`.

#### Tipuri de evenimente

1. **Click**:
   ```javascript
   let button = document.getElementById("myButton");
   button.addEventListener("click", function() {
       alert("Butonul a fost apăsat!");
   });
   ```

2. **Hover** (mouseover și mouseout):
   ```javascript
   let element = document.getElementById("myElement");
   element.addEventListener("mouseover", function() {
       element.style.backgroundColor = "yellow";
   });
   element.addEventListener("mouseout", function() {
       element.style.backgroundColor = "";
   });
   ```

3. **Keydown** (când o tastă este apăsată):
   ```javascript
   document.addEventListener("keydown", function(event) {
       console.log("Tasta apăsată: " + event.key);
   });
   ```

4. **Submit** (când un formular este trimis):
   ```javascript
   let form = document.getElementById("myForm");
   form.addEventListener("submit", function(event) {
       event.preventDefault(); // Previne trimiterea formularului
       alert("Formularul a fost trimis!");
   });
   ```

### 7.3. Manipularea atributelor și stilurilor

#### Manipularea atributelor

1. **Setarea unui atribut**:
   ```javascript
   let img = document.getElementById("myImage");
   img.setAttribute("src", "nouaImagine.jpg");
   ```

2. **Obținerea unui atribut**:
   ```javascript
   let img = document.getElementById("myImage");
   let src = img.getAttribute("src");
   console.log(src);
   ```

3. **Eliminarea unui atribut**:
   ```javascript
   let img = document.getElementById("myImage");
   img.removeAttribute("alt");
   ```

#### Manipularea stilurilor

Stilurile CSS ale unui element pot fi manipulate direct folosind proprietatea `style`.

Exemplu:
```javascript
let element = document.getElementById("myElement");
element.style.backgroundColor = "blue";
element.style.width = "200px";
element.style.height = "100px";
```

### Exemplu complet

Să creăm un exemplu complet în care accesăm și modificăm elemente DOM, gestionăm evenimente și manipulăm atribute și stiluri.

HTML:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Manipularea DOM</title>
    <style>
        .highlight {
            background-color: yellow;
        }
    </style>
</head>
<body>
    <h1 id="titlu">Salut, lume!</h1>
    <button id="schimbaText">Schimbă textul</button>
    <button id="schimbaCuloarea">Schimbă culoarea</button>
    <img id="myImage" src="imagine.jpg" alt="O imagine">

    <script src="script.js"></script>
</body>
</html>
```

JavaScript (`script.js`):
```javascript
// Accesarea elementelor
let titlu = document.getElementById("titlu");
let schimbaTextButton = document.getElementById("schimbaText");
let schimbaCuloareaButton = document.getElementById("schimbaCuloarea");
let img = document.getElementById("myImage");

// Eveniment click pentru schimbarea textului
schimbaTextButton.addEventListener("click", function() {
    titlu.textContent = "Textul a fost schimbat!";
});

// Eveniment click pentru schimbarea culorii
schimbaCuloareaButton.addEventListener("click", function() {
    if (titlu.classList.contains("highlight")) {
        titlu.classList.remove("highlight");
    } else {
        titlu.classList.add("highlight");
    }
});

// Manipularea atributelor
img.setAttribute("alt", "O nouă descriere");
```

În acest exemplu, am creat un document HTML simplu cu un titlu, două butoane și o imagine. Am folosit JavaScript pentru a accesa și modifica aceste elemente, pentru a adăuga și elimina clase CSS și pentru a manipula atributele imaginii.
