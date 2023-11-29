# Elementos

- Um elemento XML é tudo, desde (incluindo) a tag inicial do elemento até (incluindo) a tag final do elemento.
        - Exemplo: ```<price>29.99</price>```
- Um elemento XML pode conter:
    - texto
    - atributos
    - outros elementos
    - ou uma mistura dos itens acima
- Elemento vazio: 
    - Modo 1: ```<element></element>```     
    - Modo 2: ```<element />``` (tag de fechamento automático)
    - Elementos vazios podem ter atributos.

## Exemplo: bookstore.xml

~~~xml
<bookstore>
    <book category="children"> <!-- category é um atributo -->
        <title>Harry Potter</title> 
        <author>J K. Rowling</author>
        <year>2005</year>
        <price>29.99</price>
    </book>
    <book category="web">
        <title>Learning XML</title>
        <author>Erik T. Ray</author>
        <year>2003</year>
        <price>39.95</price>
    </book>
</bookstore>
~~~

## Regras de Nomeação para um elemento XML

- Os nomes dos elementos são sensíveis a maiúsculas.
- Os nomes dos elementos devem começar com uma letra ou sublinhado.
- Nomes de elementos não podem começar com as letras xml (ou XML, ou Xml, etc).
- Os nomes dos elementos podem conter letras, dígitos, hífens, sublinhados e períodos.
- Nomes de elementos não podem conter espaços.
- Qualquer nome pode ser usado, nenhuma palavra é reservada (exceto xml)
- Exemplos:
    - ```<person>```
    - ```<firstname>```
    - ```<book_title>```
- Evite "-", "." e ":" para separar duas palavras.
- ":" são reservados para namespaces.
- Escolha o seu estilo de nomeação, e seja consistente com ele.
- Documentos XML geralmente têm um banco de dados correspondente. Uma prática comum é usar as regras de nomeação do banco de dados para os elementos XML.

# Atributos

- Elementos XML podem ter atributos, assim como HTML.
- Os atributos são projetados para conter dados relacionados a um determinado elemento.
- Exemplos:
    - Modo 1: ```<person gender="female">```
    - Modo 2: ```<person gender='female'>```
    - ```<gangster name='George "Shotgun" Ziegler'>```
- Considerações sobre atributos:
    - atributos não podem conter vários valores (elementos podem)
    - atributos não podem conter estruturas de árvore (elementos podem)
    - atributos não são facilmente expansíveis ( para alterações futuras)

## Exemplos

- Não há regras sobre quando usar atributos ou quando usar elementos em XML. 
- Estes 2 exemplos dizem a mesma coisa: 

~~~xml
<person gender="female">
  <firstname>Anna</firstname>
  <lastname>Smith</lastname>
</person>
~~~

~~~xml
<person>
  <gender>female</gender>
  <firstname>Anna</firstname>
  <lastname>Smith</lastname>
</person>
~~~

- Evitar isto:

~~~xml
<note day="10" month="01" year="2008"
to="Tove" from="Jani" heading="Reminder"
body="Don't forget me this weekend!">
</note>
~~~

- As vezes utiliza-se atributos Id para identificar elementos (funcionam como metadados):

~~~xml
<messages>
  <note id="501">
    <to>Tove</to>
    <from>Jani</from>
    <heading>Reminder</heading>
    <body>Don't forget me this weekend!</body>
  </note>
  <note id="502">
    <to>Jani</to>
    <from>Tove</from>
    <heading>Re: Reminder</heading>
    <body>I will not</body>
  </note>
</messages>
~~~



