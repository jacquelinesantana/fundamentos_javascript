

# Javascript

O JavaScript é  uma **linguagem de criação de scripts ou uma linguagem interpretada**. O código em JavaScript é interpretado.

Em uma **linguagem compilada**, a máquina de destino traduz o programa diretamente. Em uma **linguagem interpretada**, o código fonte não é traduzido diretamente pela máquina de destino. Em  vez disso, um programa diferente, o interpretador, lê e executa o  código.

Criado 1996 a pedido da Netscape

Onde o JavaScript pode ser usado?

**No desenvolvimento web, o Javascript pode ser usado no Frontend, Backend e até mesmo na comunicação com banco de dados**. No frontend é possível manipular os elementos da página, como já  exploramos. No backend é possível tratar requisições e executar diversas tarefas através do framework mais popular Node. js

## Fundamentos

Dom -> Document Object Model ou modelo de documento por objetos é uma interface de programação que os navegadores utilizam para representar páginas na web. 

Então a Dom é uma interface que permite que o Javascript e outras linguagens possam manipular e construir paginas web nos navegadores - W3C é responsável pela DOM.

Sobre a Dom: https://www.youtube.com/watch?v=HOv9CqqAZk0

## Tipos de variáveis

var = Variável global

let = variável de bloco, instrução ou expressão

const = constante, não sofre alteração do seus dados até o final do arquivo.

Saída de dados = alert("texto")

Concatenar = +

### Sintaxe

em linha:

```
<h1 onclick="this.innerHTML='Isso acontece quando usamos o evento onClick!'" > Test</h1>
```

no arquivo:

```
<script type="text/javascript">
alerta("olá mundo")
</script>
```

Externo:

Adicionar no Html preferencialmente no footer

<script src="./assets/js/script.js"></script>

Criar um arquivo com nome script.js

// ! Declaração de variáveis
// tipagem por inferência

```
var nome; // Padrão antigo, evitem usar (variável de escopo global) variáveis de escopo local
let resultado; // Let it change -> (variável que pode mudar de valor)
const nome = 'Thiago'; // Constant -> (variável que não vai mudar de valor)
```

Função simples:

```
 function dataAtual() {
  alert(Date())
}
```

## Chamar função por evento:

| onBlur      | remove o foco do elemento                             |
| ----------- | ----------------------------------------------------- |
| onChange    | Ao mudar o valor do elemento                          |
| onClick     | Quando o elemento é clicado pelo usuário              |
| onFocus     | Quando elemento é focado                              |
| onKeyPress  | Quando usuário pressiona uma tecla sobre o elemento   |
| onLoad      | Quando carrega o elemento por completo                |
| onMouseOver | ação quando o usuário passa o mouse sobre o elemento  |
| onMouseOut  | ação quando o usuário retira o mouse sobre o elemento |
| onSubmit    | ação ao enviar um formulário                          |

Sobre eventos: https://www.devmedia.com.br/trabalhando-com-eventos-em-javascript/28521

```
// ! Gets de elementos da tela
// const perfil = document.getElementById('perfil') -> pega pelo ID perfil
// const perfil = document.getElementsByClassName('perfil') -> pega pela classe
// const perfil = document.getElementsByName('name') -> pega pelo atributo name
// const perfil = document.getElementsByTagName('name') -> pega pela tag
// const perfil = document.querySelector('.perfil')

const nome = document.querySelector('#nome')
const email = document.querySelector('#email')
const mensagem = document.querySelector('#mensagem')

let nomeOk = false
let emailOk = false
let mensagemOk = false

const mapa = document.querySelector('#mapa')
```
Chamando através de evento:
no html 

```
onkeyup="validaNome()"
```

no JS função para validar campo nome

```

function validaNome() {
  let txtNome = document.querySelector("#txtNome")

  if (nome.value.length < 3) {
    txtNome.innerHTML = 'Nome muito curto'
    txtNome.style.color = 'red'
    nomeOk = false
  } else {
    txtNome.innerHTML = 'Nome ok'
    txtNome.style.color = 'green'
    nomeOk = true
  }
}
```

Chamando evento no HTML

```
onkeyup="validaEmail2()"
```

Valida E-mail:

```
function validaEmail() {
  let txtEmail = document.querySelector('#txtEmail')

  if(email.value.indexOf('@') == -1 || email.value.indexOf('.') == -1) {
    txtEmail.innerHTML = 'E-mail inválido'
    txtEmail.style.color = 'red'
    emailOk = false
  } else {
    txtEmail.innerHTML = 'E-mail válido'
    txtEmail.style.color = 'green'
    emailOk = true
  }
}
```

## expressão regular

### Objeto RegExp

Uma expressão regular é um **padrão** de caracteres.

O padrão é usado para fazer funções de **"pesquisar e substituir"** de correspondência de padrão no texto.

Em JavaScript, um **Objeto RegExp** é um padrão com **Propriedades** e **Métodos** .

https://www.w3schools.com/jsref/jsref_obj_regexp.asp

https://www.w3schools.com/jsref/tryit.asp?filename=tryjsref_regexp

