# XSD Somente elementos

Um tipo complexo "**elements-only**" contém um elemento que contém apenas outros elementos.

## Tipos complexos contendo apenas elementos

Um elemento XML, "person", que contém apenas outros elementos:

~~~xml
<person>
    <firstname>John</firstname>
    <lastname>Smith</lastname>
</person>
~~~

Você pode definir o elemento "pessoa" em um esquema, assim:

~~~xml
<xs:element name="person">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="firstname" type="xs:string"/>
            <xs:element name="lastname" type="xs:string"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
~~~

Observe a tag ```<xs:sequence>```. Significa que os elementos definidos ("firstname" e "lastname") deve aparecer nessa ordem dentro de um elemento "pessoa.

Ou você pode dar um nome ao elemento complexType e deixar o elemento "person" tem um atributo type que se refere ao nome do complexType (se você usar neste método, vários elementos podem se referir ao mesmo tipo complexo):

~~~xml
<xs:element name="person" type="persontype"/>

<xs:complexType name="persontype">
    <xs:sequence>
        <xs:element name="firstname" type="xs:string"/>
        <xs:element name="lastname" type="xs:string"/>
    </xs:sequence>
</xs:complexType>
~~~