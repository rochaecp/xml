# Sintaxe

- XML usa uma sintaxe muito auto-descrita.
- Um prólogo define a versão XML e a codificação de caracteres.

~~~xml
<?xml version="1.0" encoding="UTF-8"?>
~~~

- A próxima linha é a elemento raiz do documento (bookstore).
- A próxima linha contém um elemento (book).
- Regras de sintaxe:
    - Documentos XML devem ter um elemento raiz que é o pai de todos os outros elementos.
    - O prólogo do XML é opcional. Se existir, deve ser a primeira linha do documento.
    - Para evitar erros, você deve especificar a codificação usada ou salvar seus arquivos XML como UTF-8.
    - UTF-8 é a codificação de caracteres padrão para documentos XML (e para HTML5, CSS, JavaScript, PHP e SQL).
    - Todos os Elementos XML Devem Ter uma Tag de Fechamento (O prólogo não tem uma tag de fechamento pois não faz parte do documento XML.).
    - As tags XML são sensíveis a maiúsculas de minúsculas. A tag <Letter> é diferente da tag <letter>.
    - Em XML, todos os elementos devem estar devidamente aninhados um dentro do outro.
        - Exemplo incorreto: ```<b><i>This text is bold and italic</b></i>```
        - Exemplo correto: ```<b><i>This text is bold and italic</i></b>```
    - Elementos XML podem ter atributos em pares nome/valor.
    - Caracteres especiais (Apenas ```<``` e ```&``` são estritamente ilegais em XML, mas é um bom hábito substituir ```>``` por o ```&gt;``` também): 
        - ```<``` - substituir por ```&lt;```;
        - ```>``` - substituir por ```&gt;```;
        - ```&``` - substituir por ```&amp;```;
        - ```'``` - substituir por ```&apos;```;
        - ```"``` - substituir por ```&quot;```;
    - Comentários:
        - A sintaxe para escrever comentários em XML é semelhante à do HTML: ```<!-- This is a comment -->```
        - Dois traços no meio de um comentário não são permitidos.
    - O espaço em branco é preservado em XML:
        - XML não trunca vários espaços em branco (HTML trunca vários espaços brancos para um único espaço branco).
    - O XML armazena nova linha como LF (Unix/Mac: LF, Windows: CR+LF).

