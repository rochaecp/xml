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

**meuArquivo.xml**:

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="meuEstilo.xsl"?> <!-- vinculando o xml ao meuEstilo.xsl -->
<livros>
    <livro>
        <titulo>O Livro dos Espíritos</titulo>
        <autor>Allan Kardec</autor>
        <ano>1857</ano>
    </livro>
    <livro>
        <titulo>Aprendendo Inteligência</titulo>
        <autor> Pierluigi Piazzi</autor>
        <ano>2007</ano>
    </livro>     
    <livro>
        <titulo>Missionários da Luz</titulo>
        <autor> Francisco Cândido Xavier</autor>
        <ano>1945</ano>
    </livro>
    <livro>
        <titulo>O Poder da Mente</titulo>
        <autor>Suely Caldas Schubert</autor>
        <ano>2020</ano>
    </livro>
</livros>
~~~

**meuEstilo.xsl**: 

~~~xml
<?xml version="1.0" encoding="UTF-8"?> <!-- o XSL sempre começa com essa linha, pois ele também é um documento xml -->
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"> <!-- define que o documento é um xslt -->
    <xsl:template match="/"> <!-- usado para definir um modelo (regra), o atributo match="/" define associa o modelo com a raiz do xml. '/' é um xPath -->
        <html> <!-- o conteúdo dentro de <xsl:template> define algum HTML para escrever na saída. -->
            <body>
                <h2>Lista de Livros</h2>
                <table border="1">
                    <tr bgcolor="#113366">
                        <th>Título</th>
                        <th>Autor</th>
                        <th>Ano</th>
                    </tr>
                    <xsl:for-each select="livros/livro">
                        <tr>
                            <td>
                                <xsl:value-of select="titulo"/> <!-- o elemento value-of extrai o valor de um nó selecionado pelo atributo select, que irá conter um XPath -->
                            </td>
                            <td>
                                <xsl:value-of select="autor"/>
                            </td>
                            <td>
                                <xsl:value-of select="ano"/>
                            </td>                            
                        </tr>
                    </xsl:for-each>
                </table>
            </body>
        </html>
    </xsl:template>
</xsl:stylesheet>            
~~~

> Quando você tenta carregar um arquivo XSLT local a partir de um arquivo XML local no navegador, o navegador pode bloquear essa ação devido a restrições de segurança.

Na pasta onde os arquivos meuArquivo.xml e meuEstilo.xsl estiverem é necessário rodar um servidor local. 

Podemos fazer isso com Python, com o comando: 

~~~python
python -m http.server
~~~

Após isso basta acessar a URL http://localhost:8000/meuArquivo.xml e visualizar o XML formatado pelo XSLT.

# Exemplo mais completo

Utilizando o mesmo xml **meuArquivo.xml** do exemplo anterior vamos criar um novo **meuEstilo.xsl**:

~~~xml
<?xml version="1.0" encoding="UTF-8"?> 
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"> 
    <xsl:template match="/"> 
        <html> 
            <body>
                <h2>Lista de Livros</h2>
                <table border="1">
                    <tr bgcolor="#113366">
                        <th>Título</th>
                        <th>Autor</th>
                        <th>Ano</th>
                    </tr>
                    <xsl:for-each select="livros/livro[ano > 1900]"> <!-- utilizando o xpath para filtrar por ano -->
                        <xsl:sort select="ano"/> <!-- ordena por ano -->
                        <xsl:if test="titulo != 'O Poder da Mente'"> <!-- elemento if -->
                            <tr>
                                <xsl:choose>
                                    <xsl:when test="titulo = 'Missionários da Luz'">
                                        <td bgcolor="purple"><xsl:value-of select="titulo"/></td>
                                    </xsl:when>
                                    <xsl:otherwise>
                                        <td><xsl:value-of select="titulo"/></td>
                                    </xsl:otherwise>
                                </xsl:choose>
                                <td><xsl:value-of select="autor"/></td>
                                <td><xsl:value-of select="ano"/></td>                            
                            </tr>
                        </xsl:if>
                    </xsl:for-each>
                </table>
            </body>
        </html>
    </xsl:template>
</xsl:stylesheet>  
~~~