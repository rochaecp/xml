# Elemento XSD schema

- O elemento ```<schema>``` é o elemento raiz de cada esquema XML.

~~~xml
<?xml version="1.0"?>

<xs:schema>
...
...
</xs:schema>
~~~

- O elemento ```<schema>``` pode conter alguns atributos. 

Uma declaração de esquema geralmente se parece com isso:

~~~xml
<?xml version="1.0"?>

<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
targetNamespace="https://www.w3schools.com"
xmlns="https://www.w3schools.com"
elementFormDefault="qualified">
...
...
</xs:schema>
~~~

O fragmento ```xmlns:xs="http://www.w3.org/2001/XMLSchema" ``` indica que os elementos e tipos de dados utilizados no esquema provêm do "http://www.w3.org/2001/XMLSchema" namespace. Também especifica que os elementos e tipos de dados que vêm do namespace "http://www.w3.org/2001/XMLSchema" devem ser prefixados com xs:

Este fragmento: ```targetNamespace="https://www.w3schools.com"``` indica que os elementos definidos por este esquema (nota, para, de, cabeçalho, corpo.) vêm do "https://www.w3schools.com" namespace.

Este fragmento: ```xmlns="https://www.w3schools.com"``` indica que o namespace padrão é "https://www.w3schools.com".

Este fragmento: ```elementFormDefault="qualified"``` indica que quaisquer elementos usados pelo documento de instância XML que foram declarado neste esquema deve ser namespace qualificado.

## Referenciando um Esquema em um Documento XML

Este documento XML tem uma referência a um esquema XML:

~~~xml
<?xml version="1.0"?>

<note xmlns="https://www.w3schools.com"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="https://www.w3schools.com note.xsd">

<to>Tove</to>
<from>Jani</from>
<heading>Reminder</heading>
<body>Don't forget me this weekend!</body>
</note>
~~~

O seguinte fragmento: ```xmlns="https://www.w3schools.com"``` especifica a declaração de namespace padrão. Esta declaração diz ao validador de esquema em que todos os elementos usados neste documento XML são declarados o namespace "https://www.w3schools.com".

Depois de ter o namespace XML Schema Instance disponível: ```xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"``` você pode usar o atributo schemaLocation. Este atributo tem dois valores, separados por um espaço. O primeiro valor é o namespace a ser usado. O segundo valor é a localização do esquema XML a ser usado para esse namespace: ```xsi:schemaLocation="https://www.w3schools.com note.xsd"```