## Introducció a YAML

YAML (YAML Ain't Markup Language) és un format de serialització de dades que és senzill de llegir per humans. S'utilitza àmpliament per configurar fitxers i per intercanviar dades entre aplicacions, gràcies a la seva estructura clara i l'ús d'indentació en lloc de símbols com `{}` o `[]` que són comuns en altres formats com JSON.

### Característiques principals de YAML

1. **Claus i valors**
   YAML organitza les dades en parells clau-valor, separats per dos punts (`:`). L'estructura està basada en la indentació per definir les relacions entre elements.

2. **Indentació**
   L'indentació en YAML és crucial per representar l'estructura jeràrquica de les dades. Es recomana utilitzar espais en lloc de tabulacions per mantenir la consistència.

3. **Llistes**
   Les llistes es defineixen amb guions (`-`). Cada element de la llista comença amb un guió seguit d'un espai.

4. **Comentaris**
   Els comentaris en YAML es marquen amb el símbol de coixinet (`#`). Tot el que segueix el coixinet serà ignorat pel parser de YAML.

5. **Tipus de dades**
   YAML admet diversos tipus de dades, com ara:
   - **String**: Text en línia, sense necessitat de cometes, tot i que es poden utilitzar cometes simples o dobles si el text conté caràcters especials.
   - **Números**: Es poden escriure directament com a enters o decimals.
   - **Booleans**: Els valors `true` i `false` són reconeguts com a booleans.
   - **Null**: Representat amb `null` o amb una cadena buida.

### Exemple complet de YAML

Aquest és un exemple complet de com es pot estructurar un fitxer YAML per representar informació sobre un usuari:

```yaml
usuari:
  nom: Joan
  edat: 30
  correu: joan@example.com
  interessos:
    - lectura
    - música
    - programació
```

## Pràctica: Creació i validació d'un fitxer YAML

**Objectiu:**  
Aprendre a estructurar dades en format YAML i comprovar que el fitxer té una sintaxi correcta.

---

### 1. Descripció de la pràctica

Es vol emmagatzemar informació sobre diferents usuaris en un fitxer YAML. La informació que es vol emmagatzemar és:

- **Nom** de l'usuari
- **Edat**
- **Correu electrònic**
- **Interessos** (una llista d'interessos)

### 2. Creació del fitxer YAML

Els estudiants han de crear un fitxer YAML que contingui informació de diversos usuaris amb les dades especificades.

**Exemple de fitxer YAML que han de crear:**

```yaml
usuari_1:
  nom: Anna
  edat: 25
  correu: anna@example.com
  interessos:
    - esport
    - viatges
    - cuina

usuari_2:
  nom: Marc
  edat: 28
  correu: marc@example.com
  interessos:
    - fotografia
    - muntanyisme

usuari_3:
  nom: Laia
  edat: 32
  correu: laia@example.com
  interessos:
    - lectura
    - programació
    - música
```

---

### 3. Validació del fitxer YAML

Comprovar si el fitxer YAML té una sintaxi vàlida. Es pot utilitzar un validor online com [YAML Lint](http://www.yamllint.com/) per validar el fitxer i assegurar-se que està ben estructurat.

### 4. Provar errors

Introdueir algun error en el fitxer YAML, com per exemple:
- Falta d'indentació.
- Utilitzar tabulacions en lloc d'espais.
- Ometre els dos punts després d'una clau.

**Exemple d'un fitxer incorrecte:**

```yaml
usuari_1:
  nom: Anna
  edat 25  # Falta dos punts
  correu: anna@example.com
interessos:
  - esport  # Incorrecte: falta indentació
```

---

### **Objectius d'aprenentatge:**
- Aprendre la sintaxi bàsica de YAML.
- Comprendre com estructurar dades en YAML.
- Aprendre a identificar i corregir errors comuns en YAML.

