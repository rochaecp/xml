# Elemento XSD Substitution 

Com XML Schemas, um elemento pode substituir outro elemento.

Digamos que temos usuários de dois países diferentes: Inglaterra e Noruega. Gostaríamos da capacidade de deixar o usuário escolher se ele ou ela gostaria de usar os nomes dos elementos noruegueses ou os nomes dos elementos ingleses em o documento XML.

Para resolver esse problema, poderíamos definir um grupo Substituição no XML esquema. Primeiro, declaramos um elemento principal e, em seguida, declaramos os outros elementos que afirmam que eles são substituíveis pelo elemento da cabeça.

~~~xml
<xs:element name="name" type="xs:string"/>
<xs:element name="navn" substitutionGroup="name"/>
~~~

No exemplo acima, o elemento "name" é o elemento head e o "navn" elemento é substituível por "nome".

Veja este fragmento de um esquema XML:

~~~xml
<xs:element name="name" type="xs:string"/>
<xs:element name="navn" substitutionGroup="name"/>

<xs:complexType name="custinfo">
    <xs:sequence>
        <xs:element ref="name"/>
    </xs:sequence>
</xs:complexType>

<xs:element name="customer" type="custinfo"/>
<xs:element name="kunde" substitutionGroup="customer"/>
~~~

Um documento XML válido (de acordo com o esquema acima) pode ser assim:

~~~xml
<customer>
    <name>John Smith</name>
</customer>
~~~

ou assim:

~~~xml
<kunde>
    <navn>John Smith</navn>
</kunde>
~~~

## Substituição de Elemento de Bloqueio

Para impedir que outros elementos substituam por um elemento especificado, use o atributo block:

~~~xml
<xs:element name="name" type="xs:string" block="substitution"/>
~~~

Veja este fragmento de um esquema XML:

~~~xml
<xs:element name="name" type="xs:string" block="substitution"/>
<xs:element name="navn" substitutionGroup="name"/>

<xs:complexType name="custinfo">
    <xs:sequence>
        <xs:element ref="name"/>
    </xs:sequence>
</xs:complexType>

<xs:element name="customer" type="custinfo" block="substitution"/>
<xs:element name="kunde" substitutionGroup="customer"/>
~~~

Um documento XML válido (de acordo com o esquema acima) é assim:

~~~xml
<customer>
    <name>John Smith</name>
</customer>
~~~

MAS ISTO NÃO É MAIS VÁLIDO:

~~~xml
<kunde>
    <navn>John Smith</navn>
</kunde>
~~~

## Usando o substituctionGroup

O tipo de elementos substituíveis deve ser o mesmo que, ou derivado de, o tipo do elemento da cabeça. Se o tipo do elemento substituível é o mesmo que o tipo do elemento head, você não precisará especificar o tipo de o elemento substituível.

Observe que todos os elementos no grupo de substituição (o elemento head e o elementos substituíveis) devem ser declarados como elementos globais, caso contrário, serão não funciona!

## O que são Elementos Globais?

Elementos globais são elementos que são filhos imediatos do "esquema" elemento! Elementos locais são elementos aninhados dentro de outros elementos.