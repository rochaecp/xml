# XML Parser

- Todos os principais navegadores têm um analisador XML embutido para acessar e manipular XML.
- O XML DOM (Modelo de Objeto de Documento) define as propriedades e métodos de acesso e edição XML.
- No entanto, antes que um documento XML possa ser acessado, ele deve ser carregado em um objeto DOM XML.
- Todos os navegadores modernos têm um analisador XML integrado que pode converter texto em um objeto DOM XML.

## Exemplo: analisando uma cadeia de texto

- Este exemplo analisa uma cadeia de texto em um objeto DOM XML e extrai a informação com JavaScript

~~~html
<html>
<body>
    <p id="demo"></p>

    <script>
        var text, parser, xmlDoc;

        text = "<bookstore><book>" +
            "<title>Everyday Italian</title>" +
            "<author>Giada De Laurentiis</author>" +
            "<year>2005</year>" +
            "</book></bookstore>";

        // Um analisador XML DOM é criado:
        parser = new DOMParser();

        // O analisador cria um novo objeto DOM XML usando a cadeia de texto:
        xmlDoc = parser.parseFromString(text, "text/xml");

        document.getElementById("demo").innerHTML =
            xmlDoc.getElementsByTagName("title")[0].childNodes[0].nodeValue;
    </script>

</body>
</html>
~~~

## O Objeto XMLHttpRequest

- O Objeto XMLHttpRequest tem um parser XML embutido.
- O respostaTexto a propriedade retorna a resposta como uma string.
- O respostaXML a propriedade retorna a resposta como um objeto DOM XML.
- Se você quiser usar a resposta como um objeto DOM XML, você pode usar o responseXML propriedade.

~~~javascript
// exemplo que acessa um arquivo catalogo.xml
xmlDoc = xmlhttp.responseXML;
txt = "";
x = xmlDoc.getElementsByTagName("ARTIST");
for (i = 0; i < x.length; i++) {
    txt += x[i].childNodes[0].nodeValue + "<br>";
}
document.getElementById("demo").innerHTML = txt;
~~~

~~~xml
<CATALOG>
    <CD>
        <TITLE>Empire Burlesque</TITLE>
        <ARTIST>Bob Dylan</ARTIST>
        <COUNTRY>USA</COUNTRY>
        <COMPANY>Columbia</COMPANY>
        <PRICE>10.90</PRICE>
        <YEAR>1985</YEAR>
    </CD>
    <CD>
        <TITLE>Hide your heart</TITLE>
        <ARTIST>Bonnie Tyler</ARTIST>
        <COUNTRY>UK</COUNTRY>
        <COMPANY>CBS Records</COMPANY>
        <PRICE>9.90</PRICE>
        <YEAR>1988</YEAR>
    </CD>    
<CATALOG>
~~~