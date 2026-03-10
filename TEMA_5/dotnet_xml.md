# Validar un xml contra el seu esquema

## XML

```xml
<?xml version="1.0" encoding="utf-8"?>
<Persona>
  <Nombre>Juan Pérez</Nombre>
  <Edad>30</Edad>
</Persona>
```

## XSD

```xml
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="Persona">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="Nombre" type="xs:string"/>
        <xs:element name="Edad" type="xs:int"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## C#


```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Schema;

class Program
{
    static void Main()
    {
        string xmlPath = "archivo.xml";  // Ruta del archivo XML
        string xsdPath = "archivo.xsd";  // Ruta del archivo XSD

        if (ValidateXml(xmlPath, xsdPath))
        {
            Console.WriteLine("✅ El XML es válido según el esquema XSD.");
        }
        else
        {
            Console.WriteLine("❌ El XML no es válido. Revisa los errores.");
        }
    }

    public static bool ValidateXml(string xmlFilePath, string xsdFilePath)
    {
        // Variable que indicarà si l'XML és vàlid o no.
        bool isValid = true;

        // Creació d'un conjunt d'esquemes XML (XSD).
        XmlSchemaSet schemaSet = new XmlSchemaSet();
        
        // Afegeix l'esquema XSD especificat al conjunt d'esquemes.
        schemaSet.Add("", xsdFilePath);

        // Configuració del lector XML per a la validació.
        XmlReaderSettings settings = new XmlReaderSettings();
        
        // Assigna el conjunt d'esquemes al lector XML.
        settings.Schemas = schemaSet;
        
        // Indica que el tipus de validació serà segons l'esquema XSD.
        settings.ValidationType = ValidationType.Schema;

        // Definició del gestor d'errors de validació.
        settings.ValidationEventHandler += (sender, args) =>
        {
            // Si es detecta un error de validació, es marca com a no vàlid.
            isValid = false;

            // Mostra un missatge d'error amb la línia i columna on s'ha detectat el problema.
            Console.WriteLine($"[ERROR] Línia {args.Exception.LineNumber}, Columna {args.Exception.LinePosition}: {args.Message}");
        };

        // Obre el fitxer XML i aplica la configuració definida anteriorment.
        using (XmlReader reader = XmlReader.Create(xmlFilePath, settings))
        {
            try
            {
                // Llegeix tot el fitxer XML per a validar-lo.
                while (reader.Read()) { }
            }
            catch (Exception ex)
            {
                // Captura qualsevol excepció durant la lectura i la mostra per consola.
                isValid = false;
                Console.WriteLine($"[EXCEPCIÓ] {ex.Message}");
            }
        }

        // Retorna true si l'XML és vàlid, o false si hi ha hagut errors.
        return isValid;
    }


}
```

## .csproj
Recorda que quan afegim fitxers externs al projecte (per exemple `archivo.xml` i `archivo.xsd`) cal que aquests siguin copiats a la carpeta de sortida del build perquè l'executable els pugui llegir en temps d'execució (p. ex. `bin/Debug/net10.0`).

Hi ha dues maneres bàsiques de fer-ho:

- Des de l'IDE: a l'Explorador de solucions selecciona el fitxer, obre `Properties` i a la propietat **Copy to Output Directory** tria `Copy always` o `Copy if newer`.
- Editant el fitxer `.csproj` manualment: afegeix entrades dins de `<ItemGroup>` per marcar els fitxers com a `Content` o `None` i indicar `CopyToOutputDirectory`.

Exemples útils (afegeix-los dins del teu `.csproj`):

1) Exemple per a un fitxer concret (`archivo.xml`, `archivo.xsd`):

```xml
  <ItemGroup>
    <None Include="archivo.xml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </None>
    <None Include="archivo.xsd">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </None>
  </ItemGroup>
```

2) Exemple per copiar tots els `.xml` i `.xsd` del projecte (comodí):

```xml
  <ItemGroup>
    <None Include="**\*.xml">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </None>
    <None Include="**\*.xsd">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </None>
  </ItemGroup>
```

3) Exemple si tens una carpeta `Assets` amb diversos recursos:

```xml
  <ItemGroup>
    <None Include="Assets\**\*.*">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </None>
  </ItemGroup>
```
