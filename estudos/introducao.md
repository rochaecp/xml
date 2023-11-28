# Introdução

- XML = eXtensible Markup Language = Linguagem de Marcação Extensível.
- O XML foi projetado para armazenar e transportar dados.
- O XML foi projetado para ser legível por humanos e máquinas.
- O XML é frequentemente usado para distribuir dados pela Internet.
- O XML é uma linguagem de marcação muito parecida com HTML.
- O XML foi projetado para armazenar e transportar dados.
- O XML foi projetado para ser auto-descritivo.
- O XML é uma recomendação do W3C.
- O XML Não Faz Nada. O XML é apenas informação envolta em tags.
- Alguém deve escrever um software para enviar, receber, armazenar ou exibi-lo.
- Diferenças para o HTML:
    - O XML foi projetado para transportar dados.
    - O HTML foi projetado para exibir dados.
    - As tags XML não são predefinidas como as tags HTML.
    - Em muitas aplicações HTML, XML é usado para armazenar ou transportar dados, enquanto o HTML é usado para formatar e exibir os dados os mesmos dados.
- O XML é Extensível. 
- O XML armazena dados em formato de texto sem formatação.
- O XML tornou-se uma recomendação do W3C em fevereiro de 1998.    
- O XML não contém nenhuma informação sobre como ser exibido.

# Padrões XML importantes

- XML AJAX
- DOM XML
- XML XPath
- XML XSLT
- XML XQuery
- DTD XML
- Esquema XML
- Serviços XML

# Exemplo: notes.xml

~~~xml
<note>
    <to>Tove</to>
    <from>Jani</from>
    <heading>Reminder</heading>
    <body>Don't forget me this weekend!</body>
</note>
~~~

# Árvore XML

- Os documentos XML formam uma estrutura de árvore que começa na "raiz" e se ramifica para "as folhas".

# Exemplo: bookstore.xml

![Árvore do XML](https://www.w3schools.com/xml/nodetree.gif)

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<bookstore>
  <book category="cooking">
    <title lang="en">Everyday Italian</title>
    <author>Giada De Laurentiis</author>
    <year>2005</year>
    <price>30.00</price>
  </book>
  <book category="children">
    <title lang="en">Harry Potter</title>
    <author>J K. Rowling</author>
    <year>2005</year>
    <price>29.99</price>
  </book>
  <book category="web">
    <title lang="en">Learning XML</title>
    <author>Erik T. Ray</author>
    <year>2003</year>
    <price>39.95</price>
  </book>
</bookstore>
~~~

