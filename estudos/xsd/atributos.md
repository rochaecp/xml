# Atributos XSD

- Todos os atributos são declarados como tipos simples.

- O que é um atributo?
    - Elementos simples não podem ter atributos. Se um elemento tem atributos, ele é considerado de um tipo complexo. Mas o atributo em si é sempre declarado como um tipo simples.
- Como Definir um Atributo?
    - A sintaxe para definir um atributo é:
        - ```<xs:attribute name="xxx" type="yyy"/>``` onde xxx é o nome do atributo e yyy especifica o tipo de dados do atributo.

XML Schema tem um monte de built-in tipos de dados. Os tipos mais comuns são:
- xs: string
- xs: decimal
- xs: inteiroger
- xs: booleano
- xs:data
- xs: tempo

## Exemplo

Aqui está um elemento XML com um atributo:

```<lastname lang="EN">Smith</lastname>```

E aqui está a definição de atributo correspondente:

```<xs:attribute name="lang" type="xs:string"/>```

## Valores Padrão e Fixos para Atributos

- Atributos podem ter um valor padrão OU um valor fixo especificado.
- Um valor padrão é atribuído automaticamente ao atributo quando nenhum outro valor é especificado.

No exemplo a seguir, o valor padrão é "EN":

```<xs:attribute name="lang" type="xs:string" default="EN"/>```

Um valor fixo também é atribuído automaticamente ao atributo e você não pode especificar outro valor.

No exemplo a seguir, o valor fixo é "EN":

```<xs:attribute name="lang" type="xs:string" fixed="EN"/>```

## Atributos Opcionais e Necessários

- Os atributos são opcionais por padrão. 
- Para especificar que o atributo é obrigatório, use o atributo "use:

```<xs:attribute name="lang" type="xs:string" use="required"/>```

## Restrições ao Conteúdo

- Quando um elemento ou atributo XML tem um tipo de dados definido, ele coloca restrições no conteúdo do elemento ou atributo.
- Se um elemento XML for do tipo "xs:date" e contiver uma string como "Olá Mundo", o elemento não validará.
- Com XML Schemas, você também pode adicionar suas próprias restrições ao seu XML elementos e atributos. Essas restrições são chamadas de facetas. Você pode ler mais sobre facetas no próximo capítulo.