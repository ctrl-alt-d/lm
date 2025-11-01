## Sessió 5: Introducció a CSS

### Objectius
- Entendre què és CSS i la seva relació amb HTML.
- Aplicar estils bàsics a un document HTML.

### Continguts

#### Definició de CSS
CSS (Cascading Style Sheets) és el llenguatge utilitzat per definir l'aparença visual dels elements d'una pàgina HTML. Permet controlar aspectes com els colors, mides, tipus de lletra, marges, etc., i està dissenyat per separar la presentació del contingut.

#### Selecció d'elements
A CSS es poden seleccionar elements HTML de diferents maneres:
- **Per etiquetes** (p, h1, div): Aplica l'estil a tots els elements d'aquest tipus.
- **Per classes** (.nom-classe): S'utilitza per estilitzar múltiples elements amb la mateixa classe.
- **Per ID** (#nom-id): Aplica l'estil a un sol element que tingui aquest ID específic.

#### Sintaxi bàsica de CSS
Un conjunt de regles CSS segueix aquesta estructura:

```css
selector {
  propietat: valor;
}
```

Per exemple:

```css
p {
  color: blue;
  font-size: 16px;
}
```

#### Maneres d'inserir CSS

- **Estils en línia**: Afegits directament a l'element HTML mitjançant l'atribut style. Exemple:

```html
<p style="color: red;">Això és un paràgraf en vermell.</p>
```

- **Estils en capçalera**: Definits dins l'etiqueta <style> dins del document HTML. Exemple:

```html
<head>
  <style>
    p { color: green; }
  </style>
</head>
```

- **Arxius externs**: Es creen en un fitxer .css separat i s'inclou al document HTML amb l'etiqueta <link>. Exemple:

```html
<head>
  <link rel="stylesheet" href="estils.css">
</head>
```

### Selecció d'elements i lligam amb CSS

#### Selecció per nom d'element
Els selectors per nom d'element s'utilitzen per aplicar estils a tots els elements HTML d'un mateix tipus. Per exemple, si vols aplicar un estil a tots els paràgrafs d'una pàgina, utilitzes el nom de l'element p:

```css
p {
  color: blue;
  font-size: 16px;
}
```

En aquest cas, tots els elements p del document tindran el text de color blau i una mida de lletra de 16px.

#### Selecció per classe
Les classes permeten aplicar estils a múltiples elements que comparteixin la mateixa classe, independentment del seu tipus d'etiqueta. A CSS, les classes es defineixen amb un punt (.) abans del nom de la classe.

```css
.nom-classe {
  background-color: yellow;
  padding: 10px;
}
```

Els elements HTML que utilitzin aquesta classe tindran un fons de color groc i un farcit intern (padding) de 10px. Exemple d'ús en HTML:

```html
<div class="nom-classe">Aquest div utilitza la classe</div>
<p class="nom-classe">Aquest paràgraf també utilitza la classe</p>
```

#### Selecció per ID
Els IDs s'utilitzen per aplicar estils a un sol element específic, ja que els IDs són únics dins d'un document HTML. En CSS, els IDs es defineixen amb un coixinet (#) abans del nom de l'ID.

```css
#nom-id {
  color: red;
  font-weight: bold;
}
```

Això només s'aplicarà a l'element que tingui aquest ID. Exemple d'ús en HTML:

```html
<p id="nom-id">Aquest paràgraf tindrà el text en vermell i negreta.</p>
```


### Herència d'estils en CSS

#### Com funciona l'herència?

Quan un element HTML té elements fills dins seu, aquests poden heretar algunes propietats CSS definides per l'element pare. L'herència permet que els estils definits per un element superior es propaguin als seus descendents, estalviant la necessitat d'aplicar els estils repetidament. 

#### Exemples de propietats heretades

Algunes propietats CSS s'hereten automàticament. Exemples comuns inclouen:

- **color**: El color del text es transmet als elements fills.
- **font-family**: La tipografia utilitzada pels elements pares s'aplica als elements fills.
- **font-size**: La mida del text es propaga als elements dins del pare.
- **line-height**: L'alçada de la línia també es transmet als elements fills.

Exemple:

```css
body {
  color: blue;
  font-family: Arial, sans-serif;
}
```

Tots els paràgrafs, encapçalaments i altres elements dins del body mostraran el text en color blau i amb la font Arial, a menys que s'hi defineixin altres estils específics.

#### Propietats no heretades

Algunes propietats no s'hereten automàticament perquè el seu comportament heretat no tindria sentit. Exemples de propietats que no s'hereten:

- **margin**: Els marges no es transmeten als elements fills.
- **padding**: El farcit (padding) no s'hereta.
- **border**: Les propietats relacionades amb les vores tampoc s'hereten.

Aquestes propietats s'han d'aplicar específicament a cada element si es vol que tinguin efecte sobre els elements fills.

#### Controlar l'herència amb `inherit`

Pots forçar que un element fill hereti una propietat que no s'heretaria per defecte utilitzant el valor `inherit`. Això obliga l'element fill a heretar la propietat del seu pare.

Exemple:

```css
div {
  background-color: red;
}

p {
  background-color: inherit;
}
```

En aquest cas, el paràgraf heretarà el color de fons vermell del seu element pare (div).

#### Conclusió

L'herència en CSS és una característica útil que permet aplicar estils de manera eficient, reduint la repetició de codi. No totes les propietats s'hereten automàticament, però amb el valor `inherit` es pot forçar l'herència quan sigui necessari.
