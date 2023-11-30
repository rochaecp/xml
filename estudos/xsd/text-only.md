# Elementos XSD text-only

Um elemento complexo text-only pode conter texto e atributos.

Este tipo contém apenas conteúdo simples (texto e atributos), portanto, nós adicione um elemento **simpleContent** ao redor do conteúdo. Ao usar conteúdo simples, você deve definir uma extensão OR uma restrição dentro do elemento **simpleContent**, assim:

~~~xml
<xs:element name="somename">
    <xs:complexType>
        <xs:simpleContent>
            <xs:extension base="basetype">
                ....
                ....
            </xs:extension>
        </xs:simpleContent>
    </xs:complexType>
</xs:element>

OR

<xs:element name="somename">
    <xs:complexType>
        <xs:simpleContent>
            <xs:restriction base="basetype">
                ....
                ....
            </xs:restriction>
        </xs:simpleContent>
    </xs:complexType>
</xs:element>
~~~

> Dica: Use o elemento de extensão/restrição para expandir ou limitar o tipo simples de base para o elemento.

Aqui está um exemplo de um elemento XML, "shoesize", que contém apenas texto:

~~~xml
<shoesize country="france">35</shoesize>
~~~

O exemplo a seguir declara um complexType, "shoesize". O conteúdo é definido como um o valor inteiro e o elemento "shoesize" também contém um atributo chamado "country":

~~~xml
<xs:element name="shoesize">
    <xs:complexType>
        <xs:simpleContent>
            <xs:extension base="xs:integer">
                <xs:attribute name="country" type="xs:string" />
            </xs:extension>
        </xs:simpleContent>
    </xs:complexType>
</xs:element>
~~~

Também poderíamos dar um nome ao elemento complexType e deixar o elemento "shoesize tem um atributo type que se refere ao nome do complexType (se você usar neste método, vários elementos podem se referir ao mesmo tipo complexo):

~~~xml
<xs:element name="shoesize" type="shoetype"/>

<xs:complexType name="shoetype">
    <xs:simpleContent>
        <xs:extension base="xs:integer">
            <xs:attribute name="country" type="xs:string" />
        </xs:extension>
    </xs:simpleContent>
</xs:complexType>
~~~