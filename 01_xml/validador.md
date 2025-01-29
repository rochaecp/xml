# Validador XML

- Um documento XML com sintaxe correta é chamado de "Bem Formado".
- As regras de sintaxe foram são:
    - Os documentos XML devem ter um elemento raiz.
    - Elementos XML devem ter uma tag de fechamento.
    - As tags XML são sensíveis a maiúsculas.
    - Os elementos XML devem estar corretamente aninhados.
    - Os valores de atributo XML devem ser citados.
- Erros em documentos XML interromperão seus aplicativos XML.
- A especificação XML do W3C afirma que um programa deve parar de processar um documento XML se encontrar um erro. A razão é que o software XML deve ser pequeno, rápido e compatível.
- Os navegadores HTML têm permissão para exibir documentos HTML com erros (como tags finais ausentes).
- **Com XML, erros não são permitidos.**

## Documentos XML válidos

- Um documento XML "bem formado" não é o mesmo que um documento XML "válido.
- Um documento XML "válido" deve ser bem formado. Além disso, deve estar em conformidade com a definição do tipo de documento.
- Existem duas definições de tipo de documento diferentes que podem ser usadas com XML:
    - DTD - O Documento original Tipo Definição
    - XML Schema - Uma alternativa baseada em XML para DTD
- Uma definição de tipo de documento define as regras e os elementos e atributos legais para um documento XML.    