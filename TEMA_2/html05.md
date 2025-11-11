# Sessió 5: Organització d'una pàgina HTML

## Objectius
- Aprendre a utilitzar etiquetes HTML semàntiques per estructurar una pàgina web de manera correcta.
- Entendre el propòsit de cada element estructural (`<header>`, `<footer>`, `<nav>`, `<section>`, `<article>`, `<aside>`).
- Crear pàgines web ben organitzades i accessibles utilitzant elements semàntics.

---

## 1. Introducció als Elements Semàntics d'HTML5

Els elements semàntics HTML5 permeten estructurar la pàgina de manera que tant els navegadors com els motors de cerca entenguin millor el contingut. A més, milloren l'accessibilitat per a usuaris amb lectors de pantalla.

Els elements que veurem en aquesta sessió són:
- `<header>`: Encapçalament de la pàgina o secció
- `<footer>`: Peu de pàgina o secció
- `<nav>`: Navegació principal
- `<section>`: Secció genèrica de contingut
- `<article>`: Contingut independent (entrada de blog, notícia, etc.)
- `<aside>`: Contingut relacionat però secundari (barra lateral)

---

## 2. L'Element `<header>`

### Descripció
L'element `<header>` representa un contenidor d'introducció o navegació. Normalment conté:
- El logotip del lloc web
- El títol principal de la pàgina
- La navegació principal
- Elements de recerca o formularis de login

### Característiques
- **Semàntica**: Indica que el contingut és d'introducció o navegació.
- **Ubicació**: Generalment a la part superior de la pàgina o secció.
- **Ús múltiple**: Pots tenir múltiples `<header>` elements en la mateixa pàgina (un per secció).

### Exemple
```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <meta charset="UTF-8">
    <title>Mi lloc web</title>
</head>
<body>
    <header>
        <h1>Benvinguts al meu lloc web</h1>
        <p>Aquí trobareu informació sobre els meus projectes</p>
    </header>
    
    <main>
        <p>Contingut principal...</p>
    </main>
</body>
</html>
```

### Ús Pràctic
```html
<header>
    <img src="logo.png" alt="Logo del lloc">
    <h1>El meu lloc web</h1>
    <nav>
        <ul>
            <li><a href="#inici">Inici</a></li>
            <li><a href="#sobre">Sobre</a></li>
            <li><a href="#contacte">Contacte</a></li>
        </ul>
    </nav>
</header>
```

---

## 3. L'Element `<footer>`

### Descripció
L'element `<footer>` representa el peu de pàgina o d'una secció. Normalment conté:
- Informació de copyright
- Informació de contacte
- Enllaços a xarxes socials
- Mapa del lloc
- Informació legal

### Característiques
- **Semàntica**: Indica que el contingut és informació final o secundària.
- **Ubicació**: Generalment a la part inferior de la pàgina o secció.
- **Ús múltiple**: Pots tenir múltiples `<footer>` elements (un per secció).

### Exemple
```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <meta charset="UTF-8">
    <title>Mi lloc web</title>
</head>
<body>
    <header>
        <h1>Mi lloc web</h1>
    </header>
    
    <main>
        <p>Contingut principal...</p>
    </main>
    
    <footer>
        <p>&copy; 2024 Mi lloc web. Tots els drets reservats.</p>
        <p>Contacte: info@miposit.com</p>
    </footer>
</body>
</html>
```

### Ús Pràctic
```html
<footer>
    <div class="footer-content">
        <h3>Informació de Contacte</h3>
        <p>Email: contacte@exemple.com</p>
        <p>Telèfon: +34 123 456 789</p>
    </div>
    
    <div class="footer-links">
        <h3>Enllaços Ràpids</h3>
        <ul>
            <li><a href="#privacitat">Política de Privacitat</a></li>
            <li><a href="#termini">Termes de Servei</a></li>
        </ul>
    </div>
    
    <div class="footer-social">
        <h3>Segueix-nos</h3>
        <a href="#">Facebook</a>
        <a href="#">Twitter</a>
        <a href="#">Instagram</a>
    </div>
</footer>
```

---

## 4. L'Element `<nav>`

### Descripció
L'element `<nav>` representa una secció amb enllaços de navegació. S'utilitza per als menús principals, breadcrumbs (migas de pà) o índexs de taula de continguts.

