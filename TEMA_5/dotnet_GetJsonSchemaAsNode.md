# Generar un JSON Schema amb `GetJsonSchemaAsNode`

A partir de .NET 9, la llibreria `System.Text.Json` inclou el mètode `JsonSchemaExporter.GetJsonSchemaAsNode`, que permet generar automàticament un JSON Schema a partir d'una classe C#. Això és útil per documentar l'estructura esperada de les dades o per validar JSON d'entrada sense haver d'escriure l'esquema manualment.

## Classe d'exemple

```csharp
public class Persona
{
    public string Nom { get; set; }
    public int Edat { get; set; }
    public string? Correu { get; set; }
}
```

## Generar l'esquema

```csharp
using System.Text.Json;
using System.Text.Json.Nodes;
using System.Text.Json.Schema;

class Program
{
    static void Main()
    {
        // Opcions de serialització (es poden personalitzar)
        JsonSerializerOptions options = new JsonSerializerOptions
        {
            WriteIndented = true
        };

        // Genera el JSON Schema com a JsonNode
        JsonNode schemaNode = options.GetJsonSchemaAsNode(typeof(Persona));

        // Mostra l'esquema per consola
        Console.WriteLine(schemaNode.ToJsonString(new JsonSerializerOptions { WriteIndented = true }));
    }
}
```

## Resultat esperat

El codi anterior generarà un esquema similar a:

```json
{
  "type": "object",
  "properties": {
    "Nom": { "type": "string" },
    "Edat": { "type": "integer" },
    "Correu": { "type": ["string", "null"] }
  },
  "required": ["Nom", "Edat"]
}
```

> Fixa't que `Correu` és `string?` (nullable), per tant l'esquema accepta tant `string` com `null`. Les propietats no nullable apareixen a `required`.

## Exemple amb tipus compostos

```csharp
public class Equip
{
    public string NomEquip { get; set; }
    public List<Persona> Membres { get; set; }
}
```

```csharp
JsonSerializerOptions options = new JsonSerializerOptions { WriteIndented = true };
JsonNode schema = options.GetJsonSchemaAsNode(typeof(Equip));
Console.WriteLine(schema.ToJsonString(new JsonSerializerOptions { WriteIndented = true }));
```

Resultat:

```json
{
  "type": "object",
  "properties": {
    "NomEquip": { "type": "string" },
    "Membres": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "Nom": { "type": "string" },
          "Edat": { "type": "integer" },
          "Correu": { "type": ["string", "null"] }
        },
        "required": ["Nom", "Edat"]
      }
    }
  },
  "required": ["NomEquip", "Membres"]
}
```

## Guardar l'esquema en un fitxer

```csharp
JsonSerializerOptions options = new JsonSerializerOptions { WriteIndented = true };
JsonNode schema = options.GetJsonSchemaAsNode(typeof(Persona));

string schemaJson = schema.ToJsonString(new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText("persona_schema.json", schemaJson);

Console.WriteLine("✅ Esquema generat i guardat a persona_schema.json");
```

## Resum

| Concepte | Detall |
|---|---|
| Mètode | `JsonSerializerOptions.GetJsonSchemaAsNode(Type)` |
| Namespace | `System.Text.Json.Schema` |
| Retorna | `JsonNode` amb l'esquema JSON Schema |
| Requisit mínim | .NET 9 |
| Nullable (`?`) | Genera `"type": ["string", "null"]` |
| Col·leccions (`List<T>`) | Genera `"type": "array"` amb `"items"` |
