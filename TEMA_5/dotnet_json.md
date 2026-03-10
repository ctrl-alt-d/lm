# Validar un json contra el seu esquema

Nota, les llibreries dotnet encara no suporten validació d'esquema, s'ha fet servir https://www.nuget.org/packages/JsonSchema.Net/

> `dotnet add package JsonSchema.Net`

## json:

```json
{
  "Persona": {
    "Nombre": "Juan Pérez",
    "Edad": 30
  }
}
```

## XSD

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "type": "object",
  "properties": {
    "Persona": {
      "type": "object",
      "properties": {
        "Nombre": { "type": "string" },
        "Edad": { "type": "integer" }
      },
      "required": ["Nombre", "Edad"]
    }
  },
  "required": ["Persona"]
}

```

## C#


```c#
namespace provaJSON;
using System;
using System.IO;
using System.Text.Json;
using Json.Schema;



class Program
{
    static void Main()
    {
        string jsonPath = "archivo.json";  // Ruta del fitxer JSON
        string schemaPath = "esquema.json";  // Ruta del fitxer JSON Schema

        if (ValidateJson(jsonPath, schemaPath))
        {
            Console.WriteLine("✅ El JSON és vàlid segons l'esquema JSON Schema.");
        }
        else
        {
            Console.WriteLine("❌ El JSON no és vàlid. Revisa els errors.");
        }
    }

    public static bool ValidateJson(string jsonFilePath, string schemaFilePath)
    {
        bool isValid = true;

        try
        {
            // Llegeix el fitxer JSON i el fitxer de l'esquema
            string jsonText = File.ReadAllText(jsonFilePath);
            string schemaText = File.ReadAllText(schemaFilePath);

            // Parseja l'esquema
            JsonSchema schema = JsonSchema.FromText(schemaText);

            // Parseja el JSON
            JsonDocument jsonDocument = JsonDocument.Parse(jsonText);

            // Valida el JSON contra l'esquema
            var result = schema.Evaluate(jsonDocument.RootElement);

            if (!result.IsValid)
            {
                isValid = false;
                Console.WriteLine("[ERRORS DE VALIDACIÓ]");
                
            }
        }
        catch (Exception ex)
        {
            isValid = false;
            Console.WriteLine($"[EXCEPCIÓ] {ex.Message}");
        }

        return isValid;
    }
}

```

## .csproj
Recorda que quan afegim fitxers externs al projecte (per exemple `archivo.json` i `esquema.json`) cal que aquests siguin copiats a la carpeta de sortida del build perquè l'executable els pugui llegir en temps d'execució (p. ex. `bin/Debug/net6.0`).

Hi ha dues maneres bàsiques de fer-ho:

- Des de l'IDE: a l'Explorador de solucions selecciona el fitxer, obre `Properties` i a la propietat **Copy to Output Directory** tria `Copy always` o `Copy if newer`.
- Editant el fitxer `.csproj` manualment: afegeix entrades dins de `<ItemGroup>` per marcar els fitxers com a `Content` o `None` i indicar `CopyToOutputDirectory`.

Exemples pràctics (afegeix-los dins del teu `.csproj`):

1) Exemple per a un fitxer concret (`archivo.json`, `esquema.json`):

```xml
  <ItemGroup>
    <None Include="archivo.json">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </None>
    <None Include="esquema.json">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </None>
  </ItemGroup>
```

2) Exemple per copiar tots els `.json` del projecte (comodí):

```xml
  <ItemGroup>
    <None Include="**\*.json">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </None>
  </ItemGroup>
```
