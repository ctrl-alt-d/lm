# Deserialització en XML

La deserialització XML és el procés de convertir dades XML en objectes C# en memòria.

## Deserialització bàsica

Usem `XmlSerializer` per deserialitzar XML a objectes:

```c#
using System.Xml.Serialization;

namespace DeserializeXmlBasic
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
            string xmlString = """
                <?xml version="1.0" encoding="utf-8"?>
                <WeatherForecast>
                    <Date>2019-08-01T00:00:00</Date>
                    <TemperatureCelsius>25</TemperatureCelsius>
                    <Summary>Hot</Summary>
                </WeatherForecast>
                """;

            var serializer = new XmlSerializer(typeof(WeatherForecast));
            
            using var stringReader = new StringReader(xmlString);
            var weatherForecast = serializer.Deserialize(stringReader) as WeatherForecast;

            Console.WriteLine($"Date: {weatherForecast?.Date}");
            Console.WriteLine($"TemperatureCelsius: {weatherForecast?.TemperatureCelsius}");
            Console.WriteLine($"Summary: {weatherForecast?.Summary}");
        }
    }
}
// output:
// Date: 01/08/2019 0:00:00
// TemperatureCelsius: 25
// Summary: Hot
```

## Deserialitzar des de fitxer

Per llegir XML des d'un fitxer a disc:

```c#
using System.Xml.Serialization;

namespace DeserializeXmlFromFile
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
            string fileName = "WeatherForecast.xml";
            var serializer = new XmlSerializer(typeof(WeatherForecast));
            
            using var fileStream = new FileStream(fileName, FileMode.Open);
            var weatherForecast = serializer.Deserialize(fileStream) as WeatherForecast;

            Console.WriteLine($"Date: {weatherForecast?.Date}");
            Console.WriteLine($"TemperatureCelsius: {weatherForecast?.TemperatureCelsius}");
            Console.WriteLine($"Summary: {weatherForecast?.Summary}");
        }
    }
}
```

## Estructures complexes amb llistes

Per deserialitzar XML amb llistes i estructures niades:

```c#
using System.Xml.Serialization;

namespace DeserializeXmlComplex
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
            string xmlString = """
                <?xml version="1.0" encoding="utf-8"?>
                <WeatherForecast>
                    <Date>2019-08-01T00:00:00</Date>
                    <TemperatureCelsius>25</TemperatureCelsius>
                    <Summary>Hot</Summary>
                    <DatesAvailable>
                        <Date>2019-08-01T00:00:00</Date>
                        <Date>2019-08-02T00:00:00</Date>
                    </DatesAvailable>
                    <TemperatureRanges>
                        <Range name="Cold">
                            <High>20</High>
                            <Low>-10</Low>
                        </Range>
                        <Range name="Hot">
                            <High>60</High>
                            <Low>20</Low>
                        </Range>
                    </TemperatureRanges>
                    <SummaryWords>
                        <Word>Cool</Word>
                        <Word>Windy</Word>
                        <Word>Humid</Word>
                    </SummaryWords>
                </WeatherForecast>
                """;

            var serializer = new XmlSerializer(typeof(WeatherForecast));
            
            using var stringReader = new StringReader(xmlString);
            var weatherForecast = serializer.Deserialize(stringReader) as WeatherForecast;

            Console.WriteLine($"Date: {weatherForecast?.Date}");
            Console.WriteLine($"TemperatureCelsius: {weatherForecast?.TemperatureCelsius}");
            Console.WriteLine($"Summary: {weatherForecast?.Summary}");
            
            Console.WriteLine("\nDates disponibles:");
            weatherForecast?.DatesAvailable?.ForEach(d => Console.WriteLine($"  - {d:yyyy-MM-dd}"));
            
            Console.WriteLine("\nRangs de temperatura:");
            weatherForecast?.TemperatureRanges?.ForEach(r => 
                Console.WriteLine($"  - {r.Name}: {r.Low}°C a {r.High}°C"));
            
            Console.WriteLine("\nParaules resum:");
            weatherForecast?.SummaryWords?.ForEach(w => Console.WriteLine($"  - {w}"));
        }
    }
}
```

