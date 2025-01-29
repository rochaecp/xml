# Elementos XSD Vazios

Um elemento complexo vazio não pode ter conteúdo, apenas atributos.

Um elemento XML vazio:

```<product prodid="1345" />```

O elemento "product" acima não tem nenhum conteúdo. Para definir um tipo sem conteúdo, devemos definir um tipo que permita elementos em seu conteúdo, mas nós realmente não declaramos quaisquer elementos, como este:

~~~xml
<xs:element name="product">
    <xs:complexType>
        <xs:complexContent>
            <xs:restriction base="xs:integer">
                <xs:attribute name="prodid" type="xs:positiveInteger"/>
            </xs:restriction>
        </xs:complexContent>
    </xs:complexType>
</xs:element>
~~~

No exemplo acima, definimos um tipo complexo com um conteúdo complexo. O elemento complexContent sinaliza que pretendemos restringir ou estenda o modelo de conteúdo de um tipo complexo, e a restrição de inteiro declara um atributo, mas não introduz nenhum conteúdo de elemento.

No entanto, é possível declarar o elemento "produto" de forma mais compacta, assim:

~~~xml
<xs:element name="product">
    <xs:complexType>
        <xs:attribute name="prodid" type="xs:positiveInteger"/>
    </xs:complexType>
</xs:element>
~~~

Ou você pode dar um nome ao elemento complexType e deixar o elemento "product" tem um atributo type que se refere ao nome do complexType (se você usar neste método, vários elementos podem se referir ao mesmo tipo complexo):

~~~xml
<xs:element name="product" type="prodtype"/>

<xs:complexType name="prodtype">
    <xs:attribute name="prodid" type="xs:positiveInteger"/>
</xs:complexType>
~~~