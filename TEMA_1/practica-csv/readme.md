## Conceptes bàsics de CSV
CSV (Comma-Separated Values) és un format senzill per emmagatzemar dades tabulars, com les que es troben en fulls de càlcul o bases de dades. Cada línia del fitxer representa un registre i cada camp està separat per una coma (o, en alguns casos, per altres caràcters com el punt i coma).

### 1. **Estructura bàsica d'un fitxer CSV**
Un fitxer CSV conté:
- Una primera línia amb els noms de les columnes (opcionales però recomanables).
- Cada línia següent conté els valors corresponents a cada columna, separats per comes.

**Exemple de fitxer CSV:**
```csv
nom,kilocalories,proteines,greixos
Pit de pollastre,100,20,10
Salmó,208,22,13
Ou bullit,155,13,11
```

En aquest exemple:
- La primera línia indica els noms de les columnes.
- Cada línia següent representa un menjar amb la seva informació nutricional.

### 2. **Separadors alternatius**
En alguns països, especialment on la coma s'utilitza com a separador decimal, es fa servir el punt i coma (`;`) com a separador de camps.

**Exemple:**
```csv
nom;kilocalories;proteines;greixos
Pit de pollastre;100;20;10
```

### 3. **Cometes i caràcters especials**
Si un valor conté una coma, salt de línia o cometes, s'ha d'envoltar amb cometes dobles (`"`).

**Exemple:**
```csv
nom,descripcio
"Pit de pollastre","Carn blanca, baixa en greix"
```

### 4. **Sintaxi bàsica**
- Cada línia representa un registre.
- Els camps es separen per comes (o punt i coma).
- Els valors amb comes o salts de línia s'envolten amb cometes dobles.

---

## Pràctica: Creació i validació d'un fitxer CSV

**Objectiu:**  
Aprendre a estructurar informació en un fitxer CSV i validar que la seva sintaxi és correcta.

---

### Descripció:

Es vol emmagatzemar informació sobre menjars en un fitxer CSV. La informació que es vol emmagatzemar és:

* **Nom** (Exemple: Pit de pollastre)
* **Kilocalories** per 100 grams (Exemple: 100)
* **Proteïnes** per 100 grams (Exemple: 20)
* **Greixos** per 100 grams (Exemple: 10)

---

### 1. Creació d'un fitxer CSV

Codifica la informació de diversos menjars en format CSV.

**Exemple de fitxer CSV que han de crear:**
```csv
nom,kilocalories,proteines,greixos
Pit de pollastre,100,20,10
Salmó,208,22,13
Ou bullit,155,13,11
```

---

### 2. Validació del fitxer CSV

Utilitza un editor de text o un full de càlcul (com Excel, LibreOffice Calc o Google Sheets) per obrir el fitxer CSV i comprovar que la informació es mostra correctament en columnes.

També pots utilitzar eines online com [CSVLint](https://csvlint.io/) per validar la sintaxi del fitxer.

---

### 3. Provar errors

Fes modificacions en el fitxer CSV per provocar errors, per exemple:

- Ometre una coma entre camps.
- Afegir una línia amb menys o més camps que les altres.
- No posar cometes dobles en valors amb comes.

**Exemple amb un error:**
```csv
nom,kilocalories,proteines,greixos
Pit de pollastre 100,20,10  // Error: falta una coma entre "Pit de pollastre" i "100"
```

**Error detectat pel validor:**

```
Line 2 has 3 fields, expected 4
```

---

### **Objectius d'aprenentatge:**
- Comprendre la sintaxi bàsica del format CSV.
- Aprendre a estructurar la informació de manera adequada en CSV.
- Aprendre a validar un fitxer CSV i identificar errors comuns.

---

## Exercici: CSV i eines de processament

>T'aborreixes amb els exercicis? Prova a fer aquest!

1. Crea un fitxer CSV amb la informació nutricional de 5 menjars diferents.
2. Obre el fitxer amb un full de càlcul i comprova que la informació es mostra correctament.
3. Instal·lat Python amb `pandas`, prova d'importar el fitxer CSV des d'un script en Python utilitzant la llibreria `pandas`:

```python
import pandas as pd
df = pd.read_csv('menjars.csv')
print(df)
```

4. Què passa si el fitxer CSV té errors de format? Prova-ho i observa el missatge d'error.

