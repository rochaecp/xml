# XSLT - Transformações

- O elemento raiz que declara que o documento é uma folha de estilo XSL é

~~~xslt
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
<!-- xsl:stylesheet e xsl:transform são sinônimos -->
~~~

- Para obter acesso aos elementos, atributos e recursos do XSLT, devemos declarar o namespace XSLT na parte superior do documento.
- O xmlns:xsl="http://www.w3.org/1999/XSL/Transform" aponta para o namespace oficial do W3C XSLT. Se você usar isso namespace, você também deve incluir o atributo version="1.0".

## Exemplo

- Queremos transformar o documento XML meuArquivo.xml em um XHTML:

meuArquivo.xml:

~~~xml
<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="meuEstilo.xsl"?>
<livros>
    <livro>
        <titulo>A Arte da Guerra</titulo>
        <autor>Sun Tzu</autor>
    </livro>
    <livro>
        <titulo>1984</titulo>
        <autor>George Orwell</autor>
    </livro>
</livros>
~~~

meuEstilo.xsl: 

~~~xml
<?xml version="1.0"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:template match="/">
        <html>
            <body>
                <h2>Lista de Livros</h2>
                <table border="1">
                    <tr bgcolor="#9acd32">
                        <th>Título</th>
                        <th>Autor</th>
                    </tr>
                    <xsl:for-each select="livros/livro">
                        <tr>
                            <td>
                                <xsl:value-of select="titulo"/>
                            </td>
                            <td>
                                <xsl:value-of select="autor"/>
                            </td>
                        </tr>
                    </xsl:for-each>
                </table>
            </body>
        </html>
    </xsl:template>
</xsl:stylesheet>
~~~

Na pasta onde os arquivos meuArquivo.xml e meuEstilo.xsl estiverem é necessário rodar um servidor local. 
Podemos fazer isso com Python, com o comando: 

~~~python
python -m http.server
~~~

Após isso basta acessar a URL http://localhost:8000/meuArquivo.xml e visualizar o XML formatado pelo XSLT.