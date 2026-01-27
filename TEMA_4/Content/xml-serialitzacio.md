# Serialització en XML

La serialització XML en .NET ens permet convertir objectes a format XML per persistir-los a disc o transmetre'ls.

## Usant XmlSerializer

L'`XmlSerializer` és la classe principal per serialitzar objectes a XML. Vegem un exemple bàsic:

```c#
using System.Xml.Serialization;

namespace SerializeXmlBasic
{
    public class WeatherForecast
    {
        public DateTime Date { get; set; }
        public int TemperatureCelsius { get; set; }
        public string? Summary { get; set; }
    }

    public class Program
    {
        public static void Main()
        {
            var weatherForecast = new WeatherForecast
            {
                Date = DateTime.Parse("2019-08-01"),
                TemperatureCelsius = 25,
                Summary = "Hot"
            };

            var serializer = new XmlSerializer(typeof(WeatherForecast));
            
            using var stringWriter = new StringWriter();
            serializer.Serialize(stringWriter, weatherForecast);
            
            string xmlString = stringWriter.ToString();
            Console.WriteLine(xmlString);
        }
    }
}
// output:
// <?xml version="1.0" encoding="utf-16"?>
// <WeatherForecast xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">
//   <Date>2019-08-01T00:00:00</Date>
//   <TemperatureCelsius>25</TemperatureCelsius>
//   <Summary>Hot</Summary>
// </WeatherForecast>
```

## Persistir a disc

Per desar l'XML a un fitxer:

```c#
using System.Xml.Serialization;

namespace SerializeXmlToFile
{
    public class WeatherForecast
    {
        public DateTime Date { get; set; }
        public int TemperatureCelsius { get; set; }
        public string? Summary { get; set; }
    }

    public class Program
    {
        public static void Main()
        {
            var weatherForecast = new WeatherForecast
            {
                Date = DateTime.Parse("2019-08-01"),
                TemperatureCelsius = 25,
                Summary = "Hot"
            };

            string fileName = "WeatherForecast.xml";
            var serializer = new XmlSerializer(typeof(WeatherForecast));
            
            using var fileStream = new FileStream(fileName, FileMode.Create);
            serializer.Serialize(fileStream, weatherForecast);
            
            Console.WriteLine($"Fitxer creat: {fileName}");
            Console.WriteLine(File.ReadAllText(fileName));
        }
    }
}
```

## Estructures complexes amb llistes

Quan treballem amb llistes, necessitem usar atributs per controlar com es serialitzen:

```c#
using System.Xml.Serialization;

namespace SerializeXmlComplex
{
    public class WeatherForecast
    {
        public DateTime Date { get; set; }
        public int TemperatureCelsius { get; set; }
        public string? Summary { get; set; }
        
        [XmlArray("DatesAvailable")]
        [XmlArrayItem("Date")]
        public List<DateTime>? DatesAvailable { get; set; }
        
        [XmlArray("TemperatureRanges")]
        [XmlArrayItem("Range")]
        public List<TemperatureRange>? TemperatureRanges { get; set; }
        
        [XmlArray("SummaryWords")]
        [XmlArrayItem("Word")]
        public List<string>? SummaryWords { get; set; }
    }

    public class TemperatureRange
    {
        [XmlAttribute("name")]
        public string? Name { get; set; }
        public int High { get; set; }
        public int Low { get; set; }
    }

    public class Program
    {
        public static void Main()
        {
            var weatherForecast = new WeatherForecast
            {
                Date = DateTime.Parse("2019-08-01"),
                TemperatureCelsius = 25,
                Summary = "Hot",
                DatesAvailable = new List<DateTime>
                {
                    DateTime.Parse("2019-08-01"),
                    DateTime.Parse("2019-08-02")
                },
                TemperatureRanges = new List<TemperatureRange>
                {
                    new TemperatureRange { Name = "Cold", High = 20, Low = -10 },
                    new TemperatureRange { Name = "Hot", High = 60, Low = 20 }
                },
                SummaryWords = new List<string> { "Cool", "Windy", "Humid" }
            };

            string fileName = "WeatherForecastComplex.xml";
            var serializer = new XmlSerializer(typeof(WeatherForecast));
            
            using var fileStream = new FileStream(fileName, FileMode.Create);
            serializer.Serialize(fileStream, weatherForecast);
            
            Console.WriteLine(File.ReadAllText(fileName));
        }
    }
}
```

## Atributs XML útils

| Atribut | Descripció |
|---------|------------|
| `[XmlRoot("NomElement")]` | Defineix el nom de l'element arrel |
| `[XmlElement("NomElement")]` | Defineix el nom d'un element |
| `[XmlAttribute("nom")]` | Serialitza com a atribut en lloc d'element |
| `[XmlArray("NomLlista")]` | Defineix el nom del contenidor de la llista |
| `[XmlArrayItem("NomItem")]` | Defineix el nom de cada element de la llista |
| `[XmlIgnore]` | Ignora la propietat durant la serialització |
| `[XmlText]` | Serialitza com a text dins l'element |

## Controlant el format de sortida

Per obtenir XML ben formatat (indentat):

```c#
using System.Xml;
using System.Xml.Serialization;

namespace SerializeXmlFormatted
{
    public class WeatherForecast
    {
        public DateTime Date { get; set; }
        public int TemperatureCelsius { get; set; }
        public string? Summary { get; set; }
    }

    public class Program
    {
        public static void Main()
        {
            var weatherForecast = new WeatherForecast
            {
                Date = DateTime.Parse("2019-08-01"),
                TemperatureCelsius = 25,
                Summary = "Hot"
            };

            var serializer = new XmlSerializer(typeof(WeatherForecast));
            
            var settings = new XmlWriterSettings
            {
                Indent = true,
                IndentChars = "  ",
                NewLineChars = "\n",
                NewLineHandling = NewLineHandling.Replace
            };
            
            using var stringWriter = new StringWriter();
            using var xmlWriter = XmlWriter.Create(stringWriter, settings);
            serializer.Serialize(xmlWriter, weatherForecast);
            
            Console.WriteLine(stringWriter.ToString());
        }
    }
}
```

## Exercicis

1. Serialitza a XML una estructura amb una llista de productes, on cada producte té nom, preu i categoria.

2. Crea una classe `Biblioteca` que contingui una llista de `Llibre` (amb títol, autor, any i disponible). Serialitza-la a XML usant atributs per a l'ISBN i elements per a la resta de propietats.

3. Compara el fitxer XML resultant amb el JSON equivalent. Quines diferències observes en l'estructura i mida?
