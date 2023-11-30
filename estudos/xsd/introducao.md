# Introdução

## O que é um esquema XML?

- Um esquema XML descreve a estrutura de um documento XML.
- A linguagem **XML Schema** também é conhecida como **XML Schema Definition (XSD)**.

## Exemplo

~~~xml
<?xml version="1.0"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

    <xs:element name="note">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="to" type="xs:string"/>
                <xs:element name="from" type="xs:string"/>
                <xs:element name="heading" type="xs:string"/>
                <xs:element name="body" type="xs:string"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>

</xs:schema>
~~~

- O objetivo de um esquema XML é definir os blocos de construção legais de um XML
    - os elementos e atributos que podem aparecer em um documento
    - o número (e a ordem dos) elementos filhos
    - tipos de dados para elementos e atributos
    - valores padrão e fixos para elementos e atributos
- O XML Schema é uma alternativa baseada em XML (e mais poderosa) ao DTD.    

## Características

- Uma das maiores forças dos esquemas XML é o suporte para tipos de dados.
    - É mais fácil descrever o conteúdo permitido do documento
    - É mais fácil validar a correção dos dados
    - É mais fácil definir facetas de dados (restrições de dados)
    - É mais fácil definir padrões de dados (formatos de dados)
    - É mais fácil converter dados entre diferentes tipos de dados
- Outra grande força sobre esquemas XML é que eles são escritos em XML.
    - Você não precisa aprender um novo idioma
    - Você pode usar seu editor XML para editar seus arquivos Schema
    - Você pode usar seu analisador XML para analisar seus arquivos Schema
    - Você pode manipular seu Schema com o XML DOM
    - Você pode transformar seu Schema com XSLT    
- Esquemas XML são extensíveis, porque eles são escritos em XML.  
- Com uma definição de esquema extensível, você pode:
    - Reutilize seu Esquema em outros Esquemas
    - Crie seus próprios tipos de dados derivados dos tipos padrão
    - Referência a vários esquemas no mesmo documento 

## Comunicação Segura de Dados

- Ao enviar dados de um remetente para um receptor, é essencial que ambas as partes tenha as mesmas "expectativas" sobre o conteúdo.
- Com XML Schemas, o remetente pode descrever os dados de uma forma que o receptor vai entender.
- Uma data como: "03-11-2004" será, em alguns países, interpretada como 3.Novembro e em outros países como 11.Março.
- No entanto, um elemento XML com um tipo de dados assim: ```<date type="date">2004-03-11</date>``` garante uma compreensão mútua do conteúdo, porque o tipo de dados XML "date" requer o formato "AAAA-MM-DD".

## Bem formado não é suficiente

- Um documento XML bem formado é um documento que está em conformidade com a sintaxe XML regras, como:
    - deve começar com a declaração XML
    - deve ter um elemento raiz exclusivo
    - tags de início devem ter tags de extremidade correspondentes
    - elementos diferenciam maiúsculas de minúsculas
    - todos os elementos devem ser fechados
    - todos os elementos devem estar devidamente aninhados
    - todos os valores de atributo devem ser citados
    - entidades devem ser usadas para caracteres especiais
- Mesmo que os documentos sejam bem formados, eles ainda podem conter erros, e esses erros podem ter sérias conseqüências.
- Pense na seguinte situação: você pede 5 impressoras a laser, em vez de 5 a laser impressoras. Com XML Schemas, a maioria desses erros pode ser capturada pelo seu validação de software.

## Exemplo

- Os documentos XML podem ter uma referência a um DTD ou a um esquema XML.

Veja este documento XML simples chamado "**note.xml**":

~~~xml
<?xml version="1.0"?>
<note>
    <to>Tove</to>
    <from>Jani</from>
    <heading>Reminder</heading>
    <body>Don't forget me this weekend!</body>
</note>
~~~

O exemplo a seguir é um arquivo DTD chamado "**note.dtd**" que define os elementos do documento XML acima ("note.xml"):
- A primeira linha define o elemento nota para ter quatro elementos filhos: "para, de, cabeçalho, corpo".
- A linha 2-5 define os elementos to, from, heading, body para serem do tipo "#PCDATA".

~~~xml
<!ELEMENT note (to, from, heading, body)>
<!ELEMENT to (#PCDATA)>
<!ELEMENT from (#PCDATA)>
<!ELEMENT heading (#PCDATA)>
<!ELEMENT body (#PCDATA)>
~~~

O exemplo a seguir é um arquivo XML Schema chamado "**note.xsd**" que define os elementos do XML documento acima ("note.xml"):
- O elemento nota é um tipo complexo porque contém outros elementos. 
- Os outros elementos (para, de, cabeçalho, corpo) são tipos simples porque eles não contém outros elementos. 

~~~xml
<?xml version="1.0"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
targetNamespace="https://www.w3schools.com"
xmlns="https://www.w3schools.com"
elementFormDefault="qualified">

    <xs:element name="note">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="to" type="xs:string"/>
                <xs:element name="from" type="xs:string"/>
                <xs:element name="heading" type="xs:string"/>
                <xs:element name="body" type="xs:string"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>

</xs:schema>
~~~

Uma referência a um esquema XML
- Este documento XML tem uma referência a um esquema XML:

~~~xml
<?xml version="1.0"?>
<note
xmlns="https://www.w3schools.com"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="https://www.w3schools.com/xml note.xsd">
    <to>Tove</to>
    <from>Jani</from>
    <heading>Reminder</heading>
    <body>Don't forget me this weekend!</body>
</note>
~~~