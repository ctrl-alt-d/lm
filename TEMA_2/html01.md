# Sessió 1: Introducció a HTML

**Objectius:**
1. Entendre què és HTML i la seva funció en el desenvolupament web.
2. Aprendre l'estructura bàsica d'un document HTML.
3. Introduir les etiquetes més comunes com `<h1>`, `<p>`,`<span>` i `<a>`.

---

## 1. Introducció a HTML
- **Què és HTML?**
  - HTML (HyperText Markup Language) és un llenguatge de marques utilitzat per crear pàgines web.
  - Serveix per estructurar i organitzar el contingut de la pàgina web.
  - No és un llenguatge de programació, és un llenguatge descriptiu.
  
- **Història breu d'HTML**
  - Desenvolupat per Tim Berners-Lee el 1991.
  - Ha evolucionat amb diferents versions, fins a l'actual HTML5.

**Exemple:**

```html
<!DOCTYPE html>  
<html>  
  <head>  
    <title>La meva primera pàgina HTML</title>  
  </head>  
  <body>  
    <h1>Benvinguts a la meva pàgina web!</h1>  
    <p>Això és un paràgraf.</p>  
  </body>  
</html>
```

---

## 2. Estructura bàsica d'un document HTML (30 min)
- **Etiquetes principals**
  - `<html>`: Conté tot el contingut d'un document HTML.
  - `<head>`: Inclou metadades, com el títol i enllaços a arxius CSS o scripts.
  - `<body>`: Conté el contingut visible de la pàgina web.
  
**Exemple:**

```html
<!DOCTYPE html>  
<html>  
  <head>  
    <title>Títol de la pàgina</title>  
  </head>  
  <body>  
    <!-- Contingut aquí -->  
  </body>  
</html>
```

---

## 3. Etiquetes bàsiques
- **Etiquetes per a encapçalaments:**
  - `<h1> a <h6>`: Utilitzades per definir títols de diferent nivell.
  - **Exemple:**

```html
    <h1>Títol principal</h1>  
    <h2>Subtítol</h2>
```

- **Etiquetes per a paràgrafs:**
  - `<p>`: Defineix un paràgraf de text.
  - **Exemple:**

    <p>Aquest és un paràgraf de text.</p>

- **Etiquetes per a enllaços:**
  - `<a>`: Crea enllaços a altres pàgines o recursos.
  - Atribut important: `href`, que defineix la URL de l'enllaç.
  - **Exemple:**

```html
    <a href="https://www.example.com">Visita example.com</a>
```

## 4. Etiqueta `<span>`

La etiqueta `<span>` en HTML és un element en línia (inline) que s'utilitza per agrupar o marcar una part del contingut dins d'un bloc de text sense afectar-ne el flux o la disposició a la pàgina. A diferència d'elements de bloc com `<div>`, que ocupen tot l'ample disponible i comencen en una nova línia, el `<span>` no altera el flux del contingut circumdant i es comporta com qualsevol altre element de text en línia, com ara `<a>` o `<strong>`.

L'objectiu principal de `<span>` és permetre aplicar estils o manipular un fragment de text mitjançant CSS o JavaScript sense canviar-ne el comportament de presentació. És especialment útil per marcar parts específiques d'un text quan només necessites aplicar-hi estils locals o accedir-hi des de JavaScript sense que afecti el format general de la pàgina.

Un exemple bàsic seria:

```html
<p>Això és un <span class="blau">text en blau</span> dins d'una frase.</p>
```

__Nota: com que encara no hem estudiat css no veuràs el text de color blau si proves aquest exemple.__

---

## 5. Entorn de desenvolupament
- **Editors de text**
  - **Recomanats:** **Visual Studio Code**, Sublime Text, Atom.
  - **Altres:** Notepad++, Brackets, Vim.
- **Navegadors**
  - **Recomanats:** Google Chrome, Mozilla Firefox, Microsoft Edge.
  - **Altres:** Safari, Opera.
- **Extensions útils:** **Live Server**, Web Developer, ColorZilla.

## 6. Activitat pràctica
- Crear una pàgina HTML senzilla que inclogui:
  - Un títol principal (`<h1>`)
  - Un subtítol (`<h2>`)
  - Dos paràgrafs (`<p>`)
  - Un enllaç (`<a>`)

---

## 7. Recapitulació i dubtes
- Revisió dels conceptes apresos.
- Espai per a preguntes i aclariments.

---

## 8. Bibliografia

- https://www.w3schools.com/html/
- https://www.w3schools.com/html/html_intro.asp
- https://developer.mozilla.org/en-US/docs/Web/HTML/Element

## 9. Humor

- https://www.reddit.com/r/ProgrammerHumor/comments/28wqvi/tim_bernerslee_web_developer/

![Tim Berners Lee amb el títol 'web developer'](https://pbs.twimg.com/media/Bp2GVC2CQAAH4uN.jpg)