## Gestió d'errors

És important gestionar els possibles errors de deserialització:

```c#
using System.Xml.Serialization;

namespace DeserializeXmlWithErrors
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
            string fileName = "WeatherForecast.xml";
            
            try
            {
                if (!File.Exists(fileName))
                {
                    Console.WriteLine($"Error: El fitxer '{fileName}' no existeix.");
                    return;
                }
                
                var serializer = new XmlSerializer(typeof(WeatherForecast));
                
                using var fileStream = new FileStream(fileName, FileMode.Open);
                var weatherForecast = serializer.Deserialize(fileStream) as WeatherForecast;
                
                if (weatherForecast is null)
                {
                    Console.WriteLine("Error: No s'ha pogut deserialitzar l'objecte.");
                    return;
                }

                Console.WriteLine($"Date: {weatherForecast.Date}");
                Console.WriteLine($"TemperatureCelsius: {weatherForecast.TemperatureCelsius}");
                Console.WriteLine($"Summary: {weatherForecast.Summary}");
            }
            catch (InvalidOperationException ex)
            {
                Console.WriteLine($"Error de deserialització: {ex.InnerException?.Message ?? ex.Message}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error inesperat: {ex.Message}");
            }
        }
    }
}
```

## Exercicis

1. Crea les classes C# necessàries per deserialitzar el següent XML i mostra la informació per consola:

```xml
<?xml version="1.0" encoding="utf-8"?>
<Factures>
    <Factura id="1">
        <Data>2024-01-15</Data>
        <Client>
            <IdClient>101</IdClient>
            <Nom>Empresa XYZ</Nom>
            <Adreca>Carrer Major, 123, Barcelona</Adreca>
        </Client>
        <Total>250.75</Total>
        <LiniesFactura>
            <Linia id="1">
                <Descripcio>Producte A</Descripcio>
                <Quantitat>2</Quantitat>
                <PreuUnitari>50.00</PreuUnitari>
                <TotalLinia>100.00</TotalLinia>
            </Linia>
            <Linia id="2">
                <Descripcio>Producte B</Descripcio>
                <Quantitat>3</Quantitat>
                <PreuUnitari>30.25</PreuUnitari>
                <TotalLinia>90.75</TotalLinia>
            </Linia>
            <Linia id="3">
                <Descripcio>Descompte especial</Descripcio>
                <Quantitat>1</Quantitat>
                <PreuUnitari>-10.00</PreuUnitari>
                <TotalLinia>-10.00</TotalLinia>
            </Linia>
        </LiniesFactura>
    </Factura>
    <Factura id="2">
        <Data>2024-01-20</Data>
        <Client>
            <IdClient>102</IdClient>
            <Nom>Client ABC</Nom>
            <Adreca>Avinguda Central, 45, Madrid</Adreca>
        </Client>
        <Total>180.00</Total>
        <LiniesFactura>
            <Linia id="1">
                <Descripcio>Servei de consultoria</Descripcio>
                <Quantitat>1</Quantitat>
                <PreuUnitari>150.00</PreuUnitari>
                <TotalLinia>150.00</TotalLinia>
            </Linia>
            <Linia id="2">
                <Descripcio>Producte C</Descripcio>
                <Quantitat>1</Quantitat>
                <PreuUnitari>30.00</PreuUnitari>
                <TotalLinia>30.00</TotalLinia>
            </Linia>
        </LiniesFactura>
    </Factura>
</Factures>
```

2. Modifica l'exercici anterior per llegir l'XML des d'un fitxer i afegir gestió d'errors adequada.

3. Compara les classes necessàries per deserialitzar JSON vs XML. Quines diferències observes en la definició de les classes?
