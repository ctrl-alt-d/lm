## Sessió 8: Posicionament i Disseny en CSS

### Objectius
- Aprendre a posicionar elements de manera relativa i absoluta.
- Introduir-se al disseny amb CSS, utilitzant Flexbox i Grid per estructurar pàgines de manera eficient i flexible.

---

### Continguts

#### 1. Propietats de Posicionament
El posicionament en CSS permet col·locar elements en diferents llocs de la pàgina, utilitzant diversos esquemes.

- **`position: static`**: És el valor per defecte. L'element es posiciona segons el flux normal del document i no es poden aplicar propietats de posicionament com `top`, `right`, `bottom`, o `left`.
  - **Ús**: Elements que no necessiten ser moguts específicament.

- **`position: relative`**: L'element es posiciona segons el flux normal del document, però pot ser desplaçat respecte a la seva posició original utilitzant `top`, `right`, `bottom`, o `left`.
  - **Ús**: Quan es vol moure un element sense treure'l del flux de la pàgina.

- **`position: absolute`**: L'element es posiciona respecte al seu contenidor posicionat més proper (no estàtic). Es treu del flux normal, de manera que no afecta els elements circumdants. Un element amb `position:absolute`, per tal que funcioni correctament, ha d'estar dins un element amb `position:relative`.
  - **Ús**: Per col·locar elements de manera precisa dins d'un contenidor.

- **`position: fixed`**: L'element es posiciona respecte a la finestra del navegador. Es manté fix en la mateixa posició fins i tot quan es fa desplaçament de la pàgina.
  - **Ús**: Per elements com menús fixos o botons de navegació.

---
## Exemple d'Ús de `position: relative`

L'ús de `position: relative` permet desplaçar un element de la seva posició original sense treure'l del flux normal del document. Això vol dir que l'element manté el seu espai reservat en el disseny, però es mou segons les propietats de desplaçament que es defineixin (`top`, `right`, `bottom`, `left`).

### Exemple de Codi

HTML:
```html
<div class="container">
    <div class="box">Caixa amb `position: relative`</div>
</div>
```

CSS:
```css
.container {
    width: 300px;
    height: 200px;
    background-color: lightgray;
    position: relative;
}

.box {
    width: 100px;
    height: 100px;
    background-color: coral;
    position: relative;
    top: 20px;
    left: 30px;
}
```



### Explicació
- **.container**: Un contenidor de mida fixa amb `position: relative` (aquí no es fa servir per desplaçar, però es pot fer si cal).
- **.box**: Una caixa de 100x100 píxels que es desplaça 20 píxels cap avall (`top: 20px`) i 30 píxels cap a la dreta (`left: 30px`).
- La caixa es mou respecte a la seva posició original, però l'espai que ocupava originalment encara es manté al document.

Aquest exemple demostra com es pot moure un element de la seva posició original sense afectar la disposició d'altres elements.

---

## Exemple d'Ús de `position: absolute`

L'ús de `position: absolute` permet posicionar un element de manera precisa respecte al seu contenidor més proper amb `position` definit (pot ser `relative`, `absolute`, `fixed`, o `sticky`). Quan un element té `position: absolute`, es treu del flux normal del document, i no afecta la posició dels altres elements.

### Exemple de Codi

HTML:
```html
<div class="container">
    <div class="box">Caixa amb `position: absolute`</div>
</div>
```

CSS:
```css
.container {
    width: 300px;
    height: 200px;
    background-color: lightgray;
    position: relative; /* Contenidor de referència */
}

.box {
    width: 100px;
    height: 100px;
    background-color: coral;
    position: absolute;
    top: 20px;
    left: 30px;
}
```

### Explicació
- **.container**: Un contenidor de mida fixa amb `position: relative`, que serveix com a referència per a l'element amb `position: absolute`.
- **.box**: Una caixa de 100x100 píxels que es posiciona 20 píxels des de la part superior del contenidor i 30 píxels des de l'esquerra.
- L'element `.box` es treu del flux normal, de manera que no afecta la posició d'altres elements dins del contenidor. Es posiciona respecte al `.container`, ja que aquest té `position: relative`.

Aquest exemple il·lustra com `position: absolute` permet col·locar un element de manera precisa dins d'un contenidor posicionat.

---

## Explicació de `position: sticky`

