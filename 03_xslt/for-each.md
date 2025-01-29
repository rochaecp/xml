# Elemento XSLT for-each

- O elemento ```<xsl:for-each>``` pode ser usado para selecionar cada elemento XML de um conjunto de nós especificado:

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

    <xsl:template match="/">
        <html>
        <body>
        <h2>My CD Collection</h2>
        <table border="1">
            <tr bgcolor="#9acd32">
                <th>Title</th>
                <th>Artist</th>
            </tr>
            <xsl:for-each select="catalog/cd">
                <tr>
                    <td><xsl:value-of select="title"/></td>
                    <td><xsl:value-of select="artist"/></td>
                </tr>
            </xsl:for-each>
        </table>
        </body>
        </html>
    </xsl:template>

</xsl:stylesheet>
~~~

O valor do atributo select é uma expressão XPath. Uma expressão XPath funciona como navegar em um sistema de arquivos; onde uma barra direta (/) seleciona subdiretórios.

## Filtragem da saída

Também podemos filtrar a saída do arquivo XML adicionando um critério ao selecione o atributo no elemento ```<xsl:for-each>```.

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

    <xsl:template match="/">
        <html>
        <body>
        <h2>My CD Collection</h2>
        <table border="1">
            <tr bgcolor="#9acd32">
                <th>Title</th>
                <th>Artist</th>
            </tr>
            <xsl:for-each select="catalog/cd[artist='Bob Dylan']">
                <tr>
                    <td><xsl:value-of select="title"/></td>
                    <td><xsl:value-of select="artist"/></td>
                </tr>
            </xsl:for-each>
        </table>
        </body>
        </html>
    </xsl:template>

</xsl:stylesheet>
~~~

Os operadores de filtros são:

- ```=``` (igual)
- ```!=``` (não igual)
- ```<``` menos que
- ```>``` maior que
