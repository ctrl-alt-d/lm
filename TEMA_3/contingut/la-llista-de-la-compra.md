# Pràctica: La Llista de la Compra

## Objectius d'aprenentatge

En aquesta pràctica aprendràs a:
- Manipular el DOM (Document Object Model) amb JavaScript
- Capturar esdeveniments de l'usuari (clics i tecles)
- Crear i afegir elements HTML dinàmicament
- Validar dades d'entrada

---

## 1. Estructura HTML

Primer, crearem l'estructura bàsica del nostre document HTML.

### Fitxer: `index.html`

```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>La llista de la compra</h1>
    <ul id="shopping-list">
    </ul>
    <label for="item-input">Nou article:</label>
    <input type="text" id="item-input" placeholder="Afegeix un article">
    <button id="add-button">Afegeix</button>
    <script src="app.js"></script>
</body>
</html>
```

### Explicació dels elements HTML

| Element | Atribut `id` | Funció |
|---------|--------------|--------|
| `<ul>` | `shopping-list` | Contenidor on apareixeran els articles |
| `<input>` | `item-input` | Camp de text per escriure nous articles |
| `<button>` | `add-button` | Botó per afegir l'article a la llista |

> ⚠️ **Important**: El `<script>` es col·loca al final del `<body>` per assegurar que tots els elements HTML ja existeixen quan s'executa el JavaScript.

---

## 2. JavaScript - Pas a Pas

Ara crearem el fitxer `app.js` que contindrà tota la lògica de la nostra aplicació.

### Pas 2.1: Seleccionar els elements del DOM

El primer que hem de fer és obtenir referències als elements HTML que necessitem manipular.

```javascript
// Elements del DOM
const shoppingList = document.getElementById('shopping-list');
const itemInput = document.getElementById('item-input');
const addButton = document.getElementById('add-button');
```

#### 📚 Concepte: `document.getElementById()`

Aquest mètode cerca un element HTML pel seu atribut `id` i ens retorna una referència a aquest element.

```javascript
document.getElementById('nom-del-id')  // Retorna l'element o null si no existeix
```

---

### Pas 2.2: Crear la funció per afegir articles

Ara crearem una funció que s'executarà cada vegada que l'usuari vulgui afegir un article.

```javascript
// Funció per afegir un article a la llista
function addItem() {
    const itemText = itemInput.value.trim();
    
    if (itemText === '') {
        alert('Si us plau, escriu un article');
        return;
    }
    
    // Crear el nou element de llista
    const li = document.createElement('li');
    li.textContent = itemText;
    shoppingList.appendChild(li);
    
    // Netejar el camp d'entrada
    itemInput.value = '';
    itemInput.focus();
}
```

#### Desglossament de la funció:

**1. Obtenir el text de l'input:**
```javascript
const itemText = itemInput.value.trim();
```
- `.value` → obté el text escrit al camp
- `.trim()` → elimina espais en blanc al principi i al final

**2. Validació:**
```javascript
if (itemText === '') {
    alert('Si us plau, escriu un article');
    return;
}
```
- Comprova que l'usuari ha escrit alguna cosa
- Si està buit, mostra un avís i surt de la funció amb `return`

**3. Crear un nou element `<li>`:**
```javascript
const li = document.createElement('li');
li.textContent = itemText;
```
- `document.createElement('li')` → crea un element `<li>` a memòria
- `.textContent` → assigna el text que mostrarà l'element

**4. Afegir l'element a la llista:**
```javascript
shoppingList.appendChild(li);
```
- `.appendChild()` → afegeix l'element com a fill de la llista `<ul>`

**5. Netejar i enfocar:**
```javascript
itemInput.value = '';
itemInput.focus();
```
- Buida el camp de text
- Posa el cursor al camp per facilitar escriure el següent article

---

### Pas 2.3: Afegir els Event Listeners

Finalment, hem de connectar els esdeveniments de l'usuari amb la nostra funció.

```javascript
// Event listeners
addButton.addEventListener('click', addItem);

// Permetre afegir amb la tecla Enter
itemInput.addEventListener('keypress', function(event) {
    if (event.key === 'Enter') {
        addItem();
    }
});
```

#### 📚 Concepte: `addEventListener()`

Aquest mètode permet "escoltar" esdeveniments en un element.

```javascript
element.addEventListener('tipus_esdeveniment', funció_a_executar);
```

**Esdeveniments utilitzats:**
- `'click'` → quan l'usuari fa clic amb el ratolí
- `'keypress'` → quan l'usuari prem una tecla

---

## 3. Codi complet

### `app.js`

```javascript
// Elements del DOM
const shoppingList = document.getElementById('shopping-list');
const itemInput = document.getElementById('item-input');
const addButton = document.getElementById('add-button');

// Funció per afegir un article a la llista
function addItem() {
    const itemText = itemInput.value.trim();
    
    if (itemText === '') {
        alert('Si us plau, escriu un article');
        return;
    }
    
    // Crear el nou element de llista
    const li = document.createElement('li');
    li.textContent = itemText;
    shoppingList.appendChild(li);
    
    // Netejar el camp d'entrada
    itemInput.value = '';
    itemInput.focus();
}

// Event listeners
addButton.addEventListener('click', addItem);

// Permetre afegir amb la tecla Enter
itemInput.addEventListener('keypress', function(event) {
    if (event.key === 'Enter') {
        addItem();
    }
});
```

---

## 4. Prova l'aplicació

1. Obre el fitxer `index.html` amb un navegador web, pots fer servir l'extensió `Live Server` o similar de `VS Code`.
2. Escriu un article al camp de text (ex: "Pa")
3. Fes clic a "Afegeix" o prem Enter
4. L'article apareixerà a la llista!

---

## 5. Exercicis addicionals (Reptes)

### 🌟 Nivell Bàsic
1. Canvia el text del botó de "Afegeix" a "➕ Afegir"
2. Modifica el `placeholder` de l'input

### 🌟🌟 Nivell Intermedi
3. Afegeix un botó "❌" a cada article per poder eliminar-lo:
   ```javascript
   const deleteButton = document.createElement('button');
   deleteButton.textContent = '❌';
   deleteButton.addEventListener('click', function() {
       li.remove();
       itemInput.focus();
   });
   li.appendChild(deleteButton);
   ```

---

## 6. Resum de conceptes apresos

| Concepte | Descripció |
|----------|------------|
| `document.getElementById()` | Seleccionar elements per ID |
| `document.createElement()` | Crear nous elements HTML |
| `.appendChild()` | Afegir elements fills |
| `.value` | Obtenir/modificar el valor d'un input |
| `.textContent` | Obtenir/modificar el text d'un element |
| `.addEventListener()` | Escoltar esdeveniments |
| `.trim()` | Eliminar espais en blanc |
| `.focus()` | Posar el cursor en un element |

---

## 7. Recursos addicionals

- [MDN Web Docs - Document Object Model](https://developer.mozilla.org/ca/docs/Web/API/Document_Object_Model)
- [MDN Web Docs - addEventListener](https://developer.mozilla.org/ca/docs/Web/API/EventTarget/addEventListener)
- [JavaScript.info - Document](https://javascript.info/document)
