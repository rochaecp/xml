# Elementos Complexos XSD

Um elemento complexo contém outros elementos e/ou atributos.

O que é um Elemento Complexo?
Um elemento complexo é um elemento XML que contém outros elementos e/ou atributos.

Existem quatro tipos de elementos complexos:

elementos vazios
elementos que contêm apenas outros elementos
elementos que contêm apenas texto
elementos que contêm ambos os outros elementos e texto
Nota: Cada um desses elementos pode conter atributos também!

Exemplos de Elementos Complexos
Um elemento XML complexo, "produto", que está vazio:

<product pid="1345"/>
Um elemento XML complexo, "empregado", que contém apenas outros elementos:

<employee>
  <firstname>John</firstname>
  <lastname>Smith</lastname>
</employee>
Um elemento XML complexo, "comida", que contém apenas texto:

<food type="dessert">Ice cream</food>
Um elemento XML complexo, "descrição", que contém elementos e texto:

<description>
It happened on <date lang="norwegian">03.03.99</date> ....
</description>
Como Definir um Elemento Complexo
Olhe para este elemento XML complexo, "empregado", que contém apenas outros elementos:

<employee>
  <firstname>John</firstname>
  <lastname>Smith</lastname>
</employee>
Podemos definir um elemento complexo em um esquema XML de duas maneiras diferentes:

1. O elemento "empregado" pode ser declarado diretamente nomeando o elemento, assim:

<xs:element name="employee">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="firstname" type="xs:string"/>
      <xs:element name="lastname" type="xs:string"/>
    </xs:sequence>
  </xs:complexType>
</xs:element>
Se você usar o método descrito acima, somente o elemento "empregado" poderá usar o tipo complexo especificado. Observe que os elementos filho, "primeiro nome" e "último nome", estão cercados pelo indicador <sequence>. Isso significa que os elementos filho devem aparecer em a mesma ordem em que são declarados. Você aprenderá mais sobre indicadores no capítulo Indicadores XSD.

2. O elemento "empregado" pode ter um atributo type que se refere ao nome do tipo complexo a ser usado:

<xs:element name="employee" type="personinfo"/>

<xs:complexType name="personinfo">
  <xs:sequence>
    <xs:element name="firstname" type="xs:string"/>
    <xs:element name="lastname" type="xs:string"/>
  </xs:sequence>
</xs:complexType>
Se você usar o método descrito acima, vários elementos podem se referir ao mesmo tipo complexo, como este:

<xs:element name="employee" type="personinfo"/>
<xs:element name="student" type="personinfo"/>
<xs:element name="member" type="personinfo"/>

<xs:complexType name="personinfo">
  <xs:sequence>
    <xs:element name="firstname" type="xs:string"/>
    <xs:element name="lastname" type="xs:string"/>
  </xs:sequence>
</xs:complexType>
Você também pode basear um tipo complexo em um tipo complexo existente e adicionar alguns elementos, como este:

<xs:element name="employee" type="fullpersoninfo"/>

<xs:complexType name="personinfo">
  <xs:sequence>
    <xs:element name="firstname" type="xs:string"/>
    <xs:element name="lastname" type="xs:string"/>
  </xs:sequence>
</xs:complexType>

<xs:complexType name="fullpersoninfo">
  <xs:complexContent>
    <xs:extension base="personinfo">
      <xs:sequence>
        <xs:element name="address" type="xs:string"/>
        <xs:element name="city" type="xs:string"/>
        <xs:element name="country" type="xs:string"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>