# Elemento XSLT apply-templates

- O elemento ```<xsl:apply-templates>``` aplica uma regra de modelo a o elemento atual ou para os nós filhos do elemento atual.
- Se adicionarmos um atributo "select" ao elemento ```<xsl:apply-templates>```, ele processará apenas os elementos filhos que correspondem ao valor do atributo. Podemos usar o atributo "select" para especificar em que ordem o os nós filhos devem ser processados.

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

    <xsl:template match="/">
        <html>
        <body>
        <h2>My CD Collection</h2>
        <xsl:apply-templates/>
        </body>
        </html>
    </xsl:template>

    <xsl:template match="cd">
        <p>
        <xsl:apply-templates select="title"/>
        <xsl:apply-templates select="artist"/>
        </p>
    </xsl:template>

    <xsl:template match="title">
        Title: <span style="color:#ff0000">
        <xsl:value-of select="."/></span>
        <br />
    </xsl:template>

    <xsl:template match="artist">
        Artist: <span style="color:#00ff00">
        <xsl:value-of select="."/></span>
        <br />
    </xsl:template>

</xsl:stylesheet>
~~~