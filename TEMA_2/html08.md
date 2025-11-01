## Sessió 7: Model de Caixa de CSS (Box Model)

### Objectius
- Entendre com funciona el model de caixa en CSS.
- Aplicar marges, farcits, i dimensions als elements.
- Veure altres propietats relacionades amb el model de caixa però que no afecten l'espai ocupat per l'element (outline, box-shadow).

### Continguts

#### 1. El Model de Caixa
Tots els elements HTML es representen com a caixes que consten de diverses capes. Aquestes capes inclouen:
- **Contingut (Content)**: L'àrea on es mostra el contingut, com el text o les imatges.
- **Farcit (Padding)**: L'espai entre el contingut i la vora de la caixa.
- **Contorn (Border)**: Un contorn que envolta el farcit (si està definit).
- **Marge (Margin)**: L'espai fora del contorn que separa l'element d'altres elements.

---

#### 2. Propietats Principals del Model de Caixa

**a. `margin`**
- Defineix l'espai exterior de la caixa (fora del contorn).
- **Exemples**:
  - margin: 20px; (defineix un marge de 20 píxels a tots els costats)
  - margin-top: 10px; (marge superior)
  - margin-right: 15px; (marge dret)
  - margin-bottom: 10px; (marge inferior)
  - margin-left: 5px; (marge esquerre)

**b. `padding`**
- Defineix l'espai interior de la caixa (entre el contingut i el contorn).
- **Exemples**:
  - padding: 15px; (defineix un farcit de 15 píxels a tots els costats)
  - padding-top: 5px; (farcit superior)
  - padding-right: 10px; (farcit dret)
  - padding-bottom: 5px; (farcit inferior)
  - padding-left: 10px; (farcit esquerre)

**c. `border`**
- Defineix un contorn al voltant de l'element.
- **Exemples**:
  - border: 2px solid #000; (un contorn de 2 píxels, línia contínua, color negre)
  - border-top: 1px dashed #ccc; (contorn superior de línia discontínua)
  - border-radius: 10px; (fa les vores arrodonides)

**d. `width` i `height`**
- Defineixen l'ample i l'altura del contingut de la caixa (no inclouen marges, farcits ni contorns).
- **Exemples**:
  - width: 100px; (ample de 100 píxels)
  - height: 200px; (altura de 200 píxels)

---

#### 3. Diferència entre Marges, Farcits i Contorns
- **Marge (Margin)**: Espai fora de la caixa que separa l'element d'altres elements.
- **Farcit (Padding)**: Espai dins de la caixa que separa el contingut del contorn.
- **Contorn (Border)**: Línia que envolta el farcit i defineix els límits de la caixa.

---

## Esquema en ASCII del Model de Caixa

Aquest esquema mostra la disposició del `margin`, `border`, `padding` i `content` en una caixa CSS.

```plaintext
+-----------------------------+
|         MARGIN              |
|  +------------------------+ |
|  |       BORDER           | |
|  |  +-------------------+ | |
|  |  |     PADDING       | | |
|  |  |  +-------------+  | | |
|  |  |  |  CONTENT    |  | | |
|  |  |  +-------------+  | | |
|  |  +-------------------+ | |
|  +------------------------+ |
+-----------------------------+
```

### Descripció
- **MARGIN**: Espai exterior que envolta el contorn de la caixa.
- **BORDER**: Contorn que envolta el farcit de la caixa.
- **PADDING**: Espai entre el contingut i el contorn.
- **CONTENT**: L'àrea on es mostra el contingut, com text o imatges.

---

