# XML DOM

## O que é DOM?

- O Document Object Model (DOM) define um padrão para acessar e manipular documentos.
- "O W3C Document Object Model (DOM) é uma plataforma e uma interface neutra em termos de linguagem que permite que programas e scripts acessem e atualizem dinamicamente o conteúdo, estrutura e estilo de um documento."
- O DOM HTML define uma maneira padrão de acessar e manipular documentos HTML. Ele apresenta um documento HTML como uma estrutura de árvore.
- Entender o DOM é uma obrigação para qualquer pessoa que trabalhe com HTML ou XML.

## O HTML DOM

- Todos os elementos HTML podem ser acessados através do HTML DOM.

Este exemplo altera o valor de um elemento HTML com id="demo":

~~~html
<h1 id="demo">This is a Heading</h1>

<button type="button"
onclick="document.getElementById('demo').innerHTML = 'Hello World!'">Click Me!
</button>
~~~

## O XML DOM

- Todos os elementos XML podem ser acessados através do XML DOM.

Exemplo: Livros.xml

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
</bookstore>
~~~

Este código recupera o valor de texto do primeiro elemento <title> num Documento XML:

~~~javascript
txt = xmlDoc.getElementsByTagName("title")[0].childNodes[0].nodeValue;
~~~

- O XML DOM é um padrão para como obter, alterar, adicionar e excluir elementos XML.