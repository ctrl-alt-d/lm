# Deserialització en JSON

Deserialitzar és el procés contrari a serialitzar. De manera ideal, podem tenir les classes c# preparades per deserialitzar un JSON. Quan el deserialitzem haurem d'informar al deserialitzador de quina és la classe que deserialitzem.

Treballem amb la [documentació de Microsoft de deserialització](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/deserialization#examples):

```c#
using System.Text.Json;

namespace DeserializeExtra
{
    public class WeatherForecast
    {
        public DateTimeOffset Date { get; set; }
        public int TemperatureCelsius { get; set; }
        public string? Summary { get; set; }
        public string? SummaryField;
        public IList<DateTimeOffset>? DatesAvailable { get; set; }
        public Dictionary<string, HighLowTemps>? TemperatureRanges { get; set; }
        public string[]? SummaryWords { get; set; }
    }

    public class HighLowTemps
    {
        public int High { get; set; }
        public int Low { get; set; }
    }

    public class Program
    {
        public static void Main()
        {
            string jsonString =
                """
                {
                  "Date": "2019-08-01T00:00:00-07:00",
                  "TemperatureCelsius": 25,
                  "Summary": "Hot",
                  "DatesAvailable": [
                    "2019-08-01T00:00:00-07:00",
                    "2019-08-02T00:00:00-07:00"
                  ],
                  "TemperatureRanges": {
                                "Cold": {
                                    "High": 20,
                      "Low": -10
                                },
                    "Hot": {
                                    "High": 60,
                      "Low": 20
                    }
                            },
                  "SummaryWords": [
                    "Cool",
                    "Windy",
                    "Humid"
                  ]
                }
                """;
                
            WeatherForecast? weatherForecast = 
                JsonSerializer.Deserialize<WeatherForecast>(jsonString);

            Console.WriteLine($"Date: {weatherForecast?.Date}");
            Console.WriteLine($"TemperatureCelsius: {weatherForecast?.TemperatureCelsius}");
            Console.WriteLine($"Summary: {weatherForecast?.Summary}");
        }
    }
}
// output:
//Date: 8/1/2019 12:00:00 AM -07:00
//TemperatureCelsius: 25
//Summary: Hot
```

A l'exemple es veu com deserialitzem un `string` i obtenim un objecte. En aquesta línia es veu com informem al deserialitzador del tipus de dades que estem deserialitzant: `JsonSerializer.Deserialize<WeatherForecast>(jsonString)`

Nosaltre volem deserialitzar JSON que estiguin persistits a disc. Llavors, observem el segon exemple, on podem veure com primer llegeix el JSON de disc:

```c#
using System.Text.Json;

namespace DeserializeFromFile
{
    public class WeatherForecast
    {
        public DateTimeOffset Date { get; set; }
        public int TemperatureCelsius { get; set; }
        public string? Summary { get; set; }
    }

    public class Program
    {
        public static void Main()
        {
            string fileName = "WeatherForecast.json";
            string jsonString = File.ReadAllText(fileName);
            WeatherForecast weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString)!;

            Console.WriteLine($"Date: {weatherForecast.Date}");
            Console.WriteLine($"TemperatureCelsius: {weatherForecast.TemperatureCelsius}");
            Console.WriteLine($"Summary: {weatherForecast.Summary}");
        }
    }
}
// output:
//Date: 8/1/2019 12:00:00 AM -07:00
//TemperatureCelsius: 25
//Summary: Hot
```

## Exercicis

* Crea les classes c# per deserialitzar el següent JSON i deserialitza'l:

```json
{
  "factures": [
    {
      "id_factura": 1,
      "data": "2024-01-15",
      "client": {
        "id_client": 101,
        "nom": "Empresa XYZ",
        "adreça": "Carrer Major, 123, Barcelona"
      },
      "total": 250.75,
      "linies_factura": [
        {
          "id_linia": 1,
          "descripcio": "Producte A",
          "quantitat": 2,
          "preu_unitari": 50.00,
          "total_linia": 100.00
        },
        {
          "id_linia": 2,
          "descripcio": "Producte B",
          "quantitat": 3,
          "preu_unitari": 30.25,
          "total_linia": 90.75
        },
        {
          "id_linia": 3,
          "descripcio": "Descompte especial",
          "quantitat": 1,
          "preu_unitari": -10.00,
          "total_linia": -10.00
        }
      ]
    },
    {
      "id_factura": 2,
      "data": "2024-01-20",
      "client": {
        "id_client": 102,
        "nom": "Client ABC",
        "adreça": "Avinguda Central, 45, Madrid"
      },
      "total": 180.00,
      "linies_factura": [
        {
          "id_linia": 1,
          "descripcio": "Servei de consultoria",
          "quantitat": 1,
          "preu_unitari": 150.00,
          "total_linia": 150.00
        },
        {
          "id_linia": 2,
          "descripcio": "Producte C",
          "quantitat": 1,
          "preu_unitari": 30.00,
          "total_linia": 30.00
        }
      ]
    }
  ]
}
```
