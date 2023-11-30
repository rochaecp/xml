# Elemento XSD anyAttribute

O elemento ```<anyAttribute>``` nos permite estender o documento XML com atributos não especificados pelo esquema.

O exemplo a seguir é um fragmento de um esquema XML chamado "family.xsd". Ele mostra uma declaração para o elemento "pessoa. Usando o elemento ```<anyAttribute>``` nós pode adicionar qualquer número de atributos ao elemento "person":

~~~xml
<xs:element name="person">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="firstname" type="xs:string"/>
            <xs:element name="lastname" type="xs:string"/>
        </xs:sequence>
        <xs:anyAttribute/>
    </xs:complexType>
</xs:element>
~~~

Agora queremos estender o elemento "person" com um atributo "eyecolor". Nisto caso possamos fazê-lo, mesmo que o autor do esquema acima nunca tenha declarado qualquer atributo "eyecolor".

Veja este arquivo de esquema, chamado "attribute.xsd":

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
targetNamespace="https://www.w3schools.com"
xmlns="https://www.w3schools.com"
elementFormDefault="qualified">

    <xs:attribute name="eyecolor">
        <xs:simpleType>
            <xs:restriction base="xs:string">
                <xs:pattern value="blue|brown|green|grey"/>
            </xs:restriction>
        </xs:simpleType>
    </xs:attribute>

</xs:schema>
~~~

O arquivo XML abaixo (chamado "Myfamily.xml"), usa componentes de dois esquemas diferentes; "family.xsd" e "attribute.xsd":

~~~xml
<?xml version="1.0" encoding="UTF-8"?>

<persons xmlns="http://www.microsoft.com"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:SchemaLocation="http://www.microsoft.com family.xsd
https://www.w3schools.com attribute.xsd">

    <person eyecolor="green">
        <firstname>Hege</firstname>
        <lastname>Refsnes</lastname>
    </person>

    <person eyecolor="blue">
        <firstname>Stale</firstname>
        <lastname>Refsnes</lastname>
    </person>

</persons>
~~~

O arquivo XML acima é válido porque o esquema "family.xsd" nos permite adicione um atributo ao elemento "pessoa.

Os elementos ```<any>``` e ```<anyAttribute>``` são usados para tornar EXTENSIBLE documentos! Eles permitem que os documentos contenham elementos adicionais que não são declarado no esquema XML principal.