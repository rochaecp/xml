# Elemento XSLT if

- O elemento ```<xsl:if>``` é usado para colocar um teste condicional contra o conteúdo do arquivo XML.
- Para colocar um teste if condicional em relação ao conteúdo do arquivo XML, adicione um elemento ```<xsl:if>``` ao documento XSL.

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
                <th>Price</th>
            </tr>
            <xsl:for-each select="catalog/cd">
                <xsl:if test="price &gt; 10"> <!-- o atributo test contém a expressão a ser avaliada -->
                    <tr>
                        <td><xsl:value-of select="title"/></td>
                        <td><xsl:value-of select="artist"/></td>
                        <td><xsl:value-of select="price"/></td>
                    </tr>
                </xsl:if>
            </xsl:for-each>
        </table>
        </body>
        </html>
    </xsl:template>

</xsl:stylesheet>
~~~