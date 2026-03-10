# Generar un XSD amb `XmlSchemaExporter`

.NET inclou les classes `XmlReflectionImporter` i `XmlSchemaExporter` del namespace `System.Xml.Serialization`, que permeten generar automàticament un esquema XSD a partir d'una classe C#. Això és l'equivalent XML del `GetJsonSchemaAsNode` per a JSON Schema.

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
using System.Xml;
using System.Xml.Schema;
using System.Xml.Serialization;

class Program
{
    static void Main()
    {
        // Crea l'importador i l'exportador
        XmlReflectionImporter importer = new XmlReflectionImporter();
        XmlSchemas schemas = new XmlSchemas();
        XmlSchemaExporter exporter = new XmlSchemaExporter(schemas);

        // Genera el mapping del tipus i l'exporta com a esquema
        XmlTypeMapping mapping = importer.ImportTypeMapping(typeof(Persona));
        exporter.ExportTypeMapping(mapping);

        // Mostra l'XSD per consola
        using StringWriter sw = new StringWriter();
        using XmlTextWriter xw = new XmlTextWriter(sw);
        xw.Formatting = Formatting.Indented;
        schemas[0].Write(xw);

        Console.WriteLine(sw.ToString());
    }
}
```

## Resultat esperat

El codi anterior generarà un XSD similar a:

```xml
<?xml version="1.0" encoding="utf-16"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Persona" type="Persona" />
  <xs:complexType name="Persona">
    <xs:sequence>
      <xs:element minOccurs="0" maxOccurs="1" name="Nom" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="Edat" type="xs:int" />
      <xs:element minOccurs="0" maxOccurs="1" name="Correu" type="xs:string" />
    </xs:sequence>
  </xs:complexType>
</xs:schema>
```

> Fixa't que `Edat` (tipus `int`, no nullable) té `minOccurs="1"`, mentre que `Nom` i `Correu` (tipus `string`, referència) tenen `minOccurs="0"`.

## Exemple amb tipus compostos

```csharp
public class Equip
{
    public string NomEquip { get; set; }
    public List<Persona> Membres { get; set; }
}
```

```csharp
XmlReflectionImporter importer = new XmlReflectionImporter();
XmlSchemas schemas = new XmlSchemas();
XmlSchemaExporter exporter = new XmlSchemaExporter(schemas);

XmlTypeMapping mapping = importer.ImportTypeMapping(typeof(Equip));
exporter.ExportTypeMapping(mapping);

using StringWriter sw = new StringWriter();
using XmlTextWriter xw = new XmlTextWriter(sw);
xw.Formatting = Formatting.Indented;
schemas[0].Write(xw);

Console.WriteLine(sw.ToString());
```

Resultat:

```xml
<?xml version="1.0" encoding="utf-16"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Equip" type="Equip" />
  <xs:complexType name="Equip">
    <xs:sequence>
      <xs:element minOccurs="0" maxOccurs="1" name="NomEquip" type="xs:string" />
      <xs:element minOccurs="0" maxOccurs="1" name="Membres" type="ArrayOfPersona" />
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="ArrayOfPersona">
    <xs:sequence>
      <xs:element minOccurs="0" maxOccurs="unbounded" name="Persona" type="Persona" />
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name="Persona">
    <xs:sequence>
      <xs:element minOccurs="0" maxOccurs="1" name="Nom" type="xs:string" />
      <xs:element minOccurs="1" maxOccurs="1" name="Edat" type="xs:int" />
      <xs:element minOccurs="0" maxOccurs="1" name="Correu" type="xs:string" />
    </xs:sequence>
  </xs:complexType>
</xs:schema>
```

> Les col·leccions (`List<T>`) generen un `complexType` addicional amb `maxOccurs="unbounded"`.

## Guardar l'esquema en un fitxer

```csharp
XmlReflectionImporter importer = new XmlReflectionImporter();
XmlSchemas schemas = new XmlSchemas();
XmlSchemaExporter exporter = new XmlSchemaExporter(schemas);

XmlTypeMapping mapping = importer.ImportTypeMapping(typeof(Persona));
exporter.ExportTypeMapping(mapping);

using FileStream fs = new FileStream("persona.xsd", FileMode.Create);
using XmlTextWriter xw = new XmlTextWriter(fs, System.Text.Encoding.UTF8);
xw.Formatting = Formatting.Indented;
schemas[0].Write(xw);

Console.WriteLine("✅ Esquema generat i guardat a persona.xsd");
```

## Comparativa amb JSON Schema

| | XML (XSD) | JSON (JSON Schema) |
|---|---|---|
| Classes | `XmlReflectionImporter` + `XmlSchemaExporter` | `JsonSerializerOptions.GetJsonSchemaAsNode` |
| Namespace | `System.Xml.Serialization` | `System.Text.Json.Schema` |
| Retorna | `XmlSchemas` (col·lecció de `XmlSchema`) | `JsonNode` |
| Requisit mínim | .NET Framework / .NET Core 1.0+ | .NET 9 |
| Col·leccions | `maxOccurs="unbounded"` | `"type": "array"` amb `"items"` |
| Nullable | `minOccurs="0"` / `nillable="true"` | `"type": ["string", "null"]` |

## Resum

| Concepte | Detall |
|---|---|
| Classes principals | `XmlReflectionImporter` + `XmlSchemaExporter` |
| Namespace | `System.Xml.Serialization` |
| Retorna | `XmlSchemas` (col·lecció de `XmlSchema`) |
| Disponibilitat | Totes les versions de .NET |
| Col·leccions (`List<T>`) | Genera `complexType` amb `maxOccurs="unbounded"` |
