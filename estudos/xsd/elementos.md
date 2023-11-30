# Elementos Simples XSD

- Esquemas XML definem os elementos de seus arquivos XML.
- Um elemento simples é um elemento XML que contém apenas texto. Não pode conter quaisquer outros elementos ou atributos.
- O que é um Elemento Simples?
    - Um elemento simples é um elemento XML que pode conter apenas texto. Não pode conter quaisquer outros elementos ou atributos.
    - No entanto, a restrição "apenas texto" é bastante enganosa. O texto pode ser de muitos tipos diferentes. Pode ser um dos tipos incluídos em a definição de Esquema XML (booleano, string, data, etc.), ou pode ser um tipo personalizado que você pode definir a si mesmo.
    - Você também pode adicionar restrições (facetas) a um tipo de dados para limitar seu conteúdo ou exigir que os dados correspondam a um padrão específico.

## Definindo um Elemento Simples

A sintaxe para definir um elemento simples é: ```<xs:element name="xxx" type="yyy"/>``` onde xxx é o nome do elemento e yyy é o tipo de dados do elemento.

XML Schema tem um monte de built-in tipos de dados. O mais os tipos comuns são:
- xs:string
- xs:decimal
- xs:integer
- xs:boolean
- xs:date
- xs:time

Aqui estão alguns elementos XML:

~~~xml
<lastname>Refsnes</lastname>
<age>36</age>
<dateborn>1970-03-27</dateborn>
~~~

E aqui estão as definições de elementos simples correspondentes:

~~~xml
<xs:element name="lastname" type="xs:string"/>
<xs:element name="age" type="xs:integer"/>
<xs:element name="dateborn" type="xs:date"/>
~~~

## Valores Padrão e Fixos para Elementos Simples

- Elementos simples podem ter um valor padrão OU um valor fixo especificado.
- Um valor padrão é atribuído automaticamente ao elemento quando nenhum outro valor é especificado.

No exemplo a seguir, o valor padrão é "vermelho":
- ```<xs:element name="color" type="xs:string" default="red"/>```

Um valor fixo também é atribuído automaticamente ao elemento e você não pode especificar outro valor.

No exemplo a seguir, o valor fixo é "vermelho":
- ```<xs:element name="color" type="xs:string" fixed="red"/>```