## Conceptes bàsics de XML

XML (Extensible Markup Language) és un llenguatge de marques dissenyat per emmagatzemar i transportar dades de manera estructurada. A continuació es detallen alguns dels conceptes bàsics d'XML, en particular l'ús de `<`, `</`, `>` i altres elements.

### 1. **Elements**
Els elements en XML estan delimitats per etiquetes d'obertura i tancament, on l'etiqueta d'obertura és `<element>` i l'etiqueta de tancament és `</element>`. Un element pot contenir dades o altres elements.

**Exemple d'un element:**
```xml
<nom>Pit de pollastre</nom>
```

En aquest exemple, `nom` és l'element que conté el valor `Pit de pollastre`.

### 2. **Atributs**
Els elements poden tenir atributs que proporcionen informació addicional. Els atributs es defineixen dins de l'etiqueta d'obertura i tenen el format clau-valor.

**Exemple d'un element amb atributs:**

```xml
<llibre idioma="català">El Petit Príncep</llibre>
```

En aquest exemple, `idioma` és un atribut amb el valor `català`, i l'element conté el text `El Petit Príncep`.

### 3. **Estructura en arbre**
XML té una estructura jeràrquica en forma d'arbre, on un element pot contenir altres elements "fills". Aquesta estructura és autodescriptiva, ja que cada element descriu el tipus de dades que conté.

**Exemple d'una estructura en arbre:**

```xml
<llibreria>
  <llibre>
    <titol>El Petit Príncep</titol>
    <autor>Antoine de Saint-Exupéry</autor>
    <any>1943</any>
  </llibre>
</llibreria>
```

En aquest exemple:
- `llibreria` és l'element "pare".
- `llibre` és un element "fill" de `llibreria`.
- Els elements `titol`, `autor` i `any` són fills de `llibre`.