La propietat `position: sticky` combina característiques de `relative` i `fixed`. Un element amb `position: sticky` es comporta inicialment com un element amb `position: relative`, però es fixa (adhereix) en una posició concreta quan l'usuari es desplaça per la pàgina, mantenint-se visible fins que es compleixin certes condicions dins del seu contenidor pare.

### Com funciona
- L'element es manté en la seva posició relativa fins que l'usuari es desplaça per la pàgina i es troba amb el punt definit (per exemple, `top: 10px`).
- Quan aquest punt es compleix, l'element es "fixa" en aquesta posició i es manté visible, seguint el desplaçament de l'usuari fins que el seu contenidor pare surti del camp de visió.

### Exemple de Codi

HTML:
```html
<div class="container">
    <div class="sticky-element">Element Sticky</div>
    <p>Alt contingut aquí...</p>
</div>
```

CSS:
```css
.container {
    height: 1000px;
    background-color: lightgray;
}

.sticky-element {
    background-color: coral;
    padding: 10px;
    position: sticky;
    top: 20px;
}
```

### Explicació
- **.container**: Un contenidor alt per demostrar l'efecte de desplaçament.
- **.sticky-element**: Un element que es manté fixat a 20 píxels de la part superior de la finestra quan es fa desplaçament. Quan l'usuari es desplaça cap avall i arriba a aquest punt, l'element es fixa a la posició definida fins que el contenidor ja no sigui visible. **Per tal que quedi enganxat, és important dir-li respecte que s'ha d'engancar, en aquest exemple, respecte el `top: 20px` , és a dir, quedarà a 20px de la part superior de la finestra.**

### Ús Comú
- **Barres de navegació**: Mantenir menús visibles a la part superior de la pàgina quan es desplaça.
- **Titulars o seccions destacades**: Mantenir seccions importants a la vista de l'usuari mentre es desplaça pel contingut.

Aquest comportament és útil per millorar la usabilitat i la navegació a les pàgines amb molt de contingut.

---