### Característiques
- **Semàntica**: Indica que el contingut conté enllaços de navegació.
- **Ubicació**: Generalment dins del `<header>` o com a secció independent.
- **Ús múltiple**: Pots tenir múltiples `<nav>` elements (navegació principal, secundaria, breadcrumbs, etc.).

### Exemple Bàsic
```html
<nav>
    <ul>
        <li><a href="#inici">Inici</a></li>
        <li><a href="#productes">Productes</a></li>
        <li><a href="#sobre">Sobre Nosaltres</a></li>
        <li><a href="#contacte">Contacte</a></li>
    </ul>
</nav>
```

### Ús Pràctic: Navegació en Header
```html
<header>
    <h1>Botiga Online</h1>
    <nav>
        <ul>
            <li><a href="/">Inici</a></li>
            <li><a href="/cataleg">Catàleg</a></li>
            <li><a href="/ofertes">Ofertes</a></li>
            <li><a href="/carrito">Carrito</a></li>
        </ul>
    </nav>
</header>
```

### Ús Pràctic: Breadcrumbs
```html
<nav aria-label="Breadcrumb">
    <ol>
        <li><a href="/">Inici</a></li>
        <li><a href="/productes">Productes</a></li>
        <li aria-current="page">Telèfons Mòbils</li>
    </ol>
</nav>
```

---

## 5. L'Element `<section>`

### Descripció
L'element `<section>` representa una secció temàtica genèrica de contingut. S'utilitza per agrupar contingut relacionat amb un tema.

### Característiques
- **Semàntica**: Agrupa contingut relacionat temàticament.
- **Ús**: Normalment amb un títol (`<h1>`, `<h2>`, etc.).
- **Múltiples seccions**: Una pàgina pot tenir vàries `<section>` elements.
- **No és genèric**: Usa `<div>` si no hi ha relació temàtica clara.

### Quan Utilitzar `<section>`
- Agrupar capítols d'un llibre
- Agrupar apartats temàtics (Introducció, Historia, Característiques)
- Agrupar productes per categoria
- Separar seccions d'una pàgina web

### Exemple
```html
<section>
    <h2>Característiques Principals</h2>
    <p>Aquesta secció descriu les característiques del producte.</p>
    <ul>
        <li>Característica 1</li>
        <li>Característica 2</li>
        <li>Característica 3</li>
    </ul>
</section>

<section>
    <h2>Preus</h2>
    <p>Els nostres plans de preus:</p>
    <ul>
        <li>Pla Bàsic: 10€/mes</li>
        <li>Pla Professional: 25€/mes</li>
        <li>Pla Empresarial: 50€/mes</li>
    </ul>
</section>
```

### Ús Pràctic: Estructura de Pàgina
```html
<body>
    <header>
        <h1>Meu Portal</h1>
        <nav>...</nav>
    </header>
    
    <section>
        <h2>Benvinguda</h2>
        <p>Aquesta és la secció de benvinguda...</p>
    </section>
    
    <section>
        <h2>Últimes Notícies</h2>
        <article>...</article>
        <article>...</article>
    </section>
    
    <footer>...</footer>
</body>
```

---

## 6. L'Element `<article>`

### Descripció
L'element `<article>` representa contingut independent que pot funcionar autònomament. Exemples: entrada de blog, notícia, comentari, review de producte, etc.

### Característiques
- **Semàntica**: Representa contingut reutilitzable i independent.
- **Reutilització**: El contingut dins `<article>` hauria de tenir sentit per si sol.
- **Múltiples usos**: Pots tenir varis `<article>` elements en la mateixa pàgina.
- **Anidació**: Pots anidar `<article>` elements (per exemple, comentaris dins una entrada).

### Quan Utilitzar `<article>`
- Entrades de blog
- Notícies
- Comentaris de usuaris
- Reviews de productes
- Publicacions en xarxes socials

### Exemple: Entrada de Blog
```html
<article>
    <header>
        <h2>Com Aprendre HTML</h2>
        <p>Publicat per: Joan Martí | Data: 15 de novembre de 2024</p>
    </header>
    
    <section>
        <p>HTML és el llenguatge de marcatge hipertextual...</p>
        <p>Aquesta és la introducció de l'article...</p>
    </section>
    
    <section>
        <h3>Passos per Aprendre HTML</h3>
        <ol>
            <li>Entendre les etiquetes bàsiques</li>
            <li>Practicar la estructura dels documents</li>
            <li>Crear projectes simples</li>
        </ol>
    </section>
    
    <footer>
        <p>Paraules clau: html, programació, web</p>
    </footer>
</article>
```

