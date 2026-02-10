# Xuleta de Sintaxi de Validació JSON Schema


* [Què és json schema?](https://json-schema.org/overview/what-is-jsonschema#what-is-json-schema)

## Exemple d'un JSON que compleix amb un JSON Schema

```json
{
  "Persones": [
    {
      "Nom": "Anna",
      "Edat": 30
    },
    {
      "Nom": "Pere",
      "Edat": 25
    }
  ]
}
```

## Exemple de fitxer JSON Schema corresponent

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "object",
  "properties": {
    "Persones": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "Nom": { "type": "string" },
          "Edat": { "type": "integer", "minimum": 0, "maximum": 120 }
        },
        "required": ["Nom", "Edat"]
      }
    }
  },
  "required": ["Persones"]
}
```

## Elements Bàsics en JSON Schema

### Definir una propietat simple
```json
"Nom": { "type": "string" }
```

### Definir un objecte
```json
"Persona": {
  "type": "object",
  "properties": {
    "Nom": { "type": "string" },
    "Edat": { "type": "integer" }
  },
  "required": ["Nom", "Edat"]
}
```

### Tipus de dades bàsics en JSON Schema
- `string` → Cadena de text
- `integer` → Enter
- `number` → Número decimal
- `boolean` → Cert o fals (`true` / `false`)
- `array` → Llista de valors
- `object` → Estructura amb propietats
- `null` → Valor nul

### Definir atributs en objectes
```json
"Persona": {
  "type": "object",
  "properties": {
    "Nom": { "type": "string" },
    "id": { "type": "integer" }
  },
  "required": ["Nom"]
}
```

### Restriccions de valors
```json
"Edat": {
  "type": "integer",
  "minimum": 0,
  "maximum": 120
}
```

### Enumeracions (valors predefinits)
```json
"Color": {
  "type": "string",
  "enum": ["Vermell", "Verd", "Blau"]
}
```

### Definir propietats opcionals o amb múltiples ocurrències
- Opcional (`required` no especificat)
- Repetit com a array

```json
"Persones": {
  "type": "array",
  "items": {
    "type": "object",
    "properties": {
      "Nom": { "type": "string" },
      "Edat": { "type": "integer" }
    },
    "required": ["Nom", "Edat"]
  }
}
```


# 📖 Documentació sobre JSON Schema

Si busques informació sobre **JSON Schema**, aquí tens alguns recursos útils:

## 🌍 Web oficial
- [JSON Schema](https://json-schema.org/) – Documentació oficial, guies d’ús i especificacions.

## 📂 Repositoris oficials
- [JSON Schema a GitHub](https://github.com/json-schema-org) – Repositoris amb especificacions i eines relacionades.

## 📜 Documentació en APIs
- [Swagger/OpenAPI](https://swagger.io/docs/specification/data-models/) – Explicació sobre JSON Schema en el context d'APIs.

## 📚 Altres fonts útils
- [MDN (Mozilla Developer Network)](https://developer.mozilla.org/en-US/docs/Web/JSON) – Explicació general de JSON i recursos addicionals.
- [Stack Overflow - JSON Schema](https://stackoverflow.com/questions/tagged/json-schema) – Preguntes i respostes sobre JSON Schema.

## 🛠 Eines per validar esquemes JSON
- [JSON Schema Validator](https://www.jsonschemavalidator.net/)
- [JSONLint](https://jsonlint.com/)


