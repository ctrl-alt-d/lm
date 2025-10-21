# Sessió de Formació: Creació de Formularis en HTML

## Objectius

- **Aprendre a crear formularis en HTML.**
- **Comprendre els diferents elements de formularis: `<form>`, `<input>`, `<select>`, `<textarea>`.**
- **Conèixer els tipus de camps d'entrada: text, password, radio, checkbox.**

## Continguts

1. **Introducció als Formularis HTML**
   - Importància dels formularis en el desenvolupament web
   - Estructura bàsica d'un formulari

2. **Elements de Formulari**
   - `<form>`: Definició i atributs principals
   - `<input>`: Tipus i atributs
   - `<select>` i `<option>`: Creació de llistes desplegables
   - `<textarea>`: Àrees de text multi-línia

3. **Tipus de Camps d'Entrada**
   - **Text:** Captura de dades alfanumèriques
   - **Password:** Camps per a contrasenyes
   - **Radio:** Selecció única entre diverses opcions
   - **Checkbox:** Selecció múltiple d'opcions

4. **Validació de Formularis**
   - Validació HTML5
   - Validació amb JavaScript (al següent tema)

5. **Accessibilitat en Formularis**
   - Bones pràctiques per a formularis accessibles

## Desenvolupament del Contingut

### 1. Introducció als Formularis HTML

- **Importància dels Formularis:**
  - Permeten la interacció de l'usuari amb la web.
  - Recopilació de dades com registres, comentaris, cercadors, etc.

- **Estructura Bàsica:**
  - Exemple d'un formulari bàsic:

```html
    <form action="procesar.php" method="post">
      <!-- Camps del formulari -->
    </form>
```

### 2. Elements de Formulari

#### `<form>`

- **Atributs Principals:**
  - `action`: URL a la qual s'envien les dades.
  - `method`: Mètode d'enviament (`get` o `post`).
  - `id` i `class`: Per a estils i scripts.

#### `<input>`

- **Tipus Comuns:**
  - `type="text"`
  - `type="password"`
  - `type="radio"`
  - `type="checkbox"`
  - `type="submit"`

- **Exemple:**
```html
  <input type="text" name="nom" placeholder="El teu nom">
```

#### `<select>` i `<option>`

- **Creació de Llistes Desplegables:**
```html
  <label for="pais">País:</label>
  <select id="pais" name="pais">
    <option value="espanya">Espanya</option>
    <option value="francia">França</option>
    <option value="itali">Itàlia</option>
  </select>
```

#### `<textarea>`

- **Àrees de Text Multi-línia:**
```html
  <label for="comentari">Comentari:</label>
  <textarea id="comentari" name="comentari" rows="4" cols="50"></textarea>
```

### 3. Tipus de Camps d'Entrada

#### **Text**

- **Ús:** Captura de dades alfanumèriques simples.
- **Exemple:**

```html
  <input type="text" name="usuari" placeholder="Nom d'usuari">
```

#### **Password**

- **Ús:** Captura de contrasenyes de manera segura.
- **Exemple:**

```html
  <input type="password" name="contrasenya" placeholder="Contrasenya">
```

#### **Radio**

- **Ús:** Permet seleccionar una única opció d'un conjunt.
- **Exemple:**
```html
  <p>Gènere:</p>
  <input type="radio" id="masculí" name="genere" value="masculí">
  <label for="masculí">Masculí</label><br>
  <input type="radio" id="femení" name="genere" value="femení">
  <label for="femení">Femení</label>
```

#### **Checkbox**

- **Ús:** Permet seleccionar múltiples opcions.
- **Exemple:**
```html
  <p>Interessos:</p>
  <input type="checkbox" id="tecnologia" name="interessos" value="tecnologia">
  <label for="tecnologia">Tecnologia</label><br>
  <input type="checkbox" id="art" name="interessos" value="art">
  <label for="art">Art</label>
```

### 4. Validació de Formularis

- **HTML5:**
  - Atributs com `required`, `pattern`, `min`, `max`.
  - Exemples:
```html
    <input type="email" name="correu" required>
```

- **JavaScript (Introducció):**
  - Validació personalitzada.
  - Missatges d'error.

### 5. Accessibilitat en Formularis

#### Creant Formularis Accessibles

##### Visió General

Per crear un formulari accessible en línia, cal assegurar-se que tots els camps del formulari tinguin etiquetes o indicacions precises perquè els usuaris de lectors de pantalla sàpiguen què se sol·licita en cada camp. Els formularis normalment tenen etiquetes o indicacions que són òbvies per als usuaris amb visió, però la seva associació amb camps particulars es basa en pistes visuals, com la posició relativa i la proximitat al camp. Com que els usuaris de lectors de pantalla no tenen accés a aquestes mateixes pistes visuals, les etiquetes i les indicacions s'han d'associar explícitament amb els camps del formulari dins del HTML. A continuació, es presenten algunes tècniques per aconseguir-ho.

##### Ús de l'Element `<label>`

Considera el següent camp i la indicació que l'acompanya:

```html
<div>
  Last name: 
  <input type="text" name="last_name" id="last_name">
</div>
```