### Ús Pràctic: Llista de Notícies
```html
<section>
    <h2>Últimes Notícies</h2>
    
    <article>
        <h3>Noticia 1: Nova Actualització de Navegador</h3>
        <p>Data: 20 de novembre</p>
        <p>Contingut de la noticia...</p>
        <a href="#">Llegir més</a>
    </article>
    
    <article>
        <h3>Noticia 2: HTML5 Evoluciona</h3>
        <p>Data: 19 de novembre</p>
        <p>Contingut de la noticia...</p>
        <a href="#">Llegir més</a>
    </article>
</section>
```

---

## 7. L'Element `<aside>`

### Descripció
L'element `<aside>` representa contingut relacionat però secundari. Típicament utilitzat per a barres laterals, barres de cita (sidebars), o anuncis.

### Característiques
- **Semàntica**: Indica contingut secundari o relacionat.
- **Ubicació**: Generalment a un costat del contingut principal.
- **Independència**: El contingut principal hauria de funcionar sense l'`<aside>`.
- **No és decoratiu**: Usa `<div>` si el contingut no té relació temàtica.

### Quan Utilitzar `<aside>`
- Barra lateral amb widgets
- Enllaços relacionats
- Glossari de termes
- Publicitat contextual
- Autor de l'article
- Informació suplementària

### Exemple: Barra Lateral
```html
<main>
    <article>
        <h2>Introducció a CSS</h2>
        <p>CSS és el llenguatge per estilitzar pàgines web...</p>
        <p>Més contingut de l'article...</p>
    </article>
    
    <aside>
        <h3>Informació de l'Autor</h3>
        <img src="autor.jpg" alt="Foto de l'autor">
        <p>Joan Martí és un desenvolupador web amb 10 anys d'experiència.</p>
        
        <h3>Articles Relacionats</h3>
        <ul>
            <li><a href="#">HTML per Principiants</a></li>
            <li><a href="#">CSS Avançat</a></li>
            <li><a href="#">JavaScript Bàsic</a></li>
        </ul>
        
        <h3>Subscriu-te</h3>
        <form>
            <input type="email" placeholder="El teu email">
            <button type="submit">Subscriure</button>
        </form>
    </aside>
</main>
```

### Ús Pràctic: Layout amb Sidebar
```html
<body>
    <header>
        <h1>Mi Blog</h1>
        <nav>...</nav>
    </header>
    
    <main>
        <article>
            <h2>Entrada Principal</h2>
            <p>Contingut de l'article...</p>
        </article>
        
        <aside>
            <h3>Categoríes</h3>
            <ul>
                <li><a href="#">HTML</a></li>
                <li><a href="#">CSS</a></li>
                <li><a href="#">JavaScript</a></li>
            </ul>
        </aside>
    </main>
    
    <footer>...</footer>
</body>
```

---

## 8. Estructura Completa d'una Pàgina Web

