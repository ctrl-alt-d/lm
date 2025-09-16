---
marp: true
theme: default
class: lead
paginate: true
footer: 'Lenguajes de Marcas | Curso'
---

# Lenguatges de Marques

Explorant els llenguatges més utilitzats en web, ciència i tecnologia.


---

# Què resol un llenguatge de marques?

Els llenguatges de marques s'utilitzen per estructurar i presentar informació de manera coherent, estandarditzada i comprensible per humans i màquines.


---


# Humans: Estructuració del contingut

Un llenguatge de marques permet definir la jerarquia i l'organització del text (títols, paràgrafs, llistes, etc.). Això facilita la lectura i la comprensió tant per a usuaris.

---
# Separació de contingut i presentació

Gràcies als llenguatges de marques (com HTML), podem estructurar el contingut d'una manera clara i reutilitzable, separant-lo de com es veu (CSS) o es presenta a l'usuari.

---

# Màquines: Estructuració del contingut

Un llenguatge de marques permet intercanvi d'informació d'una manera estructurada sense haver de reinventar la roda cada cop que volem intercanviar dades..

---

# Intercanvi d'informació i accessibilitat

Llenguatges com XML, JSON i YAML permeten l'intercanvi de dades estructurades entre aplicacions diferents. També asseguren que els continguts siguin accessibles en diversos dispositius.

---

# HTML (HyperText Markup Language)

**Definició:**
HTML és el llenguatge de marques més comú utilitzat per crear pàgines web. Defineix l'estructura bàsica d'una pàgina web mitjançant elements com títols, paràgrafs, enllaços i imatges.

**Aplicabilitat:**
S'utilitza per estructurar el contingut web, definir hipervincles, imatges i proporcionar una base per a fulls d'estil (CSS) i JavaScript.

---

# HTML: Exemple de Codi

```html
<!DOCTYPE html>
<html>
  <head>
    <title>La Meva Pàgina Web</title>
  </head>
  <body>
    <h1>Benvinguts</h1>
    <p>Aquesta és una pàgina d'exemple.</p>
  </body>
</html>
```

---

# Markdown

**Definició:**
Markdown és un llenguatge de marques lleuger que s'utilitza comunament per escriure documentació, arxius README i contingut per a blocs o wikis.

**Aplicabilitat:**
És ideal per a documents lleugers i fàcilment llegibles, i s'utilitza molt en plataformes com GitHub i altres gestors de versions.

---

# Markdown: Exemple de Codi

```markdown
# Títol Principal
Aquest és un paràgraf amb **negretes** i *cursives*.

- Element de llista
- Un altre element

[Enllaç a GitHub](https://github.com)
```

---

# XML (Extensible Markup Language)

**Definició:**
XML és un llenguatge de marques dissenyat per emmagatzemar i transportar dades. A diferència d'HTML, XML no defineix etiquetes predefinides, sinó que permet als usuaris crear les seves pròpies etiquetes per adaptar-se a la informació que es vol representar. És autodescriptiu i està dissenyat per ser tant llegible per màquines com per humans.

**Aplicabilitat:**
És utilitzat en la transmissió de dades entre sistemes, especialment en entorns empresarials i governamentals, així com en arxius de configuració, documents estructurats i serveis web (com ara SOAP).

# XML: Exemple

```xml
<llibre>
  <títol>El Petit Príncep</títol>
  <autor>Antoine de Saint-Exupéry</autor>
  <any>1943</any>
</llibre>
```

---


# JSON (JavaScript Object Notation)

**Definició:**
JSON és un format lleuger per a l'intercanvi de dades, basat en una estructura de parells clau-valor. Tot i que tècnicament no és un llenguatge de marques, s'utilitza àmpliament per a la transmissió de dades en aplicacions web.

**Aplicabilitat:**
És molt utilitzat en APIs, en l'intercanvi de dades entre aplicacions i com a format per a arxius de configuració.

---

# JSON: Exemple de Codi

```json
{
  "nom": "Joan",
  "edat": 30,
  "ocupació": "Desenvolupador"
}
```

---


# YAML (YAML Ain't Markup Language)

**Definició:**
YAML és un format de serialització de dades que és més llegible i simple que JSON o XML. Es fa servir sovint en fitxers de configuració per la seva claredat i senzillesa.

