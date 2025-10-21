# Propietats CSS fonamentals

## Objectius

Treballar amb les propietats de text, color i fons per millorar l'aparença d'una pàgina web.

## Continguts

### 1. Propietats de text

Aquestes propietats permeten ajustar l'estil del text per millorar la seva llegibilitat i aparença.

#### a. Font (font-family)
Defineix el tipus de lletra utilitzat en el text.
**Exemple:**
```css
font-family: Arial, sans-serif;
```

#### b. Grandària de la font (font-size)
Ajusta la mida del text.
**Exemple:**
```css
font-size: 16px;
```

#### c. Alineació de text (text-align)
Permet alinear el text a l'esquerra, dreta, centre o justificar-lo.
**Exemples:**
```css
text-align: left;
text-align: right;
text-align: center;
text-align: justify;
```

#### d. Espaiat (line-height, letter-spacing)
- **line-height**: Defineix l'espai entre línies de text.
  **Exemple:**
```css
  line-height: 1.5;
```

- **letter-spacing**: Defineix l'espai entre caràcters.
  **Exemple:**
```css
  letter-spacing: 2px;
```

---

### 2. Color de text i fons

Aquestes propietats permeten definir el color del text i el color de fons d'un element.

#### a. Color del text (color)
Defineix el color del text.
**Exemple:**
```css
color: #333333;
```

#### b. Color de fons (background-color)
Defineix el color de fons d'un element.
**Exemple:**
```css
background-color: #f0f0f0;
```

---

### 3. Imatges de fons

Pots utilitzar una imatge com a fons d'un element amb la propietat background-image.
**Exemple:**
```css
background-image: url('path/to/image.jpg');
```

També pots ajustar la repetició, posició i mida de la imatge de fons:

- **background-repeat**: Defineix si la imatge es repeteix.
  **Exemple:**
```css
  background-repeat: no-repeat;
```

- **background-position**: Defineix la posició de la imatge de fons.
  **Exemple:**
```css
  background-position: center;
```

- **background-size**: Ajusta la mida de la imatge.
  **Exemple:**
```css
  background-size: cover;
```


## Annex: Tipus de Grandària en CSS

Quan definim la mida de les propietats en CSS, podem utilitzar diferents unitats. A continuació es descriuen les més comunes:

### 1. Pixels (px)
- **Descripció**: Una unitat fixa que representa un píxel a la pantalla.
- **Ús comú**: Ideal per a dissenys on es necessita precisió en mides fixes.
- **Exemple**: font-size: 16px;

### 2. Em (em)
- **Descripció**: Una unitat relativa basada en la mida de la font del seu element pare. 1em és igual a la mida de la font actual.
- **Ús comú**: Per mides relatives que es redimensionin en funció de la mida de la font pare.
- **Exemple**: font-size: 1.5em;

### 3. Rem (rem)
- **Descripció**: Similar a em, però basada en la mida de la font de l'arrel (root). 1rem és igual a la mida de la font de l'element root.
- **Ús comú**: Per mantenir mides consistents i fàcilment escalables a tota la pàgina.
- **Exemple**: font-size: 2rem;

### 4. Percentatge (%)
- **Descripció**: Una unitat relativa basada en el context de l'element pare. Per exemple, un font-size del 50% serà la meitat de la mida de la font de l'element pare.
- **Ús comú**: Per fer que els elements s'adaptin de manera proporcional.
- **Exemple**: width: 100%;

### 5. Points (pt)
- **Descripció**: Unitats de mida que s'utilitzen principalment per a mitjans impresos. Un punt (pt) és 1/72 d'una polzada.
- **Ús comú**: Menys comú en disseny web, més utilitzat en CSS per a documents impresos.
- **Exemple**: font-size: 12pt;

### 6. Viewport Units (vw, vh)
- **Descripció**: Unitats relatives a la mida de la finestra del navegador (viewport). 
  - **vw**: Percentatge de l'ample de la finestra.
  - **vh**: Percentatge de l'altura de la finestra.