```
function validaEmail2() {
  // criação do padrão de email, vai aceitar caracteres + @ + caracteres + . + 2 ou 3 caracteres pra finalizar
  //email@email.com
  let regex = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/
  let txtEmail = document.querySelector('#txtEmail')

  // o if será feito de uma forma diferente, verificando se o que a pessoa digitou condiz com o padrão do e-mail (match)
  // caso de certo, e-mail válido, senão, e-mail inválido
  if(email.value.match(regex)) {
    txtEmail.innerHTML = 'E-mail válido'
    txtEmail.style.color = 'green'
    emailOk = true
  } else {
    txtEmail.innerHTML = 'E-mail inválido'
    txtEmail.style.color = 'red'
    emailOk = false
  }
}
```

Valida mensagem do textarea:

```
function validaMensagem() {
  let txtMensagem = document.querySelector('#txtMensagem')

  if(mensagem.value.length >= 10) {
    txtMensagem.innerHTML = 'Mensagem muito grande, da até preguiça de ler'
    txtMensagem.style.color = 'red'
    mensagemOk = false
  } else {
    txtMensagem.innerHTML = 'Mensagem ok'
    txtMensagem.style.color = 'green'
    mensagemOk = true
  }
}
```

Chamar evento ao digitar a mensagem:

```
onkeyup="validaMensagem()"
```



Validação ao enviar o formulário

```
function enviarForm() {
  if(nomeOk === true && emailOk === true && mensagemOk === true) {
    alert(nome.value + ', obrigado pelo contato, aguarde nosso retorno.')
  } else {
    alert('Por favor, preencha todos os campos corretamente.')
  }
}

function mapaZoom() {
  mapa.style.aspectRatio = '16/11'
}

function mapaNormal() {
  mapa.style.aspectRatio = '16/9'
}
```

Chamar evento ao clicar no botão:

```
onclick="enviarForm()"
```



> Curiosidades, sites antigos:
> https://web.archive.org/web/19961223175947/http://uol.com.br/
>
> https://web.archive.org/web/19991002184149/http://uol.com.br:80/
>
> https://web.archive.org/web/20000818123804/http://www.ig.com.br/br/
>
> https://web.archive.org/web/20230508062707/https://www.ig.com.br/

> Curiosidades2: sistemas operacionais antigos Windows e Mac
>
> https://oldweb.today/?browser=ns4-win#19960101/https://www.globo.com/

Código completo JS:

```
// ! Declaração de variaveis

// tipagem por inferencia
// var nome; // Padrão antigo, evitem usar (variavel de escopo global)
//  variaveis de escopo local
// let resultado; // Let it change -> (variavel que pode mudar de valor)
// const nome = 'Thiago'; // Constant -> (variavel que não vai mudar de valor)


// function dataAtual() {

//  alert(Date())

// }

// ! Gets de elementos da tela
// const perfil = document.getElementById('perfil') -> pega pelo ID perfil
// const perfil = document.getElementsByClassName('perfil') -> pega pela classe
// const perfil = document.getElementsByName('name') -> pega pelo atributo name
// const perfil = document.getElementsByTagName('name') -> pega pela tag
// const perfil = document.querySelector('.perfil')

const nome = document.querySelector('#nome')
const email = document.querySelector('#email')
const mensagem = document.querySelector('#mensagem')

let nomeOk = false
let emailOk = false
let mensagemOk = false

const mapa = document.querySelector('#mapa')

function validaNome() {

 let txtNome = document.querySelector("#txtNome")

 if (nome.value.length < 3) {

  txtNome.innerHTML = 'Nome muito curto'
  txtNome.style.color = 'red'
  nomeOk = false

 } else {
  txtNome.innerHTML = 'Nome ok'
  txtNome.style.color = 'green'
  nomeOk = true
 }
}

function validaEmail() {
 let txtEmail = document.querySelector('#txtEmail')

 if(email.value.indexOf('@') == -1 || email.value.indexOf('.') == -1) {

  txtEmail.innerHTML = 'E-mail inválido'
  txtEmail.style.color = 'red'
  emailOk = false

 } else {

  txtEmail.innerHTML = 'E-mail válido'
  txtEmail.style.color = 'green'
  emailOk = true

 }

}



function validaEmail2() {

 // criação do padrão de email, vai aceitar caracteres + @ + caracteres + . + 2 ou 3 caracteres pra finalizar

 let regex = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/
 let txtEmail = document.querySelector('#txtEmail')

 // o if será feito de uma forma diferente, verificando se o que a pessoa digitou condiz com o padrão do e-mail (match)
 // caso de certo, e-mail válido, senão, e-mail inválido

 if(email.value.match(regex)) {

  txtEmail.innerHTML = 'E-mail válido'
  txtEmail.style.color = 'green'
  emailOk = true

 } else {

  txtEmail.innerHTML = 'E-mail inválido'
  txtEmail.style.color = 'red'
  emailOk = false

 }

}

function validaMensagem() {

 let txtMensagem = document.querySelector('#txtMensagem')

 if(mensagem.value.length >= 10) {
  txtMensagem.innerHTML = 'Mensagem muito grande, da até preguiça de ler'
  txtMensagem.style.color = 'red'
  mensagemOk = false

 } else {
  txtMensagem.innerHTML = 'Mensagem ok'
  txtMensagem.style.color = 'green'
  mensagemOk = true
 }

}

function enviarForm() {

 if(nomeOk === true && emailOk === true && mensagemOk === true) {
  alert(nome.value + ', obrigado pelo contato, aguarde nosso retorno.')

 } else {
  alert('Por favor, preencha todos os campos corretamente.')
 }

}

function mapaZoom() {
 mapa.style.aspectRatio = '16/11'

}

function mapaNormal() {
 mapa.style.aspectRatio = '16/9'
}
```

