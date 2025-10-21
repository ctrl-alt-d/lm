
# Solució: Pràctica Final

Aquest document conté exemples de com codificar la informació dels plats en diferents formats: Markdown, XML, JSON, YAML i una proposta de com representar-ho en CSV. S'han creat tres plats d'exemple: Paella, Amanida de Tonyina i Crema de Carbassa.

---

## Dades d'exemple (resum)

- Nom: Paella
- Ingredients: Arròs, Camaró, Pollastre, Safrà, Aigua
- Al·lergògens: Pot contenir traces de crustacis
- Preu: 12.50

- Nom: Amanida de Tonyina
- Ingredients: Enciam, Tomàquet, Tonyina, Ou dur, Oliva
- Al·lergògens: Ou
- Preu: 8.00

- Nom: Crema de Carbassa
- Ingredients: Carbassa, Ceba, Oli d'oliva, Brou vegetal
- Al·lergògens: Pot contenir traces de llet
- Preu: 6.50

---

## 1) Fitxer Markdown

Aquí teniu una possible codificació en Markdown. Fem servir títols, llistes i taules per organitzar la informació.

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

---

## 2) Fitxer XML

Exemple de com es podria estructurar la informació en XML. El fitxer té l'arrel `plats` i cada `plat` conté `ingredients` i `alergogens`.

```xml
<?xml version="1.0" encoding="utf-8"?>
<plats>
	<plat>
		<nom>Paella</nom>
		<preu>12.50</preu>
		<ingredients>
			<ingredient>
				<nom>Arròs</nom>
				<quantitat unitats="grams">200.0</quantitat>
				<calories>180 kcal</calories>
			</ingredient>
			<ingredient>
				<nom>Camaró</nom>
				<quantitat unitats="grams">100.0</quantitat>
				<calories>90 kcal</calories>
			</ingredient>
			<!-- ... més ingredients ... -->
		</ingredients>
		<alergogens>
			<alergogen>Pot contenir traces de crustacis</alergogen>
		</alergogens>
	</plat>
	<plat>
		<nom>Amanida de Tonyina</nom>
		<preu>8.00</preu>
		<ingredients>
			<ingredient>
				<nom>Enciam</nom>
				<quantitat unitats="grams">80.0</quantitat>
				<calories>14 kcal</calories>
			</ingredient>
			<!-- ... -->
		</ingredients>
		<alergogens>
			<alergogen>Ou</alergogen>
		</alergogens>
	</plat>
	<!-- Crema de Carbassa, etc. -->
</plats>
```

Notes per a XML:

- Assegura't d'utilitzar entitats i escapar caràcters especials quan calgui (p. ex. &amp;).
- Pots validar el fitxer a https://www.xmlvalidation.com/.

## 3) Fitxer JSON

Una representació en JSON (array de plats). Aquest JSON és fàcilment processable per aplicacions web o scripts Python/Node.

```json
[
	{
		"nom": "Paella",
		"preu": 12.50,
		"ingredients": [
			{"nom": "Arròs", "quantitat": 200.0, "unitats": "grams", "calories": "180 kcal"},
			{"nom": "Camaró", "quantitat": 100.0, "unitats": "grams", "calories": "90 kcal"},
			{"nom": "Pollastre", "quantitat": 150.0, "unitats": "grams", "calories": "210 kcal"}
		],
		"alergogens": ["Pot contenir traces de crustacis"]
	},
	{
		"nom": "Amanida de Tonyina",
		"preu": 8.00,
		"ingredients": [
			{"nom": "Enciam", "quantitat": 80.0, "unitats": "grams", "calories": "14 kcal"},
			{"nom": "Tomàquet", "quantitat": 100.0, "unitats": "grams", "calories": "18 kcal"}
		],
		"alergogens": ["Ou"]
	}
]
```

Punts a comprovar amb JSON:

- Valida a https://jsonlint.com/.
- Utilitza nombres per a quantitats i preus per facilitar càlculs.

## 4) Fitxer YAML

Exemple de fitxer YAML que representa la mateixa informació. YAML és molt llegible per humans i serveix bé per configuracions i intercanvi de dades.

```yaml
plats:
	- nom: "Paella"
		preu: 12.50
		ingredients:
			- nom: "Arròs"
				quantitat: 200.0
				unitats: "grams"
				calories: "180 kcal"
			- nom: "Camaró"
				quantitat: 100.0
				unitats: "grams"
				calories: "90 kcal"
		alergogens:
			- "Pot contenir traces de crustacis"

	- nom: "Amanida de Tonyina"
		preu: 8.00
		ingredients:
			- nom: "Enciam"
				quantitat: 80.0
				unitats: "grams"
				calories: "14 kcal"
		alergogens:
			- "Ou"
```

Valida el YAML a https://www.yamllint.com/ o un altre validador abans d'usar-lo.

## 5) CSV — proposta i exemple

CSV és un format tabular; representar estructures aninhades (ingredients amb diversos camps) requereix convensions. Aquí tens dues opcions:

1) CSV 'aplanat' amb una columna on es serialitzen els ingredients com a JSON (fàcil d'importar després).

Capçaleres proposades:

nom,preu,ingredients_json,alergogens

Exemple de línia (com a CSV amb cometes per la columna JSON):

"Paella",12.50,"[{""nom"": ""Arròs"", ""quantitat"": 200.0, ""unitats"": ""grams""}, {""nom"": ""Camaró"", ""quantitat"": 100.0, ""unitats"": ""grams""}]","Pot contenir traces de crustacis"

Nota: si utilitzes aquest mètode, escapa cometes dins la cadena JSON segons l'estàndard CSV del teu processador.

2) CSV normalitzat (múltiples files per plat), on cada línia representa un ingredient — això facilita càlculs i consultes amb eines SQL/Excel:

Capçaleres proposades:

plat_nom,preu,ingredient_nom,ingredient_quantitat,ingredient_unitats,ingredient_calories,alergogens

Exemple (3 línies corresponents a 3 ingredients de la Paella):

Paella,12.50,Arròs,200.0,grams,"180 kcal","Pot contenir traces de crustacis"
Paella,12.50,Camaró,100.0,grams,"90 kcal","Pot contenir traces de crustacis"
Paella,12.50,Pollastre,150.0,grams,"210 kcal","Pot contenir traces de crustacis"

Aquest segon format és més adient per eines que treballen per fila (Excel, pandas, bases relationals) i és senzill d'usar per agregar calories, costos, etc.

---

## Notes finals i bones pràctiques

- Tria el format segons l'ús: JSON/YAML per interfícies i intercanvi; XML si cal interoperabilitat amb sistemes que l'exigeixin; CSV per fulls de càlcul i importacions senzilles.
- Mantingues els nombres com a tipus numèrics (no com a strings) per facilitar càlculs.
- Per camps amb text lliure (descripcions d'al·lergògens), evita caràcters problemàtics o escapa'ls correctament.
- Si esperes ingredients amb múltiples al·lergògens o subcamps addicionals, considera normalitzar la dada (taules separades o arrays en JSON/YAML).

Si vols, puc generar fitxers separats (`plats.md`, `plats.xml`, `plats.json`, `plats.yaml`, `plats.csv`) amb aquests continguts i afegir-los al repositori. Vols que els creï ara?

