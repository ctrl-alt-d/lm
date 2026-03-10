# Validacions

Les validacions en un llenguatge de marques són processos que comproven que un document segueix unes regles predefinides sobre la seva estructura i el tipus de dades que conté. Cal distingir entre:

- Document ben format: el document respecta la sintaxi bàsica del llenguatge (per exemple, un XML ben format té etiquetes tancades correctament, una estructura jeràrquica vàlida i una declaració d'encodificació si cal). Ser ben format és la condició mínima perquè un parser pugui llegir el document.
- Document validat (respecte d'un esquema): a més de ser ben format, el document compleix amb una descripció formal (esquema) que defineix elements, atributs, tipus de dades, restriccions i relacions (per exemple, XSD per a XML o JSON Schema per a JSON). La validació garanteix que la informació s'ajusta a les regles esperades per una aplicació o servei.

Validar documents és important per assegurar interoperabilitat, detectar errors de modelatge de dades i protegir processos d'intercanvi d'informació contra entrades incorrectes.


## XML

XML (Extensible Markup Language) és un llenguatge de marques per representar dades estructurades en text. Per validar documents XML s'utilitzen principalment esquemes com ara XSD (XML Schema Definition) i, en alguns casos més antics, DTD (Document Type Definition). L'esquema defineix els elements acceptats, l'ordre i repeticions (seqüències, minOccurs/maxOccurs), els tipus de dades (xs:string, xs:int, xs:date, etc.), atributs i restriccions (rangs, enumeracions).

La validació d'un XML contra un XSD es fa carregant l'esquema i comprovant que cada node i valor del document compleix les regles definides. Això permet detectar errors semàntics (p. ex. un camp obligatori absent, un número fora de rang) que no serien captats només comprovant si el document és ben format.

* [Conceptes validació XML](./xuletaxml.md)
* [Exemple validació XML amb C#](./dotnet_xml.md)
* [Generar XSD amb XmlSchemaExporter](./dotnet_GetXmlSchema.md)

## JSON

JSON (JavaScript Object Notation) és un format lleuger per a l'intercanvi de dades. Per validar JSON s'utilitzen esquemes com JSON Schema, que defineix l'estructura esperada: propietats, tipus (`string`, `integer`, `array`, `object`), restriccions de valors (`minimum`, `maximum`, `pattern`), propietats obligatòries (`required`) i altres regles composables (allOf, anyOf, oneOf, not).

La validació amb JSON Schema s'executa comparant l'objecte JSON amb l'esquema; les eines de validació retornen errors detallats quan alguna propietat no compleix les regles. Això facilita la robustesa en APIs, la verificació de dades d'entrada i la generació automàtica de documents de prova.

* [Conceptes validació JSON](./xuletajson.md)
* [Exemple validació JSON amb C#](./dotnet_json.md)
* [Generar JSON Schema amb GetJsonSchemaAsNode](./dotnet_GetJsonSchemaAsNode.md)

# Avaluació

* [Avaluació](./avaluació.md)
* **RA4.** Estableix mecanismes de validació de documents per a l'intercanvi d'informació utilitzant mètodes per definir-ne la sintaxi i l'estructura.
   * 4.1. Estableix la necessitat de descriure la informació transmesa als * documents i les seves regles.
   * 4.2. Identifica les tecnologies relacionades amb la definició de * documents.
   * 4.3. Analitza l'estructura i la sintaxi específica utilitzada en la * descripció.
   * 4.4. Crea descripcions de documents.
   * 4.5. Utilitza descripcions en l'elaboració i la validació de documents.
   * 4.6. Associa les descripcions amb els documents.
   * 4.7. Utilitza eines específiques de validació.
* Continguts: **Definició d'esquemes i vocabularis en llenguatges de marques**
   * 4.1. Tecnologies per a la definició de documents. Estructura i sintaxi.
   * 4.2. Creació de descripcions de documents.
   * 4.3. Associació de descripcions amb documents. Validació.
   * 4.4. Eines de creació i validació.