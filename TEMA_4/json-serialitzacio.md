# Serialització en JSON

Per fer aquesta pràctica el que farem serà crear una sèrie de classes c#, instanciar-les amb valors i, finalment, persistir l'estat d'aquests objectes a disc en un format de llenguatge de marques JSON

Usarem l'[exemple de Microsoft](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/how-to#serialization-examples) per a fer la pràctica:


```c#
using System.Text.Json;

namespace SerializeBasic
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
            var weatherForecast = new WeatherForecast
            {
                Date = DateTime.Parse("2019-08-01"),
                TemperatureCelsius = 25,
                Summary = "Hot"
            };

            string jsonString = JsonSerializer.Serialize(weatherForecast);

            Console.WriteLine(jsonString);
        }
    }
}
// output:
//{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot"}
```

Si ens fixem a l'exemple crea en memòria un objecte de tipus `WeatherForecast`, la transforma a JSON i la mostra per consola.

Per tal de **persistir-ho** a disc cal usar el segon exemple:

```c#
using System.Text.Json;

namespace SerializeToFile
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
            var weatherForecast = new WeatherForecast
            {
                Date = DateTime.Parse("2019-08-01"),
                TemperatureCelsius = 25,
                Summary = "Hot"
            };

            string fileName = "WeatherForecast.json"; 
            string jsonString = JsonSerializer.Serialize(weatherForecast);
            File.WriteAllText(fileName, jsonString);

            Console.WriteLine(File.ReadAllText(fileName));
        }
    }
}
// output:
//{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot"}
```

Busca el fitxer que s'ha creat al sistema de fitxers. Obra'l amb VSCode, amb el Navegador o amb alguna altra aplicació i contesta:
* Hi ha tota la informació de l'objecte?
* Té format? (És a dir, està indentat i és de bon llegit o bé no té format i està tot seguit)

Mira la [documentació de Microsoft](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/how-to#serialize-to-formatted-json) i mira de serialitzar amb format.


## Exercicis

* Prepara en memòria una estructura més complexa que no pas la que hem fet servir a l'exemple. Aquesta estructura contindrà llistes d'objectes i dicionaris. Serialitza la teva estructura.
