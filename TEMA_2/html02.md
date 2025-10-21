# Sessió 2: Etiquetes d'HTML

**Objectius:**
1. Comprendre l'ús d'etiquetes per estructurar continguts.
2. Treballar amb llistes, imatges i enllaços.

---

## 1. Llistes en HTML (30 min)
- **Llistes ordenades i desordenades**
  - **Llista desordenada (`<ul>`):** Utilitzada per a elements sense un ordre específic.
  - **Llista ordenada (`<ol>`):** Utilitzada per a elements que requereixen un ordre.
  
**Exemple de llista desordenada:**

```html
<ul>
  <li>Primer element</li>
  <li>Segon element</li>
  <li>Tercer element</li>
</ul>
```

**Exemple de llista ordenada:**

```html
<ol>
  <li>Primer pas</li>
  <li>Segon pas</li>
  <li>Últim pas</li>
</ol>
```

---

## 2. Inserció d'imatges (30 min)
- **Etiqueta d'imatge (`<img>`):**
  - Utilitzada per inserir imatges en una pàgina web.
  - Atributs importants: `src` (font de la imatge) i `alt` (text alternatiu).

**Exemple:**

```html
<img src="https://www.example.com/imatge.jpg" alt="Descripció de la imatge" >
```

---

## 3. Creació d'enllaços (30 min)
- **Enllaços externs i interns (`<a>`):**
  - **Enllaços externs:** Enllaços que redirigeixen a una pàgina web diferent.
  - **Enllaços interns:** Enllaços que redirigeixen a una secció específica dins de la mateixa pàgina.

**Exemple d'enllaç extern:**

```html
<a href="https://www.example.com">Visita example.com</a>
```

**Exemple d'enllaç intern:**

```html
<a href="#seccio">Vés a la secció</a>
<!-- blah blah -->
<h4 id="seccio">Secció 4</h4>
```

---

## 4. Activitat pràctica
- Crear una pàgina HTML que inclogui:
  - Una llista desordenada amb tres elements.
  - Una llista ordenada amb tres passos.
  - Una imatge amb un text alternatiu.
  - Un enllaç extern i un enllaç intern.