### Exemple: Portal de Bloc
```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Blog de Desenvolupament Web</title>
</head>
<body>
    <!-- Encapçalament de la pàgina -->
    <header>
        <img src="logo.png" alt="Logo del bloc">
        <h1>Mi Blog de Desenvolupament Web</h1>
        <p>Aprén HTML, CSS i JavaScript</p>
    </header>
    
    <!-- Navegació principal -->
    <nav>
        <ul>
            <li><a href="#inici">Inici</a></li>
            <li><a href="#articles">Articles</a></li>
            <li><a href="#tutorials">Tutorials</a></li>
            <li><a href="#contacte">Contacte</a></li>
        </ul>
    </nav>
    
    <!-- Contingut principal -->
    <main>
        <!-- Secció: Entrades del blog -->
        <section>
            <h2>Últimes Entrades</h2>
            
            <!-- Article 1 -->
            <article>
                <header>
                    <h3>Com Aprendre HTML Correctament</h3>
                    <p>Publicat per: Joan Martí | Data: 15 de novembre de 2024</p>
                </header>
                <p>HTML és la base de tota pàgina web. En aquest article et mostré com aprendre-ho...</p>
                <a href="#">Llegir més</a>
            </article>
            
            <!-- Article 2 -->
            <article>
                <header>
                    <h3>CSS Grid vs Flexbox</h3>
                    <p>Publicat per: Maria López | Data: 14 de novembre de 2024</p>
                </header>
                <p>Quan hauries d'utilitzar CSS Grid i quan Flexbox? En aquest article ho explorem...</p>
                <a href="#">Llegir més</a>
            </article>
        </section>
        
        <!-- Barra lateral -->
        <aside>
            <h3>Sobre Mi</h3>
            <p>Sóc Joan Martí, un desenvolupador web appassionat per ensenyar.</p>
            
            <h3>Categoríes Populars</h3>
            <ul>
                <li><a href="#">HTML</a> (5 articles)</li>
                <li><a href="#">CSS</a> (8 articles)</li>
                <li><a href="#">JavaScript</a> (3 articles)</li>
            </ul>
            
            <h3>Subscriu-te al Butlletí</h3>
            <form>
                <input type="email" placeholder="El teu email" required>
                <button type="submit">Subscriure</button>
            </form>
        </aside>
    </main>
    
    <!-- Peu de pàgina -->
    <footer>
        <div>
            <h4>Informació de Contacte</h4>
            <p>Email: joan@exemple.com</p>
            <p>Telèfon: +34 123 456 789</p>
        </div>
        
        <div>
            <h4>Enllaços Útils</h4>
            <ul>
                <li><a href="#">Política de Privacitat</a></li>
                <li><a href="#">Termes de Servei</a></li>
                <li><a href="#">Mapa del Lloc</a></li>
            </ul>
        </div>
        
        <div>
            <h4>Segueix-nos</h4>
            <a href="#">Facebook</a> | 
            <a href="#">Twitter</a> | 
            <a href="#">Instagram</a>
        </div>
        
        <p>&copy; 2024 Mi Blog. Tots els drets reservats.</p>
    </footer>
</body>
</html>
```

---

## 9. Taula Comparativa dels Elements

| Element | Propòsit | Ubicació | Múltiple |
|---------|----------|----------|----------|
| `<header>` | Introducció, navegació | Superior | Sí (per secció) |
| `<footer>` | Informació final | Inferior | Sí (per secció) |
| `<nav>` | Enllaços de navegació | Variable | Sí |
| `<section>` | Agrupa contingut temàtic | Dins main | Sí |
| `<article>` | Contingut independent | Dins section o main | Sí |
| `<aside>` | Contingut secundari | Al costat de main | Generalment 1 |

---

## 10. Beneficis dels Elements Semàntics

### 1. **Accessibilitat**
- Els lectors de pantalla entenen millor l'estructura
- Usuaris amb discapacitat poden navegar millor

### 2. **SEO (Posicionament en Cercadors)**
- Google entén millor el contingut
- Millor classificació en resultats de cerca

### 3. **Mantenibilitat**
- Codi més llegible i fàcil de mantenir
- Altres desenvolupadors comprenen ràpidament l'estructura

### 4. **Estil CSS**
- Més fàcil d'aplicar estils
- Millor control sobre la disposició

### 5. **Compatibilitat**
- Compatible amb navegadors moderns
- Millor suport futur

---

## 11. Exemple de Pàgina amb Estil CSS

```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <meta charset="UTF-8">
    <title>Lloc Web Semàntic</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f9f9f9;
        }
        
        header {
            background-color: #333;
            color: white;
            padding: 20px;
            text-align: center;
        }
        
        nav {
            background-color: #444;
            padding: 10px;
        }
        
        nav ul {
            list-style-type: none;
            margin: 0;
            padding: 0;
        }
        
        nav ul li {
            display: inline;
            margin-right: 20px;
        }
        
        nav a {
            color: white;
            text-decoration: none;
        }
        
        main {
            display: flex;
            max-width: 1000px;
            margin: 20px auto;
            gap: 20px;
        }
        
        article {
            flex: 2;
            background-color: white;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        aside {
            flex: 1;
            background-color: white;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 20px;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Benvinguts al Meu Lloc</h1>
    </header>
    
    <nav>
        <ul>
            <li><a href="#">Inici</a></li>
            <li><a href="#">Articles</a></li>
            <li><a href="#">Contacte</a></li>
        </ul>
    </nav>
    
    <main>
        <article>
            <h2>Estructura HTML Semàntica</h2>
            <p>Els elements semàntics ajuden a crear pàgines més accessibles i fàcils de mantenir.</p>
        </article>
        
        <aside>
            <h3>Informació Relacionada</h3>
            <ul>
                <li>Aprén més sobre HTML</li>
                <li>Guia de CSS</li>
                <li>Tutorial de JavaScript</li>
            </ul>
        </aside>
    </main>
    
    <footer>
        <p>&copy; 2024 Mi Lloc Web</p>
    </footer>
</body>
</html>
```