Més informació a w3schools: [CSS Positioning](https://www.w3schools.com/css/css_positioning.asp)

---

## Exercici

Observa aquest diseny i intenta replicar-lo utilitzant les propietats de posicionament de CSS (static, relative, absolute, fixed, sticky).

![Exemple de Diseny](https://i.imgur.com/CA7STuj.png)

### Millores:

1.- Una de les ofertes ha de tenir, centrada a la cantonada de dalt a la dreta, una rodona que digui 'millor oferta' (`position: absolute`)
2.- A baix a l'esquerra hi ha d'haver un botó d'ajuda. Encara que fem scroll de la pàgina el botó s'ha de mantenir allà mateix (`position: fixed`)
3.- Opcional: Les ofertes han de quedar 'engaxades' a la part de dalt de la pàgina quan fem scrol (`position: sticky`)

Per [centrar el text](https://stackoverflow.com/a/78651219/842935) dins el div pots fer servir:

```css
.box {
  align-content: center; /* vertical */
  text-align: center; /* horitzontal */
}
```

---

#### 2. Introducció a Flexbox
Flexbox és un model de disseny que facilita la creació de layouts flexibles i dinàmics. Permet alinear i distribuir elements de manera eficient dins d'un contenidor.

- **Conceptes Bàsics**:
  - **Contenidor Flex (`display: flex`)**: Transforma un element en un contenidor flex, i els seus elements fills es converteixen en elements flexibles.
  - **`justify-content`**: Alinea els elements horitzontalment dins del contenidor.
    - **Opcions**: `flex-start`, `flex-end`, `center`, `space-between`, `space-around`.
  - **`align-items`**: Alinea els elements verticalment dins del contenidor.
    - **Opcions**: `stretch`, `flex-start`, `flex-end`, `center`, `baseline`.
  - **`flex`**: Defineix com un element flexible ha de créixer, encongir-se i ocupar espai dins del contenidor. (The flex property is a shorthand property for the flex-grow, flex-shrink, and flex-basis properties.)
    - **Sintaxi**: `flex: grow shrink basis;`
    - **Exemple**: `flex: 1 0 100px;` (creix, no es redueix, base de 100px).
  - Altres propietats: `flex-direction`, `flex-wrap`, `align-content`, etc.

- **Exemple**:
```html
  <div style="display: flex; justify-content: space-between; align-items: center;">
    <div style="flex: 1;">Element 1</div>
    <div style="flex: 2;">Element 2</div>
    <div style="flex: 1;">Element 3</div>
  </div>
```

---

Més informació a w3schools: [CSS Flexbox](https://www.w3schools.com/css/css3_flexbox.asp)

---

#### 3. Introducció a CSS Grid
CSS Grid és un sistema de disseny basat en una estructura de graella de files i columnes, oferint un control precís sobre la distribució dels elements.

- **Conceptes Bàsics**:
  - **Contenidor Grid (`display: grid`)**: Transforma un element en un contenidor de graella, i els seus elements fills es posicionen en una estructura de files i columnes.
  - **`grid-template-columns`**: Defineix el nombre i la mida de les columnes.
    - **Exemple**: grid-template-columns: 1fr 2fr 1fr; (tres columnes amb proporcions diferents).
  - **`grid-template-rows`**: Defineix el nombre i la mida de les files.
    - **Exemple**: grid-template-rows: 100px auto 50px; (tres files amb mides diferents).
  - **`gap`**: Defineix l'espai entre files i columnes.
    - **Exemple**: gap: 20px; (espai de 20px entre files i columnes).

- **Exemple**:
```html
  <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
    <div>Element 1</div>
    <div>Element 2</div>
    <div>Element 3</div>
    <div>Element 4</div>
  </div>
```

---

Més informacio a w3schools: [CSS Grid Layout](https://www.w3schools.com/css/css_grid.asp)

---

## CSS Grid vs. Flexbox: Quan Utilitzar Cada Un?

### 1. CSS Grid
**Descripció**: CSS Grid és un sistema de disseny bidimensional que et permet crear layouts en files i columnes. És ideal per construir estructures complexes que necessiten organitzar elements en una graella completa.

- **Quan utilitzar CSS Grid**:
  - **Layouts Complets**: Quan necessites dissenyar la disposició general d'una pàgina web, com dividir la pàgina en una capçalera, una barra lateral, el contingut principal, i un peu de pàgina.
  - **Dissenys Bidimensionals**: Quan vols controlar tant la disposició horitzontal com vertical dels elements. Per exemple, si has d'alinear elements en una estructura de files i columnes.
  - **Casos d'ús**: Galeries d'imatges, layouts complexos de pàgina, taules de preus amb diferents seccions, etc.

- **Exemple**:
```html
  <div style="display: grid; grid-template-columns: 1fr 2fr; gap: 20px;">
    <div>Element 1</div>
    <div>Element 2</div>
  </div>
```
  - **Explicació**: Aquest exemple crea una graella amb dues columnes, la primera amb una fracció de l'espai i la segona amb dues fraccions.

---

### 2. Flexbox
**Descripció**: Flexbox és un sistema de disseny unidimensional que et permet alinear i distribuir elements de manera flexible al llarg d'una sola dimensió (horitzontal o vertical).

- **Quan utilitzar Flexbox**:
  - **Alineació Simple**: Quan necessites alinear elements en una sola fila o columna. És útil per a dissenys que només requereixen organitzar elements al llarg d'una dimensió.
  - **Distribució Dinàmica**: Quan vols distribuir espai de manera uniforme o fer que els elements s'ajustin dinàmicament a l'espai disponible. Per exemple, distribuir botons horitzontalment o alinear contingut verticalment en un contenidor.
  - **Casos d'ús**: Barres de navegació, grups de botons, alineació de targetes en una fila, elements centrats verticalment dins d'un contenidor.

- **Exemple**:
```html
  <div style="display: flex; justify-content: space-between;">
    <div>Element 1</div>
    <div>Element 2</div>
    <div>Element 3</div>
  </div>
```
  - **Explicació**: Aquest exemple distribueix els elements amb espai igual entre ells, utilitzant Flexbox per a l'alineació horitzontal.

---

### Resum
- **Utilitza CSS Grid** quan necessitis estructurar dissenys complexes en dues dimensions (files i columnes).
- **Utilitza Flexbox** quan només necessitis alinear o distribuir elements en una sola dimensió (horitzontal o vertical).

Cada sistema té els seus punts forts i es poden utilitzar junts en el mateix projecte per obtenir més flexibilitat en el disseny de la pàgina.

