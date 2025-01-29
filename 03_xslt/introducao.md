# Introdução ao XSLT

- XSL (eXtensible Stylesheet Language) é uma linguagem de estilo para XML.
- O XSLT (XSL Transformations) pode transformar documentos XML em outros formatos (como transformar XML em HTML).
- [XSLT Elements Reference](https://www.w3schools.com/xml/xsl_elementref.asp)
- [XSLT, XPath, and XQuery Functions](https://www.w3schools.com/xml/xsl_functions.asp)
- Definições
    - XSLT é uma linguagem para transformar documentos XML.
    - XPath é uma linguagem para navegar em documentos XML.
    - XQuery é uma linguagem para consultar documentos XML.
- XSLT é a parte mais importante do XSL
- XSLT transforma um documento XML em outro documento XML
- XSLT usa XPath para navegar em documentos XML
- XSLT é uma recomendação do W3C
- Histórico
    - O World Wide Web Consortium (W3C) começou a desenvolver o XSL porque havia a necessidade de uma Linguagem de Folha de Estilo baseada em XML.
- XSL = Folhas de Estilo para XML
    - XML não usa tags predefinidas, e portanto, o significado de cada tag não é bem compreendido.
    - Então, XSL descreve como os elementos XML devem ser exibidos.
- XSL consiste em quatro partes:
    - XSLT - uma linguagem para transformar documentos XML
    - XPath - uma linguagem para navegar em documentos XML
    - XSL-FO - uma linguagem para formatação de documentos XML (descontinuado em 2013)
    - XQuery - uma linguagem para consultar documentos XML     
- XSLT é usado para transformar um documento XML em outro documento XML, ou outro tipo de documento reconhecido por um navegador, como HTML e XHTML. Normalmente, o XSLT faz isso transformando cada elemento XML em um (X)HTML elemento.
- Com XSLT você pode adicionar/remover elementos e atributos de ou para o arquivo de saída. Você também pode reorganizar e classificar elementos, realizar testes e tomar decisões sobre quais elementos esconder e exibir, e muito mais.
- Uma maneira comum de descrever o processo de transformação é dizer isso XSLT transforma uma árvore-fonte XML em uma árvore-resultado XML.
- XSLT usa XPath para encontrar informações em um documento XML. XPath está acostumado a navegue pelos elementos e atributos em documentos XML.
- Todos os principais navegadores suportam XSLT e XPath.
- XSLT tornou-se um Recomendação W3C 16. Novembro de 1999.

## Como Funciona

- No processo de transformação, o XSLT usa o XPath para definir partes da fonte documento que deve corresponder a um ou mais modelos predefinidos. Quando uma correspondência é encontrada, O XSLT transformará a parte correspondente do documento de origem no resultado documento.