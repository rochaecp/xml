# Restrições XSD

- Restrições são usadas para definir valores aceitáveis para elementos ou atributos XML. Restrições em elementos XML são chamadas de facetas.

## Restrições aos Valores

O exemplo a seguir define um elemento chamado "idade" com uma restrição. O valor da idade não pode ser inferior a 0 ou superior a 120:

~~~xml
<xs:element name="age">
    <xs:simpleType>
        <xs:restriction base="xs:integer">
            <xs:minInclusive value="0"/>
            <xs:maxInclusive value="120"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

## Restrições a um Conjunto de Valores

- Para limitar o conteúdo de um elemento XML a um conjunto de valores aceitáveis, usaríamos a restrição de enumeração.

O exemplo abaixo define um elemento chamado "carro" com uma restrição. Os únicos valores aceitáveis são: Audi, Golf, BMW:

~~~xml
<xs:element name="car">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:enumeration value="Audi"/>
            <xs:enumeration value="Golf"/>
            <xs:enumeration value="BMW"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

O exemplo acima também poderia ter sido escrito assim:

~~~xml
<xs:element name="car" type="carType"/>

<xs:simpleType name="carType">
    <xs:restriction base="xs:string">
        <xs:enumeration value="Audi"/>
        <xs:enumeration value="Golf"/>
        <xs:enumeration value="BMW"/>
    </xs:restriction>
</xs:simpleType>
~~~

Nota: Neste caso, o tipo "carType" pode ser usado por outros elementos porque não faz parte do elemento "carro.

## Restrições a uma Série de Valores

- Para limitar o conteúdo de um elemento XML para definir uma série de números ou letras que podem ser usadas, nós usaríamos a restrição de padrão.
- O exemplo abaixo define um elemento chamado "letra" com uma restrição. O único valor aceitável é UMA das letras MINÚSCULAS de a a z:

~~~xml
<xs:element name="letter">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:pattern value="[a-z]"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

O próximo exemplo define um elemento chamado "iniciais" com uma restrição. O único valor aceitável é TRÊS das letras MAIÚSCULAS de a a z:

~~~xml
<xs:element name="initials">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:pattern value="[A-Z][A-Z][A-Z]"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

O próximo exemplo também define um elemento chamado "iniciais" com um restrição. O único valor aceitável é TRÊS da MINÚSCULA OU MAIÚSCULA letras de a a z:

~~~xml
<xs:element name="initials">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:pattern value="[a-zA-Z][a-zA-Z][a-zA-Z]"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

O próximo exemplo define um elemento chamado "escolha" com uma restrição. O único valor aceitável é UMA das seguintes letras: x, y, OR z:

~~~xml
<xs:element name="choice">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:pattern value="[xyz]"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

O próximo exemplo define um elemento chamado "prodid" com um restrição. O único valor aceitável é CINCO dígitos em uma sequência, e cada um o dígito deve estar em um intervalo de 0 a 9:

~~~xml
<xs:element name="prodid">
    <xs:simpleType>
        <xs:restriction base="xs:integer">
            <xs:pattern value="[0-9][0-9][0-9][0-9][0-9]"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

## Outras Restrições a uma Série de Valores

O exemplo abaixo define um elemento chamado "letra" com um restrição. O valor aceitável é zero ou mais ocorrências de letras minúsculas de a a z:

~~~xml
<xs:element name="letter">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:pattern value="([a-z])*"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

O próximo exemplo também define um elemento chamado "letra" com um restrição. O valor aceitável é um ou mais pares de letras, cada par consistindo de uma letra minúscula seguida de uma letra maiúscula. Por exemplo, "sToP" será validado por este padrão, mas não "Stop" ou "STOP" ou "stop":

~~~xml
<xs:element name="letter">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:pattern value="([a-z][A-Z])+"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

O próximo exemplo define um elemento chamado "gênero" com uma restrição. O único valor aceitável é masculino OU feminino:

~~~xml
<xs:element name="gender">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:pattern value="male|female"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

O próximo exemplo define um elemento chamado "senha" com um restrição. Deve haver exatamente oito caracteres seguidos e esses os caracteres devem ser letras minúsculas ou maiúsculas de a a z, ou um número de 0 a 9:

~~~xml
<xs:element name="password">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:pattern value="[a-zA-Z0-9]{8}"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

## Restrições em Caracteres de Espaço em Branco

- Para especificar como os caracteres de espaço em branco devem ser manipulados, usaremos a restrição whiteSpace.

Este exemplo define um elemento chamado "endereço" com um restrição. A restrição whiteSpace é definida como "preservar", o que significa que o processador XML NÃO IRÁ remover quaisquer caracteres de espaço em branco:

~~~xml
<xs:element name="address">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:whiteSpace value="preserve"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

Este exemplo também define um elemento chamado "endereço" com um restrição. A restrição whiteSpace é definida como "substituir", o que significa que o Processador XML SUBSTITUIRÁ todos os caracteres de espaço em branco (alimentações de linha, guias, espaços, etc, e retornos de carruagem) com espaços:

~~~xml
<xs:element name="address">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:whiteSpace value="replace"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

Este exemplo também define um elemento chamado "endereço" com um restrição. A restrição whiteSpace é definida como "colapso", o que significa que o processador XML IRÁ REMOVER todos os caracteres de espaço em branco (alimentações de linha, guias, espaços, devoluções de carruagem são substituídos por espaços, espaços principais e trailing são removidos e vários espaços são reduzidos a um único espaço):

~~~xml
<xs:element name="address">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:whiteSpace value="collapse"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

## Restrições de Comprimento

- Para limitar o comprimento de um valor em um elemento, usaríamos as restrições length, maxLength e minLength.

Este exemplo define um elemento chamado "senha" com uma restrição. O valor deve ser exatamente oito caracteres:

~~~xml
<xs:element name="password">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:length value="8"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

Este exemplo define outro elemento chamado "senha" com um restrição. O valor deve ser mínimo de cinco caracteres e máximo de oito personagens:

~~~xml
<xs:element name="password">
    <xs:simpleType>
        <xs:restriction base="xs:string">
            <xs:minLength value="5"/>
            <xs:maxLength value="8"/>
        </xs:restriction>
    </xs:simpleType>
</xs:element>
~~~

Restrições para Datatypes

- **enumeração**: Define uma lista de valores aceitáveis
- **fracçãoDigits**: Especifica o número máximo de casas decimais permitidas. Deve ser igual ou maior que zero
- **length**: Especifica o número exato de caracteres ou itens de lista permitidos. Deve ser igual ou maior que zero
- **maxExclusive**: Especifica os limites superiores para valores numéricos (o valor deve ser menor que este valor)
- **maxInclusive**: Especifica os limites superiores para valores numéricos (o valor deve ser menor ou igual a este valor)
- **maxLength**: Especifica o número máximo de caracteres ou itens de lista permitidos. Deve ser igual ou maior que zero
- **minExclusive**: Especifica os limites inferiores para valores numéricos (o valor deve ser maior que este valor)
- **minInclusive**: Especifica os limites inferiores para valores numéricos (o valor deve ser maior ou igual a este valor)
- **minLength**: Especifica o número mínimo de caracteres ou itens de lista permitidos. Deve ser igual ou maior que zero
**pattern**: Define a sequência exata de caracteres que são aceitáveis
- **totalDigits**: Especifica o número exato de dígitos permitidos. Deve ser maior que zero
- **whiteSpace**: Especifica como o espaço em branco (alimentação de linha, tabulações, espaços e retornos de carro) é tratado
