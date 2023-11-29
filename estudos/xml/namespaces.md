# Namespaces

- XML Namespaces fornece um método para evitar conflitos de nome de elemento.
- Conflitos de Nome:
    - Em XML, os nomes dos elementos são definidos pelo desenvolvedor. Isso geralmente resulta em um conflito ao tentar misturar documentos XML de diferentes aplicativos XML.
    - Conflitos de nome em XML podem ser facilmente evitados usando um prefixo de nome. 

## Exemplo: conflitos de nome

Este fragmento de xml:

~~~xml
<table>
    <tr>
        <td>Apples</td>
        <td>Bananas</td>
    </tr>
</table>
~~~

estaria em conflito com este (caso eles fossem adicionados num mesmo xml)

~~~xml
<table>
    <name>African Coffee Table</name>
    <width>80</width>
    <length>120</length>
</table>
~~~

## Exemplo: resolvendo conflitos de nome usando um prefixo

Aqui não haverá conflito porque os dois elementos <table> têm nomes diferentes.

~~~xml
<h:table>
    <h:tr>
        <h:td>Apples</h:td>
        <h:td>Bananas</h:td>
    </h:tr>
</h:table>

<f:table>
    <f:name>African Coffee Table</f:name>
    <f:width>80</f:width>
    <f:length>120</f:length>
</f:table>
~~~

## XML Namespaces - O atributo xmlns

- Ao usar prefixos em XML, um namespace para o prefixo deve ser definido.
- O namespace pode ser definido por um xmlns atributo na tag inicial de um elemento.
- A declaração do namespace possui a seguinte sintaxe. xmlns:prefixo="URI".

~~~xml
<root>
    <h:table xmlns:h="http://www.w3.org/TR/html4/">
        <h:tr>
            <h:td>Apples</h:td>
            <h:td>Bananas</h:td>
        </h:tr>
    </h:table>
    <f:table xmlns:f="https://www.w3schools.com/furniture">
        <f:name>African Coffee Table</f:name>
        <f:width>80</f:width>
        <f:length>120</f:length>
    </f:table>
</root>
~~~

- O atributo xmlns no primeiro elemento < table > fornece ao prefixo h: um namespace qualificado.
- O atributo xmlns no segundo elemento < table > fornece ao prefixo f: um namespace qualificado.
- Quando um namespace é definido para um elemento, todos os elementos filhos com o mesmo prefixo são associados ao mesmo namespace.

Os namespaces também podem ser declarados no elemento raiz XML:

~~~xml
<root xmlns:h="http://www.w3.org/TR/html4/" xmlns:f="https://www.w3schools.com/furniture">
    <h:table>
        <h:tr>
            <h:td>Apples</h:td>
            <h:td>Bananas</h:td>
        </h:tr>
    </h:table>
    <f:table>
        <f:name>African Coffee Table</f:name>
        <f:width>80</f:width>
        <f:length>120</f:length>
    </f:table>
</root>
~~~

- A URI do namespace não é usado pelo analisador para procurar informações.
- O objetivo de usar um URI é dar ao espaço para nome um nome exclusivo.
- No entanto, as empresas costumam usar o namespace como um ponteiro para um página da web contendo informações sobre o namespace.

# Identificador uniforme de recursos (URI)

- O Identificador Uniforme de Recursos (URI) é uma cadeia de caracteres que identifica um Recurso Internet.
- O URI mais comum é o Localizador Uniforme de Recursos (URL) que identifica um endereço de domínio da Internet. 
- Outro tipo não tão comum de URI é o Nome Uniforme do Recurso (URNA).

# Espaços de nomes padrão

- A definição de um namespace padrão para um elemento nos impede de usar prefixos em todos os elementos filhos. 
- Tem a seguinte sintaxe: ```xmlns="namespaceURI"```

~~~xml
<table xmlns="http://www.w3.org/TR/html4/">
    <tr>
        <td>Apples</td>
        <td>Bananas</td>
    </tr>
</table>

<table xmlns="https://www.w3schools.com/furniture">
    <name>African Coffee Table</name>
    <width>80</width>
    <length>120</length>
</table>
~~~

## Espaços de Nomes em Uso Real

- O XSLT é uma linguagem que pode ser usada para transformar documentos XML em outros formatos.
- O documento XML abaixo é um documento usado para transformar XML em HTML.
- O espaço para nome "http://www.w3.org/1999/XSL/Transform" identifica XSLT elementos dentro de um documento HTML.

~~~xml
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:template match="/">
        <html>
            <body>
                <h2>My CD Collection</h2>
                <table border="1">
                    <tr>
                        <th style="text-align:left">Title</th>
                        <th style="text-align:left">Artist</th>
                    </tr>
                    <xsl:for-each select="catalog/cd">
                        <tr>
                            <td>
                                <xsl:value-of select="title"/>
                            </td>
                            <td>
                                <xsl:value-of select="artist"/>
                            </td>
                        </tr>
                    </xsl:for-each>
                </table>
            </body>
        </html>
    </xsl:template>
</xsl:stylesheet>
~~~