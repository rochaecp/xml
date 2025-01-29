# XML Schema

- Um esquema XML descreve a estrutura de um documento XML, apenas como um DTD.
- Um documento XML com sintaxe correta é chamado de "Bem Formado".
- Um documento XML validado contra um esquema XML é ambos "Bem Formado" e "Válido".

# XML Schema 

- O XML Schema é uma alternativa baseada em XML para DTD:

~~~xsd
<xs:element name="note">
    <xs:complexType>
        <xs:sequence>
            <xs:element name="to" type="xs:string"/>
            <xs:element name="from" type="xs:string"/>
            <xs:element name="heading" type="xs:string"/>
            <xs:element name="body" type="xs:string"/>
        </xs:sequence>
    </xs:complexType>
</xs:element>

<!-- 
O esquema acima é interpretado assim:

<xs:element name="note"> define o elemento chamado "note"<TAG1>"
<xs:complexType> o elemento "nota" é um tipo complexo
<xs:sequence> o tipo complexo é uma sequência de elementos
<xs:element name="to" type="xs:string"> o elemento "to" é do tipo string (texto)
<xs:element name="de" type="xs:string"> o elemento "de" é do tipo string
<xs:element name="heading" type="xs:string"> o elemento "heading" é do tipo string
<xs:element name="body" type="xs:string"> o elemento "body" é do tipo string
-->
~~~

- Os esquemas XML são mais poderosos que o DTD:
    - Os esquemas XML são escritos em XML.
    - Os esquemas XML são extensíveis a adições.
    - Os esquemas XML suportam tipos de dados.
    - Os esquemas XML suportam namespaces.
- Com o XML Schema, seus arquivos XML podem conter uma descrição de seu próprio formato.
- Com o XML Schema, você pode verificar os dados.
- Um dos maiores pontos fortes dos esquemas XML é o suporte para tipos de dados:
    - É mais fácil descrever o conteúdo do documento
    - É mais fácil definir restrições aos dados
    - É mais fácil validar a correção dos dados
    - É mais fácil converter dados entre diferentes tipos de dados
- Esquemas XML usam Sintaxe XML:
    - Você não precisa aprender uma nova linguagem.
    - Você pode usar seu editor XML para editar seus arquivos Schema.
    - Você pode usar seu analisador XML para analisar seus arquivos Schema.
    - Você pode manipular seus esquemas com o XML DOM.
    - Você pode transformar seus esquemas com XSLT.