La indicació "Last name" precedeix el camp d'entrada, però la seva relació amb el camp no està definida explícitament. Per tant, alguns lectors de pantalla simplement anuncien aquest camp com un camp "edit", però no indiquen a l'usuari que ha d'introduir el "Last name" en aquest camp. Altres lectors de pantalla intentaran endevinar l'etiqueta, i en aquest exemple probablement ho faran amb exactitud. No obstant això, a mesura que els formularis creixen en complexitat, els lectors de pantalla que intenten endevinar les etiquetes tenen més probabilitats d'errar, cosa que significa que els usuaris tenen més probabilitats de completar el formulari incorrectament.

El següent codi ha estat corregit. "Last name" ara està definit com una etiqueta, i està associat explícitament amb el camp del formulari perquè l'atribut `for` de l'etiqueta i l'atribut `id` de l'input comparteixen el mateix valor.

```html
<div>
  <label for="last_name">Last name:</label> 
  <input type="text" name="last_name" id="last_name">
</div>
```

##### Proporcionant Text d'Ajuda Suplementari

Només s'permite una única etiqueta `<label>` per camp del formulari. No obstant això, si hi ha text d'ajuda addicional disponible, es pot associar amb el camp del formulari utilitzant l'atribut `aria-describedby`. Els lectors de pantalla anuncien tant l'etiqueta com el text d'ajuda quan el camp del formulari està en focus.

```html
<label for="DOB">Date of birth:</label>
<input type="text" name="birthdate" id="DOB" aria-describedby="DOB-help">
<span id="DOB-help">El format de data és MM/DD/YYYY</span>
```

##### Ús dels Elements `<fieldset>` i `<legend>`

Per a grups de camps relacionats com ara botons de ràdio i caselles de selecció, cada camp del formulari ha de tenir una etiqueta com s'ha descrit en la secció anterior. No obstant això, aquesta indicació solament pot ser inintel·ligible si l'usuari no sap quina és la pregunta. La tècnica per abordar aquest problema és agrupar aquests elements utilitzant un element `<fieldset>`, i després utilitzar un element `<legend>` per marcar la pregunta, com en l'exemple següent:

```html
<fieldset>
  <legend>What is your favorite color?</legend>
  <div>
    <input type="radio" name="color" value="Red" id="color_red">
    <label for="color_red">Red</label>
  </div>
  <div>
    <input type="radio" name="color" value="Green" id="color_green">
    <label for="color_green">Green</label>
  </div>
  <div>
    <input type="radio" name="color" value="Blue" id="color_blue">
    <label for="color_blue">Blue</label>
  </div>
</fieldset>
```

## Exemples Pràctics

1. **Formulari de Registre Bàsic:**
   - Camps per a nom, correu electrònic, contrasenya, gènere, interessos.
   - Validació dels camps requerits.

2. **Formulari de Contacte:**
   - Àrea de text per a missatges.
   - Selecció de motiu del contacte.

## Exercici Pràctic

**Crea un formulari de subscripció a un butlletí de notícies:**

- Camps requerits:
  - Nom complet (text)
  - Adreça de correu electrònic (email)
  - Preferències de contingut (checkbox entre 3 opcions)
  - País (select entre 5 països)
  - Comentaris addicionals (textarea)

**Objectius de l'exercici:**

- Aplicar els coneixements apresos.
- Implementar la validació bàsica.

## Recursos Addicionals

- [Documentació MDN sobre Formularis HTML](https://developer.mozilla.org/ca/docs/Web/HTML/Element/form)
- [Tutorials de W3Schools](https://www.w3schools.com/html/html_forms.asp)
- [Guia d'Accessibilitat en Formularis](https://www.w3.org/WAI/tutorials/forms/)
- Per a més exemples de controls de formulari, pots consultar l'article de WebAIM sobre [Creating Accessible Forms](https://webaim.org/techniques/forms/).

#### Bones Pràctiques per a Formularis Accessibles

- **Associació Correcta d'Etiquetes:** Utilitza sempre l'element `<label>` i assegura't que l'atribut `for` coincideixi amb l'atribut `id` del camp corresponent.
  
- **Text d'Ajuda Suplementari:** Utilitza l'atribut `aria-describedby` per associar textos d'ajuda addicionals amb els camps del formulari.
  
- **Agrupació de Camps Relacionats:** Utilitza els elements `<fieldset>` i `<legend>` per agrupar camps relacionats i proporcionar un context clar per als usuaris de lectors de pantalla.
  
- **Navegació Accessible:** Assegura't que el formulari sigui navegable mitjançant el teclat, sense necessitat d'un ratolí.
  
- **Missatges d'Error Clarificadors:** Proporciona missatges d'error clars i específics que ajudin els usuaris a corregir els errors de manera efectiva.
  
- **Contrastes de Colors Adequats:** Assegura't que hi hagi un contrast de colors suficient entre el text i el fons per a una millor llegibilitat. (quan veiem css)

- **Evitar Exclusivament Pistes Visibles:** No depenguis únicament de pistes visuals (com ara el color) per comunicar informació essencial o requisits dels camps del formulari. (quan veiem css)

##### Exemple de Formulari Accessible

```html
<label for="email">Correu Electrònic:</label>
<input type="email" id="email" name="email" required aria-describedby="email-help">
<span id="email-help">Introdueix un correu electrònic vàlid, per exemple, exemple@domini.com</span>
```html

Aquest exemple mostra com associar correctament una etiqueta amb un camp d'entrada i proporcionar text d'ajuda suplementari que serà anunciat pels lectors de pantalla.



## Q&A

Finalitzarem la sessió amb una secció de preguntes i respostes per aclarir qualsevol dubte i assegurar-nos que tots els participants han comprès els conceptes presentats.
