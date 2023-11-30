# Elemento XSLT value-of

- O elemento ```<xsl:value-of>``` é usado para extrair o valor de um nó selecionado.

~~~xml
...
<td><xsl:value-of select="catalog/cd/title"/></td>
...
~~~

-  O atributo select, no exemplo acima, contém uma expressão XPath. Uma expressão XPath funciona como navegar em um sistema de arquivos; uma barra direta (/) seleciona subdiretórios.
