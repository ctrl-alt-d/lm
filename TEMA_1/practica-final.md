# Pràctica Final

Anem a codificar la informació en els diferents formats que hem vist.

## Dades a codificar

Una empresa de venda de plats preparats vol emmagatzemar la informació dels seus plats en diferents formats. La informació que es vol emmagatzemar és:
* **Nom** (Exemple: Paella)
* **Ingredients**
* **Al·lergogens**
* **Preu** (Exemple: 12.50)

Per a cada **Ingredient** tindrem:
* **Nom** (Exemple: Arròs)
* **Quantitat** (Exemple: 200.6)
* **Unitats** (Exemple: grams, litres, unitats)
* **Calories** (Exemple: 120 kcal)

Per a cada **Al·lergogen** tindrem:
* **Descripció** (Exemple: Pot contenir traces de fruits secs)

## 0. Dades a codificar

Les dades que volem codificar són les següents, però podeu crear tants plats com vulgueu o fer servir només els 2 primers:


### Paella

**Preu:** 12.50 €

**Ingredients:**

| Nom | Quantitat | Unitats | Calories |
|---|---:|:---:|---:|
| Arròs | 200.0 | grams | 180 kcal |
| Camaró | 100.0 | grams | 90 kcal |
| Pollastre | 150.0 | grams | 210 kcal |
| Safrà | 0.5 | grams | 2 kcal |
| Aigua | 500.0 | ml | 0 kcal |

**Al·lergògens:**

- Pot contenir traces de crustacis
- Conté safrà

---

### Amanida de Tonyina

**Preu:** 8.00 €

**Ingredients:**

| Nom | Quantitat | Unitats | Calories |
|---|---:|:---:|---:|
| Enciam | 80.0 | grams | 14 kcal |
| Tomàquet | 100.0 | grams | 18 kcal |
| Tonyina | 120.0 | grams | 132 kcal |
| Ou dur | 50.0 | grams | 77 kcal |
| Oliva | 10.0 | unitats | 40 kcal |

**Al·lergògens:**

- Ou

---

### Crema de Carbassa

**Preu:** 6.50 €

**Ingredients:**

| Nom | Quantitat | Unitats | Calories |
|---|---:|:---:|---:|
| Carbassa | 300.0 | grams | 85 kcal |
| Ceba | 50.0 | grams | 20 kcal |
| Oli d'oliva | 10.0 | grams | 90 kcal |
| Brou vegetal | 400.0 | ml | 10 kcal |

**Al·lergògens:**

- Pot contenir traces de llet



## 1. Fixer markdown
Hem codificat la informació en markdown. Crea un document incloent els 'plats' amb els que tu treballaràs.

Els següents punts, cal també incoure'ls dins el fitxer markdown:

## 2. Fitxer XML
Codifiqueu la informació en un fitxer XML seguint les normes que hem vist a la pràctica d'XML. Podeu crear tants plats com vulgueu.
Comproveu que el vostre fitxer és correcte a [XMLValidation](https://www.xmlvalidation.com/)

## 3. Fitxer JSON
Codifiqueu la informació en un fitxer JSON seguint les normes que hem vist a la pràctica de JSON. Podeu crear tants plats com vulgueu.
Comproveu que el vostre fitxer és correcte a [JSONLint](https://jsonlint.com/)
Nota: Es perfectament correcte iniciar el json amb una llista (array) de plats.

## 4. Fitxer YAML
Codifiqueu la informació en un fitxer YAML seguint les normes que hem vist a la pràctica de YAML. Podeu crear tants plats com vulgueu.
Comproveu que el vostre fitxer és correcte a [YAML Lint](https://www.yamllint.com/)

## 5. CSV
Pensa com ho codificaries en un fitxer CSV. Quines columnes tindria? Com representaries els ingredients i al·lergogens? Escriu un exemple de com seria el fitxer CSV.