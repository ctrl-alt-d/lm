# Examen de Llenguatge de Marques

## XML

Explica quin d'aquests dos XML creus que, des del punt de vista semàntic, està més ben estructurat.

```XML
<? xml version="1.0" encoding="UTF-8"?>
<company>
   <employee1>
      <name>John Doe</name>
      <position>Manager</position>
      <hired>2001</hired>
      <aficions><aficio>Tenis</aficio><<aficio>Running</aficio></aficions>
   </employee>
   <employee2>
      <name>Jane Smith</name>
      <position>Developer</position>
      <hired>2003</hired>
   </employee>
</company>
```

```XML
<? xml version="1.0" encoding="UTF-8"?>
<company>
   <employee id="1">
      <name>John Doe</name>
      <position>Manager</position>
      <hired>2001</hired>
      <aficions><aficio>Tenis</aficio><<aficio>Running</aficio></aficions>
   </employee>
   <employee id="2">
      <name>Jane Smith</name>
      <position>Developer</position>
      <hired>2003</hired>
   </employee>
</company>
```

## XML 2

Transcriu aquest YAML a XML

```yaml
usuari:
  nom: "Laura"
  edat: 28
  aficions:
    - lectura
    - muntanya
    - cuina
  adreça:
    ciutat: "Girona"
    codi_postal: 17001
```


## JSON 1

Codifica la informació de l'exercici 1 en un JSON

## JSON 2

Transcriu aquest YAML a JSON:

```yaml
usuari:
  nom: "Laura"
  edat: 28
  aficions:
    - lectura
    - muntanya
    - cuina
  adreça:
    ciutat: "Girona"
    codi_postal: 17001
```



## Markdown

Escriu aquest text en markdown, els textos no cal que els copiis complets.

Títol principal: XML
Subtítol: Què és XML?

El llenguatge de marques extensible (XML) permet definir i emmagatzemar dades de manera compartible. L’XML admet l’intercanvi d’informació entre sistemes informàtics, com ara llocs web, bases de dades i aplicacions de tercers. Les regles predefinides faciliten la transmissió de dades com a fitxers XML a través de qualsevol xarxa, ja que el destinatari pot utilitzar aquestes regles per llegir les dades de manera precisa i eficient.

Exemple:
```xml
<libro>
<título>Introducción a Amazon Web Services</título>
<autor>Mark Wilkins</autor>
</libro>
```

Subtítol: Comparativa amb altres llenguatges de marques

Taula resum:

| Aspecte | XML | JSON |
|----------|-----|------|
| Sintaxi | Etiquetes `<tag>` | Claus i valors `"clau": "valor"` |
| Llegibilitat | Més verbós | Més simple i lleuger |
| Tipus de dades | Tot text | Nombres, booleans, null, etc. |
| Comentaris | Sí (`<!-- -->`) | No |
| Validació | DTD/XSD | JSON Schema |
| Ús habitual | SOAP, configuracions antigues | APIs REST, dades web |
| Compatibilitat JS | Necessita processament | Natiu |


[-- fi de l'exercici --]

## CSV

Codifica les dades de l'exercici 1 en CSV, pot ser que necessitis més d'un fitxer CSV. Recorda afegir el camp `id`

## YAML

Un alumne està tocant el fitxer `netplan` que és el que configura la xarxa en Ubuntu, el sistama li diu que té un error. Quin és l'error?

```yaml
network:
      version: 2
    wifis:
        wl0:
            access-points:
                university:
                    auth:
                        key-management: eap
                        method: tls
                        ca-certificate: /etc/ssl/cust-cacrt.pem
                        client-certificate: /etc/ssl/cust-crt.pem
                        client-key: /etc/ssl/cust-key.pem
            dhcp4: yes
```

