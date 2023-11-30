# XSD Indicadores

Podemos controlar como os elementos devem ser usados em documentos com indicadores.

Existem sete indicadores:

- Indicadores de ordem:
    - All
    - Choice
    - Sequence
- Indicadores de ocorrência:
    - maxOccurs
    - minOccurs
- Indicadores de grupo:
    - Group name
    - attributeGroup name

## Indicadores de Ordem

Indicadores de ordem são usados para definir a ordem dos elementos.

#### All

O indicador ```<all>``` especifica que os elementos filhos podem aparecer em **qualquer ordem** e que cada elemento filho deve ocorrer **apenas uma vez**:

~~~xml
<xs:element name="person">
    <xs:complexType>
        <xs:all>
            <xs:element name="firstname" type="xs:string"/>
            <xs:element name="lastname" type="xs:string"/>
        </xs:all>
    </xs:complexType>
</xs:element>
~~~

Nota: Ao usar o indicador ```<all>```, você pode definir o ``<minOccurs>`` o indicador para 0 ou 1 e o indicador ```<maxOccurs>``` só podem ser definidos como 1 ( o ```<minOccurs>``` e ```<maxOccurs>``` são descritos mais tarde).

#### Choice

O indicador ```<choice>``` especifica que um elemento filho **ou** outro pode ocorrer:

~~~xml
<xs:element name="person">
    <xs:complexType>
        <xs:choice>
            <xs:element name="employee" type="employee"/>
            <xs:element name="member" type="member"/>
        </xs:choice>
    </xs:complexType>
</xs:element>
~~~

#### Sequence

O indicador ```<sequence>``` especifica que os elementos filhos devem aparecer em uma ordem específica:

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

## Indicadores de Ocorrência

Os indicadores de ocorrência são usados para definir com que frequência um elemento pode ocorrer.

Nota: Para todos os indicadores "Ordem" e "Grupo" (any, all, choice, sequence, group name, and group reference) o valor padrão para maxOccurs e minOccurs é 1.

#### maxOccurs

O indicador ```<maxOccurs>``` especifica o número máximo de vezes que um elemento pode ocorrer:

~~~xml
<xs:element name="person">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="full_name" type="xs:string"/>
            <xs:element name="child_name" type="xs:string" maxOccurs="10"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
~~~

O exemplo acima indica que o elemento "child_name" pode ocorrer um mínimo de uma vez (o valor padrão para minOccurs é 1) e um máximo de dez vezes no elemento "person".

#### minOccurs

O indicador ```<minOccurs>``` especifica o número mínimo de vezes que um elemento pode ocorrer:

~~~xml
<xs:element name="person">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="full_name" type="xs:string"/>
            <xs:element name="child_name" type="xs:string" maxOccurs="10" minOccurs="0"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>
~~~

O exemplo acima indica que o elemento "child_name" pode ocorrer um mínimo de zero vezes e um máximo de dez vezes no elemento "pessoa.

Dica: Para permitir que um elemento apareça um número ilimitado de vezes, utilize o ```maxOccurs="unbounded"``` declaração:

#### Um exemplo de trabalho:

Um arquivo XML chamado "**Myfamily.xml**":

~~~xml
<?xml version="1.0" encoding="UTF-8"?>

<persons xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:noNamespaceSchemaLocation="family.xsd">

    <person>
        <full_name>Hege Refsnes</full_name>
        <child_name>Cecilie</child_name>
    </person>

    <person>
        <full_name>Tove Refsnes</full_name>
        <child_name>Hege</child_name>
        <child_name>Stale</child_name>
        <child_name>Jim</child_name>
        <child_name>Borge</child_name>
    </person>

    <person>
        <full_name>Stale Refsnes</full_name>
    </person>

</persons>
~~~

O arquivo XML acima contém um elemento raiz chamado "persons". Dentro este elemento raiz definimos três elementos "person". Cada elemento "person" deve conter um elemento "full_name" e pode conter até cinco elementos "child_name".

Aqui está o arquivo de esquema "**family.xsd**":

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
elementFormDefault="qualified">

    <xs:element name="persons">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="person" maxOccurs="unbounded">
                    <xs:complexType>
                        <xs:sequence>
                            <xs:element name="full_name" type="xs:string"/>
                            <xs:element name="child_name" type="xs:string" minOccurs="0" maxOccurs="5"/>
                        </xs:sequence>
                    </xs:complexType>
                </xs:element>
            </xs:sequence>
        </xs:complexType>
    </xs:element>

</xs:schema>
~~~

## Indicadores de Grupo

Indicadores de grupo são usados para definir conjuntos de elementos relacionados.

#### Group name

Os grupos de elementos são definidos com a declaração de grupo, assim:

~~~xml
<xs:group name="groupname">
...
</xs:group>
~~~

Você deve definir um elemento all, choice ou sequence dentro do grupo declaração. O exemplo a seguir define um grupo chamado "persongrupo", que define um grupo de elementos que devem ocorrer em uma sequência exata:

~~~xml
<xs:group name="persongroup">
    <xs:sequence>
        <xs:element name="firstname" type="xs:string"/>
        <xs:element name="lastname" type="xs:string"/>
        <xs:element name="birthday" type="xs:date"/>
    </xs:sequence>
</xs:group>
~~~

Depois de ter definido um grupo, você pode referenciá-lo em outra definição, como esta:

~~~xml
<xs:group name="persongroup">
    <xs:sequence>
        <xs:element name="firstname" type="xs:string"/>
        <xs:element name="lastname" type="xs:string"/>
        <xs:element name="birthday" type="xs:date"/>
    </xs:sequence>
</xs:group>

<xs:element name="person" type="personinfo"/>

<xs:complexType name="personinfo">
    <xs:sequence>
        <xs:group ref="persongroup"/>
        <xs:element name="country" type="xs:string"/>
    </xs:sequence>
</xs:complexType>
~~~

#### attributeGroup name

Os grupos de atributos são definidos com a declaração attributeGroup, assim:

~~~xml
<xs:attributeGroup name="groupname">
...
</xs:attributeGroup>
~~~

O exemplo a seguir define um grupo de atributos chamado "personattrgroup":

~~~xml
<xs:attributeGroup name="personattrgroup">
    <xs:attribute name="firstname" type="xs:string"/>
    <xs:attribute name="lastname" type="xs:string"/>
    <xs:attribute name="birthday" type="xs:date"/>
</xs:attributeGroup>
~~~

Depois de ter definido um grupo de atributos, você pode referenciá-lo em outra definição, como esta:

~~~xml
<xs:attributeGroup name="personattrgroup">
    <xs:attribute name="firstname" type="xs:string"/>
    <xs:attribute name="lastname" type="xs:string"/>
    <xs:attribute name="birthday" type="xs:date"/>
</xs:attributeGroup>

<xs:element name="person">
    <xs:complexType>
        <xs:attributeGroup ref="personattrgroup"/>
    </xs:complexType>
</xs:element>
~~~