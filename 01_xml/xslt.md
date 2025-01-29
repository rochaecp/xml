# XML e XSLT

- Com XSLT você pode transformar um documento XML em HTML.
- XSLT (eXtensible Stylesheet Language Transformations) é a linguagem de folha de estilo recomendada para XML.
- O XSLT é muito mais sofisticado que o CSS. Com XSLT você pode adicionar/remover elementos e atributos de ou para o arquivo de saída.
- Você também pode reorganizar e classifique elementos, realize testes e tome decisões sobre quais elementos ocultar e exibição, e muito mais.
- XSLT usa XPath para encontrar informações em um documento XML.

## Exemplo

Arquivo xml:

~~~xml
<breakfast_menu>
    <food>
        <name>Belgian Waffles</name>
        <price>$5.95</price>
        <description>Two of our famous Belgian Waffles with plenty of real maple syrup</description>
        <calories>650</calories>
    </food>
    <food>
        <name>Strawberry Belgian Waffles</name>
        <price>$7.95</price>
        <description>Light Belgian waffles covered with strawberries and whipped cream</description>
        <calories>900</calories>
    </food>
    <food>
        <name>Berry-Berry Belgian Waffles</name>
        <price>$8.95</price>
        <description>Light Belgian waffles covered with an assortment of fresh berries and whipped cream</description>
        <calories>900</calories>
    </food>
    <food>
        <name>French Toast</name>
        <price>$4.50</price>
        <description>Thick slices made from our homemade sourdough bread</description>
        <calories>600</calories>
    </food>
    <food>
        <name>Homestyle Breakfast</name>
        <price>$6.95</price>
        <description>Two eggs, bacon or sausage, toast, and our ever-popular hash browns</description>
        <calories>950</calories>
    </food>
</breakfast_menu>
~~~

Use XSLT para transformar XML em HTML, antes de ser exibido em um navegador:

~~~xslt
<html xsl:version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <body style="font-family:Arial;font-size:12pt;background-color:#EEEEEE">
        <xsl:for-each select="breakfast_menu/food">
            <div style="background-color:teal;color:white;padding:4px">
                <span style="font-weight:bold">
                    <xsl:value-of select="name"/> - </span>
                <xsl:value-of select="price"/>
            </div>
            <div style="margin-left:20px;margin-bottom:1em;font-size:10pt">
                <p>
                    <xsl:value-of select="description"/>
                    <span style="font-style:italic"> (<xsl:value-of select="calories"/> calories per serving)</span>
                </p>
            </div>
        </xsl:for-each>
    </body>
</html>
~~~