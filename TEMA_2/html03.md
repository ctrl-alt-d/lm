# Sessió 3: Taules en HTML

**Objectius:**
1. Aprendre a crear taules i formularis en HTML.

---

## 1. Introducció a les Taules
- **Etiqueta de taula (`<table>`):** Utilitzada per a crear una taula.
- **Files (`<tr>`):** Representen cada fila de la taula.
- **Cel·les de dades (`<td>`):** Contenen el contingut de cada cel·la de la taula.
- **Cel·les d'encapçalament (`<th>`):** Utilitzades per a definir les cel·les d'encapçalament de la taula, generalment en negreta i centrades.
  
**Exemple bàsic de taula:**

```html
<table>
  <tr>
    <th>Encapçalament 1</th>
    <th>Encapçalament 2</th>
  </tr>
  <tr>
    <td>Dada 1</td>
    <td>Dada 2</td>
  </tr>
  <tr>
    <td>Dada 3</td>
    <td>Dada 4</td>
  </tr>
</table>
```

---

## 2. Estructura avançada de Taules
- **Encapçalament de taula (`<thead>`):** Utilitzat per a definir el conjunt de cel·les d'encapçalament.
- **Corps de taula (`<tbody>`):** Conté el contingut principal de la taula.

**Exemple de taula amb encapçalament i cos:**

```html
<table>
  <thead>
    <tr>
      <th>Nom</th>
      <th>Edats</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Ana</td>
      <td>25</td>
    </tr>
    <tr>
      <td>Joan</td>
      <td>30</td>
    </tr>
  </tbody>
</table>
```


>Once again, the CSS and visual result are unchanged—specifying such table section groups provides valuable contextual information for assistive technologies, including screen readers and search engines, as well as for styling in the CSS, which will be shown in a later example.

[mnd web docs - Explicitly specifying table section groups](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table#explicitly_specifying_table_section_groups)

LLegiu també l'us de [<caption>](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table#table_caption_and_column_summary)

---

## 3. Activitat pràctica
- Crear una taula que inclogui:
  - Un encapçalament amb dues cel·les.
  - Tres files de dades amb dues cel·les cadascuna.
  - Utilitzar les etiquetes `<thead>` i `<tbody>`.

---