**Aplicabilitat:**
S'utilitza principalment en configuracions de programari, automatització de scripts i descripcions d'infraestructura com ara Kubernetes.

---

# YAML: Exemple de Codi

```yaml
persona:
  nom: "Anna"
  edat: 25
  ocupació: "Enginyera"
```
---

# LaTeX

**Definició:**
LaTeX és un llenguatge de marques utilitzat per a la creació de documents científics i matemàtics. És especialment útil per incloure fórmules i equacions complexes de manera clara i estructurada.

**Aplicabilitat:**
S'utilitza en la redacció d'articles acadèmics, tesis, llibres científics i qualsevol document que necessiti una composició tipogràfica precisa, especialment en matemàtiques.

---

# LaTeX: Exemple de Codi

```latex
\documentclass{article}
\begin{document}
\title{El meu Document en LaTeX}
\author{Autor}
\date{\today}
\maketitle

\section{Introducció}
Aquest és un document d'exemple.

\end{document}
```
---

# SVG (Scalable Vector Graphics)

**Definició:**
SVG és un llenguatge de marques basat en XML per descriure gràfics vectorials escalables. Permet crear imatges i gràfics que es poden ampliar sense perdre qualitat.

**Aplicabilitat:**
És útil per a il·lustracions, gràfics, i animacions en llocs web, ja que els gràfics vectorials poden ser redimensionats sense pèrdua de resolució.

---

# SVG: Exemple de Codi

```xml
<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" stroke="black" stroke-width="3" fill="red" />
</svg>
```

---

# MathML (Mathematical Markup Language)

**Definició:**
MathML és un llenguatge basat en XML dissenyat per descriure notacions matemàtiques i la seva estructura. És especialment útil per mostrar equacions matemàtiques en pàgines web de manera estructurada i comprensible.

**Aplicabilitat:**
S'utilitza per incloure fórmules matemàtiques en documents interactius i llocs web que requereixen presentar contingut matemàtic de manera precisa.

---

# MathML: Exemple de Codi

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <msup>
    <mi>x</mi>
    <mn>2</mn>
  </msup>
</math>
```

---

# RSS/ATOM

**Definició:**
RSS i ATOM són llenguatges de marques utilitzats per crear feeds de notícies o blocs, permetent la distribució automàtica de contingut actualitzat en llocs web.

**Aplicabilitat:**
Són útils per compartir contingut dinàmic, com actualitzacions de blocs, llocs de notícies, podcasts o qualsevol contingut en línia que requereixi distribució automàtica.

---

# RSS: Exemple de Codi

```xml
<rss version="2.0">
  <channel>
    <title>El meu Blog</title>
    <link>http://www.elmeublog.com</link>
    <description>Últimes publicacions</description>
    <item>
      <title>Publicació d'Exemple</title>
      <link>http://www.elmeublog.com/exemple</link>
      <description>Aquesta és una publicació d'exemple.</description>
    </item>
  </channel>
</rss>
```

---

# Exemples de Llenguatges de Marques

A continuació veurem exemples de diferents llenguatges de marques a partir de fonts reals.

---

# RSS Feed (XML)

**URL d'exemple:**
[https://www.nasa.gov/rss/dyn/breaking_news.rss](https://www.nasa.gov/rss/dyn/breaking_news.rss)

Aquest enllaç et retorna un fitxer XML amb les últimes notícies de la NASA.

---

# JSON API

**URL d'exemple:**
[https://nominatim.openstreetmap.org/reverse?lat=41.3851&lon=2.1734&format=json](https://nominatim.openstreetmap.org/reverse?lat=41.3851&lon=2.1734&format=json)

Aquest enllaç et retorna un objecte JSON amb informació sobre una publicació d'exemple.

---

# SVG

**URL d'exemple:**
[https://dev.w3.org/SVG/tools/svgweb/samples/svg-files/410.svg](https://dev.w3.org/SVG/tools/svgweb/samples/svg-files/410.svg)

Aquest enllaç mostra un gràfic vectorial SVG.

---

# LaTeX

**URL d'exemple:**
[https://arxiv.org/abs/1501.00001](https://arxiv.org/abs/1501.00001)

Aquest en