Més informació a w3schools: [CSS Box Model](https://www.w3schools.com/css/css_boxmodel.asp)

### Exercicis Pràctics
1. **Exercici 1**: Defineix una caixa amb un contorn de 2 píxels, un farcit de 10 píxels i un marge de 20 píxels.
2. **Exercici 2**: Experimenta canviant les propietats de `margin` i `padding` per veure com afecten la disposició dels elements.
3. **Exercici 3**: Fes servir `border-radius` per crear una caixa amb les cantonades arrodonides.


## Exercicis per calcular l'amplada total

### Exercici 1
Aquest `<div>` tindrà una amplada total de 210px i una altura total de 110px:

```css
div {
  width: 200px;
  height: 100px;
  padding: 15px;
  border: 5px solid black;
  margin: 0;
}
```

**Càlcul de l'amplada:**
```plaintext
  200px (amplada de l'àrea de contingut)
+  30px (padding esquerre + padding dret: 15px + 15px)
+  10px (contorn esquerre + contorn dret: 5px + 5px)
= 240px (amplada total)
```

**Càlcul de l'altura:**
```plaintext
  100px (altura de l'àrea de contingut)
+  30px (padding superior + padding inferior: 15px + 15px)
+  10px (contorn superior + contorn inferior: 5px + 5px)
= 140px (altura total)
```

---

### Exercici 2
Aquest `<div>` tindrà una amplada total de 400px i una altura total de 120px:

```css
div {
  width: 350px;
  height: 80px;
  padding: 30px;
  border: 5px solid blue;
  margin: 20px;
}
```

**Càlcul de l'amplada:**
```plaintext
  350px (amplada de l'àrea de contingut)
+  60px (padding esquerre + padding dret: 30px + 30px)
+  10px (border esquerre + border dret: 5px + 5px)
+  40px (margin esquerre + padding dret: 20px + 20px)
= 460px (amplada total)
```

**Càlcul de l'altura:**
```plaintext
   80px (altura de l'àrea de contingut)
+  60px (padding superior + padding inferior: 30px + 30px)
+  10px (contorn superior + contorn inferior: 5px + 5px)
+  40px (margin superior + margin inferior: 20px + 20px)
= 120px (altura total)
```

---

### Exercici 3
Aquest `<div>` tindrà una amplada total de 500px i una altura total de 250px:

```css
div {
  width: 450px;
  height: 200px;
  padding: 30px;
  border: 0;
  margin: 25;
}
```

**Càlcul de l'amplada:**
  Completa tu mateix, t'ha de sortir 500px (amplada total)

**Càlcul de l'altura:**
  Completa tu mateix, t'ha de sortir 250px (altura total)


---

## El Model de Caixa en `<span>` i `<div>`

Els elements HTML, com `<span>` i `<div>`, tenen comportaments diferents respecte al model de caixa basats en el seu tipus de visualització: **inline** (línia) o **block** (bloc).

---

### 1. `<div>`: Element de Bloc
- **Comportament**: `<div>` és un element de bloc, el que significa que ocupa tota l'amplada disponible i es col·loca en una nova línia, separant-se dels elements anteriors i posteriors.
- **Model de Caixa**: 
  - Com a element de bloc, les propietats `width`, `height`, `margin`, `padding`, i `border` s'apliquen completament.
  - Pots definir l'amplada (`width`) i l'altura (`height`) d'un `<div>`, i aquestes propietats afecten la mida total de la seva caixa.
  - Els marges i farcits (`margin` i `padding`) separen l'element de bloc d'altres elements i es veuen clarament reflectits en el model de caixa.

**Exemple d'ús de `<div>`:**

```html
<div style="width: 200px; height: 100px; padding: 20px; border: 1px solid black; margin: 10px;">
    Aquest és un element de bloc.
</div>
```

- **Explicació**: En aquest exemple, el `<div>` tindrà un model de caixa amb totes les propietats aplicades, incloent-hi el farcit (padding), el contorn (border), i els marges (margin).

---

### 2. `<span>`: Element de Línia
- **Comportament**: `<span>` és un element de línia, el que significa que només ocupa l'espai necessari per al seu contingut i no provoca un salt de línia abans ni després.
- **Model de Caixa**:
  - Com a element de línia, les propietats `width` i `height` no tenen efecte.
  - Les propietats `margin` i `padding` s'apliquen parcialment:
    - **`padding`**: Només s'aplica lateralment (esquerra i dreta) i no afecta l'alçada de l'element.
    - **`margin`**: Només funciona lateralment i no provocarà espai per sobre o per sota de l'element de línia.
  - El contorn (`border`) es pot aplicar, però segueix l'alçada natural del contingut.

**Exemple d'ús de `<span>`:**
```html
<span style="padding: 5px; border: 1px solid red; margin: 10px;">
    Aquest és un element de línia.
</span>
```

- **Explicació**: En aquest exemple, el `<span>` tindrà un farcit (padding) i un contorn (border) aplicats, però no ocuparà tota l'amplada disponible i no es desplaçarà a una nova línia.

---

### Resum
- **`<div>`**: És un element de bloc que utilitza completament el model de caixa, permetent el control complet de les seves dimensions, marges, farcits, i contorns.
- **`<span>`**: És un element de línia que no permet definir l'amplada o l'altura, i només aplica marges i farcits lateralment, afectant únicament el seu contingut immediat.

## Què és `display: block`, `display: inline` i `display: inline-block`?

### 1. `display: block`
- **Descripció**: Els elements amb `display: block` són elements de bloc que ocupen tota l'amplada disponible i comencen en una nova línia. Això vol dir que es desplacen cap avall, separant-se dels elements anteriors i posteriors.
- **Propietats**: Pots definir `width`, `height`, `margin`, i `padding`, i aquestes afectaran completament la mida i l'espai ocupat per l'element.
- **Exemples**: Elements com `<div>`, `<h1>`, `<p>`, i `<section>` són elements de bloc per defecte.
- **Ús Comú**: Es fa servir per estructurar grans seccions de la pàgina, com contenidors, paràgrafs o capçaleres, on es necessita control complet sobre l'espai ocupat.

---

### 2. `display: inline`
- **Descripció**: Els elements amb `display: inline` són elements en línia que només ocupen l'espai necessari per al seu contingut i no comencen en una nova línia. Aquests elements es col·loquen al costat d'altres elements en línia.
- **Propietats**: No pots definir `width` o `height`, i les propietats `margin` i `padding` només s'apliquen lateralment (esquerra i dreta).
- **Exemples**: Elements com `<span>`, `<a>`, `<strong>`, i `<em>` són elements en línia per defecte.
- **Ús Comú**: Es fan servir per donar estil a parts petites de text o per a elements que han de col·locar-se dins d'una línia de text, com enllaços o paraules ressaltades.

---

### 3. `display: inline-block`
- **Descripció**: Els elements amb `display: inline-block` combinen característiques de bloc i en línia. Es comporten com elements de bloc perquè permeten definir `width`, `height`, `margin`, i `padding` completament, però es col·loquen al costat d'altres elements en línia, sense començar en una nova línia.
- **Propietats**: Pots controlar la mida de l'element i, al mateix temps, mantenir la capacitat de col·locar-los horitzontalment amb altres elements.
- **Exemples**: Elements que vols alinear horitzontalment però amb mida personalitzada, com botons o imatges amb text.
- **Ús Comú**: Es fa servir per crear dissenys més complexos on es necessita la flexibilitat d'un element de bloc però sense interrompre el flux horitzontal, com en la creació de galeries, targetes de producte o menús de navegació.




---

## Propietat `outline` en CSS

L'`outline` és una línia que envolta l'element, similar a la propietat `border`, però amb algunes diferències importants. No afecta l'espai ocupat per l'element i no modifica el flux de la pàgina.

### Característiques principals de `outline`:
1. **No ocupa espai**: A diferència del `border`, l'`outline` no afegeix espai a l'element ni mou altres elements al voltant.
2. **Visibilitat**: S'utilitza sovint per millorar l'accessibilitat i la usabilitat, ja que proporciona una clara indicació visual quan un element està enfocat (per exemple, amb la tecla "Tab").

---

### Propietats relacionades amb `outline`:

1. **`outline-width`**
   - Defineix l'ample de la línia del contorn.
   - **Exemples**:
     - outline-width: 2px;
     - outline-width: thick;

2. **`outline-style`**
   - Defineix l'estil de la línia del contorn (similar a la propietat `border-style`).
   - **Exemples**:
     - outline-style: solid; (línia contínua)
     - outline-style: dashed; (línia discontínua)
     - outline-style: none; (sense contorn)

3. **`outline-color`**
   - Defineix el color de la línia del contorn.
   - **Exemples**:
     - outline-color: red;
     - outline-color: #00ff00;

4. **`outline` (propietat abreujada)**
   - Pots definir totes les propietats de l'outline en una sola línia.
   - **Exemple**:
     - outline: 2px solid blue;

---

### Aplicació de l'`outline` en CSS


L'`outline` és especialment útil per ressaltar elements en estats d'enfocament o per destacar errors en formularis sense alterar el disseny de la pàgina.



## Annex: Com construir un sombrejat tipus Material Design amb CSS

Els efectes de sombrejat que es fan servir en Material Design són subtils i realistes, utilitzant ombres per crear una sensació de profunditat. Això es pot aconseguir amb la propietat `box-shadow` en CSS.

### Sintaxi de `box-shadow`
La propietat `box-shadow` permet afegir una o més ombres a un element. La sintaxi bàsica és la següent:
- **Sintaxi**: box-shadow: offset-x offset-y blur-radius spread-radius color;
  - **offset-x**: Desplaçament horitzontal de l'ombra.
  - **offset-y**: Desplaçament vertical de l'ombra.
  - **blur-radius**: Difusió de l'ombra (com més gran, més difusa).
  - **spread-radius**: Extensió de l'ombra (pot ser positiva o negativa).
  - **color**: Color de l'ombra.

---

## Explicació de la Propietat `box-shadow` en CSS

La propietat `box-shadow` permet afegir ombres a un element, creant efectes visuals que donen una sensació de profunditat. Pots utilitzar `box-shadow` per afegir ombres simples o múltiples, amb una gran flexibilitat en la seva configuració.

### Sintaxi de `box-shadow`
La sintaxi general de `box-shadow` és:

box-shadow: offset-x offset-y blur-radius spread-radius color;

- **offset-x**: Desplaçament horitzontal de l'ombra.
  - Un valor positiu mou l'ombra cap a la dreta.
  - Un valor negatiu mou l'ombra cap a l'esquerra.

- **offset-y**: Desplaçament vertical de l'ombra.
  - Un valor positiu mou l'ombra cap avall.
  - Un valor negatiu mou l'ombra cap amunt.

- **blur-radius** (opcional): El radi de desenfocament de l'ombra.
  - Com més gran sigui aquest valor, més difusa serà l'ombra.
  - Si no es defineix, el valor per defecte és 0 (ombra sense desenfocament).

- **spread-radius** (opcional): L'extensió de l'ombra.
  - Un valor positiu expandeix l'ombra.
  - Un valor negatiu redueix l'ombra.
  - Si no es defineix, el valor per defecte és 0.

- **color**: El color de l'ombra.
  - Pots utilitzar colors en format `rgba` per afegir transparència.

### Exemple bàsic
```css
div {
  box-shadow: 10px 10px 5px rgba(0, 0, 0, 0.5);
}
```

- **Explicació**:
  - **10px**: L'ombra es desplaça 10 píxels cap a la dreta.
  - **10px**: L'ombra es desplaça 10 píxels cap avall.
  - **5px**: L'ombra té un desenfocament de 5 píxels.
  - **rgba(0, 0, 0, 0.5)**: L'ombra és negra amb una opacitat del 50%.

---

### Exemple d'ombra sense desenfocament
```css
div {
  box-shadow: 5px 5px 0px black;
}
```

- En aquest exemple, l'ombra és negra i té un desplaçament de 5 píxels cap a la dreta i cap avall, sense desenfocament (blur-radius de 0).

---

### Exemple d'ombra amb extensió
```css
div {
  box-shadow: 0 0 10px 5px blue;
}
```

- **0**: No hi ha desplaçament horitzontal o vertical.
- **10px**: L'ombra té un desenfocament de 10 píxels.
- **5px**: L'ombra s'expandeix 5 píxels més enllà del contingut.
- **blue**: L'ombra és de color blau.

---

### Exemple d'ombres múltiples
Pots afegir diverses ombres separades per comes per crear un efecte més complex:

```css
div {
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3), -5px -5px 5px rgba(255, 255, 255, 0.5);
}
```

- **5px 5px 10px rgba(0, 0, 0, 0.3)**: Ombra fosca amb desenfocament cap a la dreta i cap avall.
- **-5px -5px 5px rgba(255, 255, 255, 0.5)**: Ombra clara amb desenfocament cap a l'esquerra i cap amunt.

### Notes
- La propietat `box-shadow` no afecta el flux de la pàgina, és a dir, no desplaça ni modifica l'espai ocupat per altres elements.
- Les ombres poden ser utilitzades per crear efectes de profunditat i destacar elements importants en la interfície.

---

Aquesta propietat ofereix una gran versatilitat per crear estils visuals atractius amb ombres a elements HTML!



### Exemples de sombrejat tipus Material Design

#### Exemple 1: Sombrejat suau
Aquest exemple crea un efecte d'ombra suau similar a un objecte flotant lleugerament per sobre d'una superfície.

```css
div {
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1), 0 2px 4px rgba(0, 0, 0, 0.1);
}
```

- **Explicació**:
  - La primera ombra (0 4px 8px rgba(0, 0, 0, 0.1)) crea una ombra difusa més gran.
  - La segona ombra (0 2px 4px rgba(0, 0, 0, 0.1)) crea una ombra més petita i propera a l'element.

---

#### Exemple 2: Sombrejat més intens
Aquest exemple crea un efecte d'ombra més profund, ideal per a elements destacats.

```css
div {
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2), 0 3px 6px rgba(0, 0, 0, 0.15);
}
```

- **Explicació**:
  - La primera ombra (0 6px 12px rgba(0, 0, 0, 0.2)) proporciona una ombra més gran amb més difusió.
  - La segona ombra (0 3px 6px rgba(0, 0, 0, 0.15)) afegeix una ombra secundària més propera i subtil.

---

### Efecte de múltiples capes d'ombres

Per a un efecte de profunditat més complex, es poden utilitzar diverses capes d'ombres:

```css
div {
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 
              0 1px 2px rgba(0, 0, 0, 0.24), 
              0 4px 6px rgba(0, 0, 0, 0.1);
}
```

- **Explicació**:
  - S'afegeixen tres capes d'ombres amb diferents intensitats i radi de difusió per donar més profunditat.

---

### Consells per a sombrejats tipus Material Design
1. Utilitza ombres suaus i difuses per a un aspecte elegant i lleuger.
2. Juga amb la transparència (rgba) per aconseguir un efecte més subtil.
3. Per a elements més destacats o elevats, incrementa el `offset-y` i el `blur-radius`.

Aquest enfocament crearà una sensació de profunditat visual, d'acord amb l'estil Material Design!