## Fundamentos Javascript com prática - https://jsfiddle.net/

A ferramenta jdfiddle.net é uma ferramenta bem legal para quem esta iniciando os primeiros passos em Javascript e deseja compartilhar suas soluções ou ver como outras pessoas estão elaborando suas soluções, vou a seguir explicar seu funcionamento e também como você pode usar o meu repositório publico para avançar nos seus estudos, também aceito novos desafios. Meu Linkedin para conversarmos é: https://www.linkedin.com/in/hernandesjacque/

Ao acessar o site https://jsfiddle.net/ você terá acesso as seguintes informações:

![image-20230514175326097](C:\Users\tijac\AppData\Roaming\Typora\typora-user-images\image-20230514175326097.png)

1. A guia HTML permite que você escreva seu código em HTML com as tags e propriedades necessárias, lembrando que ao utilizar imagens em sua página, opte por usar uma imagem da internet, ou subir sua imagem em algum servidor de imagens e usar o link dessa imagem hospedada.
2. A guia Javascript permite você escrever seus Scripts e inclusive incluir eventos aos elementos do seu HTML.
3. A guia CSS permite que você crie uma folha de estilo para a sua página.
4. Botão Salvar permite que você salve essa página e tenha um link de compartilhamento do mesmo.
5. Em Untitled você pode informar um nome para essa página e ter maior organização para os seus trabalhos.
6. Botão Run, permite executar os códigos digitados e ver o resultado em seu navegador.
7. Result é o resultado do seu código, no caso tudo que seria visto em um navegador ou abrir seu código.
8. Console permite, assim como no navegador, ver os resultados do Javascript e saídas de console.log(). Se seu console não estiver disponível para visualização experiente puxar a barra inferior do Result para cima.

### Meu primeiro desafio

Como primeira missão nessa ferramenta, você pode explorar esse JsFiddle https://jsfiddle.net/tijacque/nhar97vg/37/ e ver como ele executa no console, tentar reproduzir e até explicar para você mesmo(a) usando as suas palavras.

Leia com atenção as anotações e boa atividade.

### Como estudar através dos JSfiddle?

Para seguir se desafiando cada vez mais, acesse o link: https://jsfiddle.net/user/fiddles/all/, aqui é bem fácil o estudo, basta ir seguindo realmente cada exercício pela ordem crescente:

[01 - Javascript Introdução e conceitos](https://jsfiddle.net/tijacque/nhar97vg/37/)

[02 - Javascript funções](https://jsfiddle.net/tijacque/0817jhg2/25/)

[03 - converter dados em variavel](https://jsfiddle.net/tijacque/Lwh83sby/35/)

[04 - constantes e identificar erros.](https://jsfiddle.net/tijacque/w6zgjunx/6/)

[05 - Operadores aritméticos ](https://jsfiddle.net/tijacque/bpqanx9t/39/)

[06 - Auto Increment - Decrement](https://jsfiddle.net/tijacque/uwx3sy01/15/)

[07 - Operadores relacionais](https://jsfiddle.net/tijacque/nyfu9kod/1/)

[08 - Operadores lógicos](https://jsfiddle.net/tijacque/0dnkva2t/1/)

[09 - testes lógicos](https://jsfiddle.net/tijacque/fmck5eas/2/)

[10 - Objeto Literal e coleção de objetos](https://jsfiddle.net/tijacque/y05gamuk/26/)

[11 - Datas](https://jsfiddle.net/tijacque/6c21phny/39/)

[12 - Inputs em Javascript](https://jsfiddle.net/tijacque/13vhj6rk/29/)

[13 - Tratar dados recebidos pelo readline JS](https://jsfiddle.net/tijacque/2ou5rtyj/8/)

[14 - array](https://jsfiddle.net/tijacque/grbyn6f5/24/)

[15 - estrutura de repetição](https://jsfiddle.net/tijacque/7sax6dko/13/)

[16 - date](https://jsfiddle.net/tijacque/xbgh59az/22/)

[17 - Converter datas](https://jsfiddle.net/tijacque/hL0y9ero/28/)

[18 - funções](https://jsfiddle.net/tijacque/9wsgoayr/14/)

[19 - Arrow function](https://jsfiddle.net/tijacque/bzwypL4v/25/)