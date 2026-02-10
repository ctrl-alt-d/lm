# Xuleta de Sintaxi de Validació XSD

## Exemple d'un XML senzill que compleix amb un XSD

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Persones xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="persones.xsd">
    <Persona>
        <Nom>Anna</Nom>
        <Edat>30</Edat>
    </Persona>
    <Persona>
        <Nom>Pere</Nom>
        <Edat>25</Edat>
    </Persona>
</Persones>
```

## Exemple de fitxer XSD corresponent

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

    <xs:element name="Persones">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="Persona" maxOccurs="unbounded">
                    <xs:complexType>
                        <xs:sequence>
                            <xs:element name="Nom" type="xs:string"/>
                            <xs:element name="Edat" type="xs:int"/>
                        </xs:sequence>
                    </xs:complexType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
    </xs:element>

</xs:schema>
```

## Elements Bàsics en XSD

### Definir un element simple
```xml
<xs:element name="Nom" type="xs:string"/>
```

### Definir un element complex
```xml
<xs:element name="Persona">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="Nom" type="xs:string"/>
            <xs:element name="Edat" type="xs:int"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
```

### Tipus de dades bàsics en XSD
- `xs:string` → Cadena de text
- `xs:int` → Enter
- `xs:decimal` → Número decimal
- `xs:boolean` → Cert o fals (`true` / `false`)
- `xs:date` → Data en format `YYYY-MM-DD`
- `xs:time` → Hora en format `HH:MM:SS`
- `xs:dateTime` → Data i hora combinades

### Definir atributs en elements
```xml
<xs:element name="Persona">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="Nom" type="xs:string"/>
        </xs:sequence>
        <xs:attribute name="id" type="xs:int" use="required"/>
    </xs:complexType>
</xs:element>
```

### Restriccions de valors
```xml
<xs:element name="Edat">
    <xs:simpleType>
        <xs:restriction base="xs:int">
            <xs:minInclusive value="0"/>
            <xs:maxInclusive value="120"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
```

### Enumeracions (valors predefinits)
```xml
<xs:element name="Color">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:enumeration value="Vermell"/>
            <xs:enumeration value="Verd"/>
            <xs:enumeration value="Blau"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
```

### Definir un element opcional o amb múltiples ocurrències
- Opcional (`minOccurs="0"`)
- Repetit (`maxOccurs="unbounded"`)

```xml
<xs:element name="Persona" minOccurs="0" maxOccurs="unbounded">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="Nom" type="xs:string"/>
            <xs:element name="Edat" type="xs:int"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
```