### 4. **Regles sintàctiques**
- Tots els elements han de tenir una etiqueta d'obertura i una de tancament (`<element></element>`).
- Els noms dels elements són sensibles a majúscules i minúscules (`<Nom>` és diferent de `<nom>`).
- Els atributs han d'anar entre cometes dobles.
- Un document XML ha de tenir un únic element arrel (l'element que conté tots els altres elements).

---

**Exemple complet d'un document XML:**
```xml
<llibreria>
  <llibre isbn="3423423432">
    <titol>El Petit Príncep</titol>
    <autor>Antoine de Saint-Exupéry</autor>
    <any>1943</any>
  </llibre>
  <llibre isbn="343432888">
    <titol>1984</titol>
    <autor>George Orwell</autor>
    <any>1949</any>
  </llibre>
</llibreria>
```

En aquest exemple:
- `llibreria` és l'element arrel que conté dos elements `llibre`.
- Cada element `llibre` conté informació sobre un llibre, incloent el titol, l'autor i l'any de publicació.

Amb aquests conceptes, pots estructurar i gestionar informació utilitzant XML de manera organitzada i clara.

### 5 . Aplicacions

### On usem XML?

XML (Extensible Markup Language) és un llenguatge de marques utilitzat principalment per emmagatzemar, transmetre i estructurar dades de manera llegible tant per humans com per màquines. A continuació es mostren alguns exemples comuns d’on s’utilitza XML:

- **Intercanvi de dades entre aplicacions**: Moltes aplicacions utilitzen XML per intercanviar dades en formats estructurats. Per exemple, els serveis web sovint usen XML per enviar respostes i sol·licituds.
  
  **Exemple**: Un servei web pot retornar una resposta en format XML.
  
  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <resposta>
    <estat>èxit</estat>
    <codi>200</codi>
    <missatge>Sol·licitud completada correctament</missatge>
  </resposta>
```

- **Fitxers de configuració**: XML és utilitzat per guardar configuracions de programari o aplicacions, perquè permet una estructura clara i jeràrquica de les dades.

  **Exemple**: Un fitxer de configuració per a una aplicació web.
  
```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <configuració>
    <baseDeDades>
      <servidor>localhost</servidor>
      <usuari>admin</usuari>
      <contrasenya>12345</contrasenya>
    </baseDeDades>
  </configuració>
```

- **Emmagatzematge de dades en documents**: Aplicacions com Microsoft Office o LibreOffice utilitzen XML per desar documents en formats com DOCX, XLSX o ODT, els quals són paquets ZIP amb fitxers XML a dins.

  **Exemple**: Part d’un document de text en format DOCX.
  
```xml
  <w:document>
    <w:body>
      <w:p>
        <w:r>
          <w:t>Hola món!</w:t>
        </w:r>
      </w:p>
    </w:body>
  </w:document>
```

- **Formatació de dades**: XML també és utilitzat en alguns llenguatges per organitzar i formatar dades, com per exemple, en RSS (Really Simple Syndication), que permet distribuir contingut d'un lloc web.

  **Exemple**: Un canal RSS.
  
```xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <rss version="2.0">
    <channel>
      <title>Últimes notícies</title>
      <link>https://noticies.example.com</link>
      <description>Les notícies més recents</description>
      <item>
        <title>Notícia 1</title>
        <link>https://noticies.example.com/noticia1</link>
        <description>Detalls de la notícia 1</description>
      </item>
    </channel>
  </rss>
```

### Aplicacions on s’utilitza XML

- **Android**: Els fitxers de disseny d'interfícies d’usuari (UI) en Android estan escrits en XML.
- **Microsoft Office i OpenOffice**: Els documents (com DOCX, XLSX, ODT) estan basats en XML.
- **Servidors web**: Configuracions i respostes de serveis web sovint utilitzen XML.
- **Sistemes RSS**: Distribució de notícies i continguts d'un lloc web a través de canals RSS.

  


## Pràctica: Creació i validació d'un document XML

Objectiu: Aprendre a estructurar informació en un document XML i validar que la sintàxi és correcte.


Es vol emmagatzemar informació sobre libres en un document xml. La informació a emmagatzemar és.

* Títol, ISBN i categoria
* Autor
* Any de publicació
* Gènere

Un exemple d'xml és aquest:

```xml
<llibreria>
  <llibre isbn="3423423432" categoria="aventures">
    <titol>El Petit Príncep</titol>
    <autor>Antoine de Saint-Exupéry</autor>
    <any>1943</any>
  </llibre>
  <llibre isbn="343432888" categoria="distopies">
    <titol>1984</titol>
    <autor>George Orwell</autor>
    <any>1949</any>
  </llibre>
</llibreria>
```

Fes ara tu un fitxer xml que contingui informació sobre menjars:

* **Nom** i **categoria** (Exemple: Pit de pollastre, categoria carn)
* **Kilocalories** per 100 grams (Ex: 100)
* **Proteines** per 100 grams (Ex: 20)
* **Greixos** per 100 grams (Ex: 10)

Comprova que el teu document té un format correcte, per exemple a [XMLValidation](https://www.xmlvalidation.com/)

__Nota: si veus que es correcte, prova errors per tal que sigui incorrecte i vegis com el validador t'avisa que no és correcte__

### Versió d'XML

El fragment `<?xml version="1.0" encoding="utf-8"?>` és una declaració XML que indica la versió i la codificació utilitzada en el document XML.

- **`version="1.0"`**: especifica que el document segueix l'estàndard XML 1.0.
- **`encoding="utf-8"`**: indica que la codificació de caràcters del document és UTF-8, una codificació que permet representar una gran varietat de caràcters internacionals.

Aquesta declaració és opcional, però recomanable per assegurar la correcta interpretació del document. Es posa a la primera línia del document:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<llibres>
  <llibre>
    <títol>El petit príncep</títol>
    <autor>Antoine de Saint-Exupéry</autor>
    <any>1943</any>
  </llibre>
</llibres>
```


