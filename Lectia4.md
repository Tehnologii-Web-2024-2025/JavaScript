# Lecția 4: Evenimente în JavaScript

## 8. Evenimente

Evenimentele sunt acțiuni sau apariții care au loc în browser și la care JavaScript poate reacționa. Ele pot fi generate de utilizator (de exemplu, click-uri, apăsarea tastelor) sau de sistem (de exemplu, încărcarea paginii).

### 8.1. Adăugarea de evenimente la elemente

Pentru a adăuga un eveniment la un element, se folosește metoda `addEventListener`. Aceasta permite atribuirea unui handler (o funcție care va fi executată când evenimentul are loc) unui element pentru un anumit tip de eveniment.

#### Sintaxa de bază:
```javascript
element.addEventListener("tipEveniment", handler);
```

#### Exemplu:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Evenimente în JavaScript</title>
</head>
<body>
    <button id="myButton">Apasă-mă</button>
    <script>
        let button = document.getElementById("myButton");

        button.addEventListener("click", function() {
            alert("Butonul a fost apăsat!");
        });
    </script>
</body>
</html>
```

În acest exemplu, am adăugat un eveniment de tip `click` la butonul cu ID-ul `myButton`. Când butonul este apăsat, se afișează un mesaj de alertă.

### 8.2. Gestionarea evenimentelor

Gestionarea evenimentelor presupune definirea și utilizarea funcțiilor care vor fi apelate atunci când evenimentele au loc. Aceste funcții se numesc **event handlers**.

#### Exemplu de handler:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Gestionarea evenimentelor</title>
</head>
<body>
    <input type="text" id="myInput" placeholder="Tastează ceva...">
    <p id="output"></p>
    <script>
        let input = document.getElementById("myInput");
        let output = document.getElementById("output");

        input.addEventListener("input", function(event) {
            output.textContent = "Ai tastat: " + event.target.value;
        });
    </script>
</body>
</html>
```

În acest exemplu, am adăugat un eveniment de tip `input` la un câmp de text. De fiecare dată când utilizatorul tastează ceva în câmpul de text, textul introdus este afișat în elementul `p` cu ID-ul `output`.

### 8.3. Propagarea evenimentelor

Propagarea evenimentelor descrie modul în care evenimentele se deplasează prin DOM. Există două faze principale de propagare:

1. **Capturarea (capturing phase)**: Evenimentul se deplasează de la rădăcina DOM-ului către elementul țintă.
2. **Bubbling (bubbling phase)**: Evenimentul se deplasează de la elementul țintă înapoi către rădăcina DOM-ului.

#### Adăugarea unui eveniment în faza de capturare:
```javascript
element.addEventListener("tipEveniment", handler, true);
```

#### Adăugarea unui eveniment în faza de bubbling:
```javascript
element.addEventListener("tipEveniment", handler, false);
```

#### Exemplu de propagare a evenimentelor:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Propagarea evenimentelor</title>
    <style>
        .box {
            padding: 20px;
            border: 1px solid black;
            margin: 10px;
        }
    </style>
</head>
<body>
    <div id="div1" class="box">
        Div 1
        <div id="div2" class="box">
            Div 2
            <div id="div3" class="box">
                Div 3
            </div>
        </div>
    </div>

    <script>
        let div1 = document.getElementById("div1");
        let div2 = document.getElementById("div2");
        let div3 = document.getElementById("div3");

        div1.addEventListener("click", function() {
            alert("Div 1 a fost apăsat!");
        }, true); // Capturare

        div2.addEventListener("click", function() {
            alert("Div 2 a fost apăsat!");
        });

        div3.addEventListener("click", function() {
            alert("Div 3 a fost apăsat!");
        });
    </script>
</body>
</html>
```

În acest exemplu, avem trei elemente div în interiorul altor div-uri. Am adăugat evenimente de tip `click` la fiecare div. Evenimentul pentru `div1` este setat să fie capturat (`true`), în timp ce celelalte două sunt setate pentru bubbling (`false`).

### Oprirea propagării evenimentelor

Uneori, este util să oprești propagarea unui eveniment pentru a preveni declanșarea handler-elor din fazele ulterioare de propagare.

#### Folosirea `stopPropagation`:
```javascript
event.stopPropagation();
```

#### Exemplu de oprire a propagării:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Oprirea propagării</title>
    <style>
        .box {
            padding: 20px;
            border: 1px solid black;
            margin: 10px;
        }
    </style>
</head>
<body>
    <div id="outer" class="box">
        Outer Div
        <div id="inner" class="box">
            Inner Div
        </div>
    </div>

    <script>
        let outerDiv = document.getElementById("outer");
        let innerDiv = document.getElementById("inner");

        outerDiv.addEventListener("click", function() {
            alert("Outer Div a fost apăsat!");
        });

        innerDiv.addEventListener("click", function(event) {
            alert("Inner Div a fost apăsat!");
            event.stopPropagation(); // Oprește propagarea
        });
    </script>
</body>
</html>
```

În acest exemplu, evenimentul de click pe `innerDiv` va afișa un mesaj de alertă și va opri propagarea evenimentului, astfel încât handler-ul de pe `outerDiv` nu va fi declanșat.
