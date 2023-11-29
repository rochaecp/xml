# XML e XPath

## O que é XPath?

- XPath é um elemento importante no padrão XSLT.
- XPath pode ser usado para navegar por elementos e atributos em um documento XML.
- XPath é uma sintaxe para definir partes de um documento XML.
- XPath usa expressões de caminho para navegar em documentos XML.
- XPath contém uma biblioteca de funções padrão.
- XPath é um elemento importante no XSLT e no XQuery.
- XPath é uma recomendação do W3C.

## Expressões do Caminho XPath

O XPath usa expressões de caminho para selecionar nós ou conjuntos de nós em um documento XML. Esse caminho as expressões se parecem muito com as expressões que você vê quando trabalha com um sistema de arquivos de computador tradicional.

As expressões XPath podem ser usadas em JavaScript, Java, XML Schema, PHP, Python, etc, C e C++, e muitas outras línguas.

## XPath é usado em XSLT

- XPath é um elemento importante no padrão XSLT.
- Com conhecimento XPath você será capaz de tirar grande vantagem de XSL.

## Exemplo

~~~xml
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
        <title lang="en">XQuery Kick Start</title>
        <author>James McGovern</author>
        <author>Per Bothner</author>
        <author>Kurt Cagle</author>
        <author>James Linn</author>
        <author>Vaidyanathan Nagarajan</author>
        <year>2003</year>
        <price>49.99</price>
    </book>
    <book category="web">
        <title lang="en">Learning XML</title>
        <author>Erik T. Ray</author>
        <year>2003</year>
        <price>39.95</price>
    </book>
</bookstore>
~~~

- ´´´/bookstore/book[1]´´´: Seleciona o primeiro elemento book que é filho do elemento bookstore
- ´´´/bookstore/book[last()]´´´: Seleciona o último elemento book que é filho do elemento bookstore
- ´´´/bookstore/book[last()-1]´´´: Seleciona o penúltimo elemento book que é filho do elemento bookstore
- ´´´/bookstore/book[position()<3]´´´: Seleciona os dois primeiros elementos book que são filhos do elemento bookstore
- ´´´//title[@lang]´´´: Seleciona todos os elementos do título que possuem um atributo chamado lang
- ´´´//title[@lang='en']´´´: Seleciona todos os elementos do título que possuem um atributo "lang" com valor "en"
- ´´´/bookstore/book[price>35.00]´´´: Seleciona todos os elementos livro do elemento livraria que possuem um elemento preço com valor maior que 35,00
- ´´´/bookstore/book[price>35.00]/title´´´: Seleciona todos os elementos title dos elementos book do elemento bookstore que possuem um elemento price com valor maior que 35,00

