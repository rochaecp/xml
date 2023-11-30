# Elemento XSD any

O elemento ```<any>``` permite-nos estender o documento XML com elementos não especificados pelo esquema.

O exemplo a seguir é um fragmento de um esquema XML chamado "family.xsd". Mostra uma declaração para o elemento "person". Usando o elemento ```<any>``` pode estender (após ```<lastname>```) o conteúdo de "person" com qualquer elemento:

~~~xml
<xs:element name="person">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="firstname" type="xs:string"/>
            <xs:element name="lastname" type="xs:string"/>
            <xs:any minOccurs="0"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
~~~

Agora queremos estender o elemento "person" com um elemento "children". Nisto caso possamos fazê-lo, mesmo que o autor do esquema acima nunca tenha declarado nenhum elemento "children".

Veja este arquivo de esquema, chamado "children.xsd":

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
targetNamespace="https://www.w3schools.com"
xmlns="https://www.w3schools.com"
elementFormDefault="qualified">

    <xs:element name="children">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="childname" type="xs:string"
                maxOccurs="unbounded"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>

</xs:schema>
~~~

O arquivo XML abaixo (chamado "Myfamily.xml"), usa componentes de dois esquemas diferentes; "family.xsd" e "children.xsd":

~~~xml
<?xml version="1.0" encoding="UTF-8"?>

<persons xmlns="http://www.microsoft.com"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.microsoft.com family.xsd
https://www.w3schools.com children.xsd">

    <person>
        <firstname>Hege</firstname>
        <lastname>Refsnes</lastname>
        <children>
            <childname>Cecilie</childname>
        </children>
    </person>

    <person>
        <firstname>Stale</firstname>
        <lastname>Refsnes</lastname>
    </person>

</persons>
~~~

O arquivo XML acima é válido porque o esquema "family.xsd" nos permite estenda o elemento "person" com um elemento opcional após o "lastname" elemento.

Os elementos ```<any>``` e ```<anyAttribute>``` são usados para tornar EXTENSIBLE documentos! Eles permitem que os documentos contenham elementos adicionais que não são declarado no esquema XML principal.