---

## 11. Els Elements `<span>` i `<div>`

### Introducció

Mentre que els elements semàntics (`<header>`, `<section>`, `<article>`, etc.) posseeixen significat i propòsit específic, els elements `<span>` i `<div>` són **genèrics** i sense significat semàntic. S'utilitzen quan no hi ha un element semàntic apropiat o quan necessites contenidors purs de disposició.

### 11.1. L'Element `<div>` (Division)

#### Descripció
El `<div>` és un element de **bloc** genèric que agrupa contingut sense significat semàntic. Es tracta del contenidor més versàtil en HTML.

#### Característiques
- **Tipus de visualització**: Bloc (`display: block`)
- **Occupa**: Tota l'amplada disponible
- **Propòsit**: Agrupar elements per motius de disposició o estil
- **Significat semàntic**: Cap
- **Ús**: Quando no hi ha un element semàntic més apropiat

#### Quan Utilitzar `<div>`

1. **Contenidors de disposició** — Per agrupar elements que vull estilitzar junt:
```html
<div class="contenidor-principal">
    <h2>Títol</h2>
    <p>Paràgraf 1</p>
    <p>Paràgraf 2</p>
</div>
```

2. **Grups de formularis** — Per estructurar grups de camps:
```html
<form>
    <div class="grup-formulari">
        <label for="nom">Nom:</label>
        <input type="text" id="nom" name="nom">
    </div>
    
    <div class="grup-formulari">
        <label for="email">Email:</label>
        <input type="email" id="email" name="email">
    </div>
</form>
```

3. **Wrappers de disseny** — Per crear estructures de disposició (Flexbox, Grid):
```html
<div class="flex-container">
    <div class="item">Element 1</div>
    <div class="item">Element 2</div>
    <div class="item">Element 3</div>
</div>
```

4. **Decoració i estil** — Quan necessites contenidors addicionals per a efectes visuals:
```html
<div class="card">
    <img src="imatge.jpg" alt="Imatge">
    <h3>Títol de la Targeta</h3>
    <p>Descripció</p>
</div>
```

#### Exemple Complet de `<div>`

```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <title>Exemple de DIV</title>
    <style>
        .contenidor {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f0f0f0;
        }
        
        .header-wrapper {
            background-color: #333;
            color: white;
            padding: 20px;
            border-radius: 5px;
        }
        
        .content-row {
            display: flex;
            gap: 20px;
            margin-top: 20px;
        }
        
        .card {
            flex: 1;
            background-color: white;
            padding: 15px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
    </style>
</head>
<body>
    <!-- Contenidor principal -->
    <div class="contenidor">
        <!-- Header wrapper -->
        <div class="header-wrapper">
            <h1>Benvingut al meu Lloc</h1>
            <p>Una pàgina web exemple</p>
        </div>
        
        <!-- Fila de contingut amb tres targetes -->
        <div class="content-row">
            <div class="card">
                <h3>Targeta 1</h3>
                <p>Descripció del primer element...</p>
            </div>
            
            <div class="card">
                <h3>Targeta 2</h3>
                <p>Descripció del segon element...</p>
            </div>
            
            <div class="card">
                <h3>Targeta 3</h3>
                <p>Descripció del tercer element...</p>
            </div>
        </div>
    </div>
</body>
</html>
```

---

### 11.2. L'Element `<span>`

#### Descripció
El `<span>` és un element **en línia** (inline) genèric que agrupa petit contingut sense significat semàntic. Es tracta d'un contenidor inline versàtil.

#### Característiques
- **Tipus de visualització**: Línia (inline)
- **Occupa**: Només l'espai necessari per al seu contingut
- **Propòsit**: Destacar o estilitzar petites porcions de text dins d'una línia
- **Significat semàntic**: Cap
- **Ús**: Quan no hi ha un element inline més apropiat

