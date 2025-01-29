# XML HttpRequest

- Todos os navegadores modernos têm um objeto XMLHttpRequest embutido para solicitar dados de um servidor.

## O objeto XMLHttpRequest

- O objeto XMLHttpRequest pode ser usado para solicitar dados de um servidor web.
- O objeto XMLHttpRequest pode:
    - Atualizar uma página da web sem recarregar a página
    - Solicitar dados de um servidor - após o carregamento da página
    - Receber dados de um servidor - após a página ter sido carregada
    - Enviar dados para um servidor - em segundo plano
- Exemplo:
    - Quando você digita um caractere num campo de entrada, um XMLHttpRequest é enviado para o servidor, algumas sugestões de nome são devolvidas (do servidor)

## Enviar um XMLHttpRequest

~~~javascript
var xhttp = new XMLHttpRequest(); // cria um objeto XMLHttpPrequest 
xhttp.onreadystatechange = function() { // a propriedade onreadystatechamag especifica uma função a ser executada toda vez que o status do objeto XMLHttpRequest muda
    if (this.readyState == 4 && this.status == 200) { // Quando readyState a propriedade é 4 e o status a propriedade é 200, a resposta está pronta
        document.getElementById("demo").innerHTML = xhttp.responseText; // retorna a resposta do servidor como um cadeia de texto
    }
};
xhttp.open("GET", "filename", true);
xhttp.send();
~~~