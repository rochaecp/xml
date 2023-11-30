# XSD Conteúdo Misto

Um elemento de tipo complexo misto pode conter atributos, elementos e texto.

Um elemento XML, "letra", que contém texto e outros elementos:

~~~xml
<letter>
    Dear Mr. <name>John Smith</name>.
    Your order <orderid>1032</orderid>
    will be shipped on <shipdate>2001-07-13</shipdate>.
</letter>
~~~

O esquema a seguir declara o elemento "letter":

~~~xml
<xs:element name="letter">
    <xs:complexType mixed="true">
        <xs:sequence>
            <xs:element name="name" type="xs:string"/>
            <xs:element name="orderid" type="xs:positiveInteger"/>
            <xs:element name="shipdate" type="xs:date"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
~~~

Nota: Para permitir que os dados de caracteres apareçam entre os elementos filhos de "letter", o atributo mixed deve ser definido como "true". A tag ```<xs:sequence>``` significa que os elementos definidos (nome, ordem e data de envio) devem aparecer nessa ordem dentro de um elemento "letter".

Também poderíamos dar um nome ao elemento complexType e deixar o elemento "letter" tem um atributo type que se refere ao nome do complexType (se você usar neste método, vários elementos podem se referir ao mesmo tipo complexo):

~~~xml
<xs:element name="letter" type="lettertype"/>

<xs:complexType name="lettertype" mixed="true">
    <xs:sequence>
        <xs:element name="name" type="xs:string"/>
        <xs:element name="orderid" type="xs:positiveInteger"/>
        <xs:element name="shipdate" type="xs:date"/>
    </xs:sequence>
</xs:complexType>
~~~