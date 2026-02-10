# Validar un xml contra el seu esquema

## xml:

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


```c#
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
