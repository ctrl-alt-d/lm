## Conceptes bàsics de JSON

JSON (JavaScript Object Notation) és un format utilitzat per emmagatzemar i intercanviar dades de manera estructurada. A continuació es detallen alguns dels conceptes bàsics del format JSON, en particular l'ús de `{`, `[` i altres elements.

### 1. **Objectes `{}`**
Els objectes en JSON estan delimitats per claudàtors `{}`. Un objecte és una col·lecció de parells clau-valor, on la **clau** és sempre un string i el **valor** pot ser de diferents tipus (string, número, array, objecte, booleà o `null`).

**Exemple d'un objecte:**
```json
{ "nom": "Pit de pollastre", "kilocalories": 100 }
```

En aquest exemple:
- `"nom"` és la clau i `"Pit de pollastre"` és el valor.
- `"kilocalories"` és la clau i `100` és el valor.

### 2. **Arrays `[]`**
Els arrays en JSON estan delimitats per claudàtors quadrats `[]`. Un array és una llista ordenada de valors que poden ser de qualsevol tipus permès en JSON, inclosos altres objectes o arrays.

**Exemple d'un array:**
```json
[ "Pit de pollastre", "Salmó", "Ou bullit" ]
```

Aquest array conté tres strings, però els elements podrien ser números, objectes, o altres arrays.

### 3. **Claus i valors**
En JSON, les claus són sempre strings, mentre que els valors poden ser de diversos tipus:
- **String**: Entre cometes dobles (`"..."`), com `"Pit de pollastre"`.
- **Número**: Com `100` (no cal posar cometes).
- **Array**: Com es mostra a l'exemple anterior.
- **Objecte**: Com es mostra a l'exemple d'objectes anterior.
- **Booleà**: Pot ser `true` o `false`.
- **Null**: Indica absència de valor, representat per `null`.

### 4. **Sintaxi bàsica**
- Els objectes es delimiten amb `{}`.
- Els arrays es delimiten amb `[]`.
- Els parells clau-valor dins d'un objecte es separen amb una coma i cada parell es defineix amb dos punts (`:`).
- Els elements d'un array es separen amb comes.

---

**Exemple complet d'un document JSON:**

```json
{
  "menjars": [
    {
      "nom": "Pit de pollastre",
      "kilocalories": 100,
      "proteines": 20,
      "greixos": 10
    },
    {
      "nom": "Salmó",
      "kilocalories": 208,
      "proteines": 22,
      "greixos": 13
    }
  ]
}
```

En aquest exemple:
- `menjars` és una clau que conté un array d'objectes.
- Cada objecte dins l'array representa un menjar amb la seva informació nutricional.

Amb aquests conceptes, pots estructurar dades de manera clara i comprensible utilitzant JSON.



## Pràctica: Creació i validació d'un document JSON

**Objectiu:**  
Aprendre a estructurar informació en un document JSON i validar que la seva sintaxi és correcta.

---

### Descripció:

Es vol emmagatzemar informació sobre menjars en un document JSON. La informació que es vol emmagatzemar és:

* **Nom** (Exemple: Pit de pollastre)
* **Kilocalories** per 100 grams (Exemple: 100)
* **Proteïnes** per 100 grams (Exemple: 20)
* **Greixos** per 100 grams (Exemple: 10)

---

### 1. Creació d'un document JSON

Codificar la informació de diversos menjars en format JSON. 

**Exemple de document JSON que han de crear:**

```json
{
  "menjars": [
    {
      "nom": "Pit de pollastre",
      "kilocalories": 100,
      "proteines": 20,
      "greixos": 10
    },
    {
      "nom": "Salmó",
      "kilocalories": 208,
      "proteines": 22,
      "greixos": 13
    },
    {
      "nom": "Ou bullit",
      "kilocalories": 155,
      "proteines": 13,
      "greixos": 11
    }
  ]
}
```

---

### 2. Validació del document JSON

Indica als estudiants que utilitzin un validor online de JSON, com [JSONLint](https://jsonlint.com/), per comprovar si el document té una estructura vàlida i una sintaxi correcta.

---

### 3. Provar errors

Feu modificacions en el document JSON per provocar errors, per exemple:

- Oblidar posar cometes al voltant de les claus o valors de tipus string.
- Eliminar una clau o valor.
- Oblidar una coma després d'un element.

**Exemple amb un error:**

```json
{
  "menjars": [
    {
      "nom": Pit de pollastre,  // Error: falta posar cometes al voltant del valor "Pit de pollastre"
      "kilocalories": 100,
      "proteines": 20,
      "greixos": 10
    }
  ]
}
```


**Error detectat pel validor:**

```
Error: Parse error on line 3: 
{ "menjars": [ { "nom": Pit de pollastre...
```

---

### **Objectius d'aprenentatge:**
- Comprendre la sintaxi bàsica de JSON.
- Aprendre a estructurar la informació de manera adequada en JSON.
- Aprendre a validar un document JSON i identificar errors comuns.

---


## Exercici: JSON a les respostes d'una API

Donat d'alta [openweathermap](https://openweathermap.org/) i utilitza la API https://openweathermap.org/forecast5 per obtenir el temps que farà a Figueres els propers dies.

Hauràs de crear una API Key per poder fer les consultes.

La consulta la pots fer des del navegador, tindrà un format semblant a:

```
https://api.openweathermap.org/data/2.5/forecast?lat=42.2670&lon=2.9617&appid=f8f8f8f8f8f8f8f8f8f8f8ff8
```

El resultat serà un xml semblant a:

```xml
{
  "cod": "200",
  "message": 0,
  "cnt": 40,
  "list": [
    {
      "dt": 1727719200,
      "main": {
        "temp": 294.06,
        "feels_like": 294.3,
        "temp_min": 288.66,
        "temp_max": 294.06,
        "pressure": 1020,
        "sea_level": 1020,
        "grnd_level": 1007,
        "humidity": 80,
        "temp_kf": 5.4
      },
      "weather": [
        {
          "id": 800,
          "main": "Clear",
          "description": "clear sky",
          "icon": "01n"
        }
      ],
      "clouds": {
        "all": 0
      },
      "wind": {
        "speed": 0.49,
        "deg": 41,
        "gust": 0.78
      },
      "visibility": 10000,
      "pop": 0,
      "sys": {
        "pod": "n"
      },
      "dt_txt": "2024-09-30 18:00:00"
    },
```

Un cop ho hagis fet, contesta:

* En quin format ens retorna les dades la API de openweathermap.
* Quina avantatge té aquest format respecte que ens tornés les dades en un fitxer de text pla totes una sota de l'altre?

---

Amb aquesta pràctica, els estudiants aprenen a estructurar la informació en JSON i poden veure com els errors de sintaxi són detectats pels validors.