#### Quan Utilitzar `<span>`

1. **Destacar paraules específiques en un text**:
```html
<p>La <span style="color: red;">programació web</span> és fascinant.</p>
```

2. **Aplicar classes per a estil**:
```html
<p>Aquest és un <span class="ressaltat">text ressaltat</span> dins del paràgraf.</p>
```

3. **Marcar contingut per a JavaScript**:
```html
<p>El preu és: <span id="preu">10€</span></p>
<script>
    document.getElementById('preu').textContent = '15€';
</script>
```

4. **Wrapping d'icones o símbols**:
```html
<button>
    <span class="icona">★</span>
    <span class="text">Favorit</span>
</button>
```

5. **Estilitzar part d'un enllaç o botó**:
```html
<a href="#">
    <span class="subratllat">Feu clic aquí</span> per a més informació
</a>
```

#### Exemple Complet de `<span>`

```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <title>Exemple de SPAN</title>
    <style>
        .ressaltat {
            background-color: yellow;
            font-weight: bold;
        }
        
        .preus {
            color: green;
            font-size: 1.2em;
        }
        
        .error {
            color: red;
            font-weight: bold;
        }
        
        .badge {
            background-color: #007bff;
            color: white;
            padding: 2px 6px;
            border-radius: 3px;
            font-size: 0.9em;
        }
    </style>
</head>
<body>
    <h2>Exemples de SPAN</h2>
    
    <!-- Exemple 1: Text ressaltat -->
    <p>
        La <span class="ressaltat">web semàntica</span> és important per a 
        l'accessibilitat i el SEO.
    </p>
    
    <!-- Exemple 2: Preu destacat -->
    <p>
        El producte costa: <span class="preus">25,99€</span>
    </p>
    
    <!-- Exemple 3: Missatge d'error -->
    <p>
        Validació: <span class="error">Error: camp obligatori</span>
    </p>
    
    <!-- Exemple 4: Badge -->
    <p>
        Estat: <span class="badge">Nou</span>
    </p>
    
    <!-- Exemple 5: Parte de frase destacada -->
    <p>
        Per a més informació, consulta 
        <span style="text-decoration: underline;">la nostra guia completa</span>
        o contacta amb nosaltres.
    </p>
</body>
</html>
```

---

### 11.3. Comparació: `<div>` vs `<span>`

| Aspecte | `<div>` | `<span>` |
|---------|---------|----------|
| **Tipus de visualització** | Bloc | Línia |
| **Amplada** | Ocupa 100% disponible | Solo el necessari |
| **Altura** | Ocupa tot l'espai vertical | Altura del contingut |
| **Salts de línia** | Sí (abans i després) | No |
| **Ús típic** | Contenidors grans, disposició | Estilitzar text, small wrappers |
| **En formularis** | Agrupar camps | Marcar part d'una etiqueta |
| **En taules** | No aplicable | Marcar cel·les |
| **Propòsit** | Estructura i disposició | Estil i format inline |

---

### 11.4. Quan NO Utilitzar `<div>` o `<span>`

**Utilitza elements semàntics en lloc de `<div>`:**
- Per a capçaleres: `<header>` en lloc de `<div class="header">`
- Per a navegació: `<nav>` en lloc de `<div class="navigation">`
- Per a articles: `<article>` en lloc de `<div class="post">`
- Per a seccions: `<section>` en lloc de `<div class="section">`
- Per a barres laterals: `<aside>` en lloc de `<div class="sidebar">`

**Utilitza elements semàntics inline en lloc de `<span>`:**
- Per a text important: `<strong>` en lloc de `<span style="font-weight: bold;">`
- Per a text emfasitzat: `<em>` en lloc de `<span style="font-style: italic;">`
- Per a codi: `<code>` en lloc de `<span class="code">`
- Per a teclat: `<kbd>` en lloc de `<span class="keyboard">`

---

### 11.5. Exemple Pràctic: Comparació Visual