- **Ús comú**: Per fer que els elements s'adaptin a la mida de la finestra del navegador.
- **Exemples**: 
  - width: 50vw; (50% de l'ample de la finestra)
  - height: 100vh; (100% de l'altura de la finestra)


## Annex: Colors en CSS

En CSS, podem definir els colors utilitzant diversos formats. Aquests són els més comuns:

### 1. Colors per Nom
- **Descripció**: Alguns colors comuns es poden definir simplement pel seu nom.
- **Exemples**: 
  - color: red;
  - color: blue;
  - color: green;

### 2. Colors Hexadecimal (Hex)
- **Descripció**: Es defineixen amb un codi de sis dígits precedit pel símbol #. Els primers dos dígits representen el vermell, els següents dos el verd, i els últims dos el blau.
- **Exemples**: 
  - color: #ff0000; (vermell)
  - color: #00ff00; (verd)
  - color: #0000ff; (blau)

### 3. RGB (Red, Green, Blue)
- **Descripció**: Es defineixen utilitzant valors decimals per a cada component de color, entre 0 i 255.
- **Exemple**: 
  - color: rgb(255, 0, 0); (vermell)
  - color: rgb(0, 255, 0); (verd)
  - color: rgb(0, 0, 255); (blau)

### 4. RGBA (Red, Green, Blue, Alpha)
- **Descripció**: És una extensió de RGB que inclou un canal alpha per a la transparència. El valor alpha va de 0 (completament transparent) a 1 (completament opac).
- **Exemple**: 
  - color: rgba(255, 0, 0, 0.5); (vermell amb 50% de transparència)

### 5. HSL (Hue, Saturation, Lightness)
- **Descripció**: Es defineixen en funció del to (hue), la saturació i la lluminositat. El to (hue) es mesura en graus (de 0 a 360), on cada valor representa un color específic al cercle cromàtic. La saturació i la lluminositat es representen en percentatge (0% és el valor més baix).
- **Exemples**:
  - color: hsl(0, 100%, 50%); (vermell pur)
  - color: hsl(120, 100%, 50%); (verd pur)
  - color: hsl(240, 100%, 50%); (blau pur)

### 6. HSLA (Hue, Saturation, Lightness, Alpha)
- **Descripció**: Similar a HSL però inclou un valor alpha que permet ajustar la transparència del color. El valor alpha va de 0 (completament transparent) a 1 (completament opac).
- **Exemples**:
  - color: hsla(0, 100%, 50%, 0.5); (vermell amb 50% de transparència)
  - color: hsla(120, 100%, 50%, 0.3); (verd amb 30% de transparència)
  - color: hsla(240, 100%, 50%, 0.8); (blau amb 80% de transparència)

## Annex: Exemple d'HTML i CSS amb les Propietats Fonamentals

### Exemple d'HTML

```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Exemple de Propietats CSS Fonamentals</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Benvinguts al meu lloc web</h1>
        <p>Un exemple bàsic d'ús de propietats CSS fonamentals</p>
    </header>
    <main>
        <section class="content">
            <h2>Secció principal</h2>
            <p>Aquest és un text amb diferents estils i colors per demostrar l'ús de les propietats CSS.</p>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 El meu lloc web</p>
    </footer>
</body>
</html>
```

---

### Exemple de CSS

```css
/* Estils generals */
body {
    font-family: Arial, sans-serif;
    font-size: 16px;
    line-height: 1.5;
    color: #333;
    background-color: #f9f9f9;
    margin: 0;
    padding: 20px;
}

/* Estils de l'encapçalament */
header {
    text-align: center;
    background-color: #4CAF50;
    color: white;
    padding: 20px;
}

h1 {
    font-size: 2.5em;
    margin: 0;
}

p {
    font-size: 1em;
    letter-spacing: 1px;
}

/* Estils de la secció principal */
.content {
    background-color: #ffffff;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 5px;
    margin-top: 20px;
}

h2 {
    text-align: left;
    color: #4CAF50;
}

p {
    color: #555;
}

/* Estils del peu de pàgina */
footer {
    text-align: center;
    font-size: 0.9em;
    color: #777;
    margin-top: 20px;
}
```

