# Pràctica: El botó que no es deixa punxar

## Objectiu
Crear un botó que es mogui d'esquerra a dreta quan hi passem el ratolí per sobre.

---

## Pas 1: Crear l'HTML bàsic

Crea un fitxer `boto-juganer.html` amb aquesta estructura:

```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <meta charset="UTF-8">
    <title>Botó juganer</title>
</head>
<body>
    <h1>Intenta punxar el botó!</h1>
    <div id="contenidor">
        <button id="boto">Punxa'm!</button>
    </div>
</body>
</html>
```

---

## Pas 2: Afegir CSS

Afegeix estils dins del `<head>`, abans de tancar-lo:

```html
<style>
    #contenidor {
        width: 300px;
        height: 50px;
        border: 2px solid black;
        position: relative;
    }

    #boto {
        position: absolute;
        left: 20px;
    }
</style>
```

**Prova-ho:** El botó hauria d'aparèixer a l'esquerra del contenidor.

---

## Pas 3: Afegir JavaScript

Afegeix just abans de `</body>`:

```html
<script>
    const boto = document.getElementById('boto');

    boto.addEventListener('mouseenter', function() {
        boto.style.left = 'unset';
        boto.style.right = '20px';
    });
</script>
```

**Prova-ho:** Quan passis el ratolí pel botó, aquest saltarà a la dreta!

---

## Pas 4: Fer que torni a l'esquerra

Modifica el JavaScript perquè el botó vagi alternant:

```html
<script>
    const boto = document.getElementById('boto');
    let aEsquerra = true;

    boto.addEventListener('mouseenter', function() {
        if (aEsquerra) {
            boto.style.left = 'unset';
            boto.style.right = '20px';
        } else {
            boto.style.right = 'unset';
            boto.style.left = '20px';
        }
        aEsquerra = !aEsquerra;
    });
</script>
```

---

## Codi final complet

```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <meta charset="UTF-8">
    <title>Botó juganer</title>
    <style>
        #contenidor {
            width: 300px;
            height: 50px;
            border: 2px solid black;
            position: relative;
        }

        #boto {
            position: absolute;
            left: 20px;
        }
    </style>
</head>
<body>
    <h1>Intenta punxar el botó!</h1>
    <div id="contenidor">
        <button id="boto">Punxa'm!</button>
    </div>

    <script>
        const boto = document.getElementById('boto');
        let aEsquerra = true;

        boto.addEventListener('mouseenter', function() {
            if (aEsquerra) {
                boto.style.left = 'unset';
                boto.style.right = '20px';
            } else {
                boto.style.right = 'unset';
                boto.style.left = '20px';
            }
            aEsquerra = !aEsquerra;
        });
    </script>
</body>
</html>
```

---

## Conceptes apresos

- `position: relative` i `position: absolute`
- Propietats CSS `left` i `right`
- Event `mouseenter` de JavaScript
- Variables booleanes per alternar estats