```html
<!DOCTYPE html>
<html lang="ca">
<head>
    <title>DIV vs SPAN</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        
        .demo {
            border: 2px dashed #ccc;
            padding: 10px;
            margin: 15px 0;
        }
        
        .div-exemple {
            background-color: #ffcccc;
            padding: 10px;
            border: 1px solid red;
        }
        
        .span-exemple {
            background-color: #ccffcc;
            padding: 2px 5px;
            border: 1px solid green;
        }
    </style>
</head>
<body>
    <h1>DIV vs SPAN: Comportament Visual</h1>
    
    <h2>Comportament de DIV (Bloc)</h2>
    <div class="demo">
        <p>Text abans del div</p>
        <div class="div-exemple">
            Aquest és un DIV (bloc)
        </div>
        <p>Text després del div</p>
    </div>
    
    <h2>Comportament de SPAN (Inline)</h2>
    <div class="demo">
        <p>
            Text antes del 
            <span class="span-exemple">SPAN (inline)</span>
            text después del span
        </p>
    </div>
    
    <h2>DIV per a Disposició</h2>
    <div class="demo">
        <div style="display: flex; gap: 10px;">
            <div style="flex: 1; background-color: #ffffcc; padding: 10px;">Element 1</div>
            <div style="flex: 1; background-color: #ffffcc; padding: 10px;">Element 2</div>
            <div style="flex: 1; background-color: #ffffcc; padding: 10px;">Element 3</div>
        </div>
    </div>
    
    <h2>SPAN dins de Paragrafs</h2>
    <div class="demo">
        <p>
            Els <span class="span-exemple">elements inline</span> no causen 
            salts de línia i es col·loquen al costat d'altres contingut inline.
        </p>
    </div>
</body>
</html>
```

---

### 11.6. Resumen de Bon Ús

#### Usa `<div>` quan:
- Necessites agrupar múltiples elements
- Vols crear contenidors de disposició (Flexbox, Grid)
- Vols aplicar estils a un grup d'elements
- No hi ha un element semàntic más apropiat
- Necessites estructurar la pàgina en seccions

#### Usa `<span>` quan:
- Necesites estilitzar part d'un text dins d'una línia
- Vols marcar contingut específic per a JavaScript
- Necesites un wrapper inline sense afectar el flux
- No hi ha un element semàntic inline más apropiat (como `<strong>`, `<em>`, `<code>`)

#### Usa elements semàntics quan:
- Tens una `<header>`, `<footer>`, `<nav>`, `<section>`, `<article>`, o `<aside>`
- Vols indicar significat al contingut
- Millora l'accessibilitat i el SEO
- Facilita la mantenibilitat del codi

---

## 12. Exercicis Pràctics

### Exercici 1: Estructura Bàsica
Crea una pàgina web amb els elements `<header>`, `<nav>`, `<section>`, i `<footer>`.

### Exercici 2: Blog Complet
Crea una estructura de blog amb múltiples `<article>` elements dins una `<section>`, un `<aside>` amb categories, i una `<nav>` de navegació.

### Exercici 3: Pàgina de Producte
Estructura una pàgina de producte online amb `<header>` (logotip i navegació), secció principal amb descripció, `<aside>` amb preus i `<footer>` amb informació de contacte.

### Exercici 4: Millora d'Accessibilitat
Pren una pàgina HTML anterior que hayas creat i refactoritza-la per usar elements semàntics correctament.

### Exercici 5: Practica DIV i SPAN
Crea una pàgina que demostri l'ús correcte de `<div>` i `<span>`:
- Utilitza `<div>` per crear una disposició de 3 columnes amb Flexbox
- Utilitza `<span>` per ressaltar paraules clau dins dels texts
- Aplica estils colors a `<div>` i `<span>` per veure la diferència visual

### Exercici 6: Refactorització Semàntica
Pren aquest codi no semàntic i refactoritza'l:
```html
<div class="header">
    <div class="nav">
        <a href="#">Link 1</a>
        <a href="#">Link 2</a>
    </div>
</div>

<div class="main">
    <div class="article">
        <div class="article-title">Títol</div>
        <div class="article-content">Contingut</div>
    </div>
    
    <div class="sidebar">
        <div class="related">Articles relacionats</div>
    </div>
</div>

<div class="footer">© 2024</div>
```

---

## 13. Recursos Addicionals

- [MDN Web Docs - HTML Semàntic](https://developer.mozilla.org/es/docs/Glossary/Semantics)
- [W3C - HTML5 Specification](https://www.w3.org/TR/html5/)
- [A11y Project](https://www.a11yproject.com/)
