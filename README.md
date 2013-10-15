# HTML e CSS guia de codificação
Padrões para um desenvolvimento flexivel, duravél e sustentavel com HTML e CSS.



----------


## Indíce

* [Regra de ouro](#golden-rule)
* [HTML](#html)
  * [Syntaxe](#html-syntax)
  * [HTML5 doctype](#html5-doctype)
  * [Pragmatismo com a semântica](#pragmatism-over-semantics)
  * [Ordenação de atributos](#attribute-order)
  * [Marcação gerada através do Javascript](#javascript-generated markup)
* [CSS](#css)
  * [CSS syntaxe](#css-syntax)
  * [Ordem de declaração](#declaration-order)
  * [Formatando exceções](#formatting-exceptions)
    * [Propriedades prefixadas](#prefixed-properties)
    * [Regras com declarações unicas](#rules-with-single-declarations)
  * [Legibilidade para humanos](#human-readable)
    * [Comentarios](#comments)
    * [Classes](#classes)
    * [Seletores](#selectors)
  * [Organização](#organization)
* [Escrevendo uma cópia](#copy)
  * [Caso de sentença](#sentence-case)



----------



## Regra de outro 

> Todo o código em uma base deve parecer que uma pessoa o codificou, não importando quantas pessoas contribuiram.

Isso significa estritamente que deve ser reforçado o use de guias a todo momento. Para adições ou contribuições, por favor [mande abra uma "issue" no Github](https://github.com/mdo/code-guide).



----------



## HTML


### HTML syntaxe

* Use tabulações suaves com dois espaços
* A cada novo elemento aninhado deve-se utilzar (2 espaços) para estrutura-los
* Sempre use aspas, nunca apostrofes
* Não inclua barras em elementos que não tem a necessidade de fechamento

**Exemplo incorreto:**

````html
<!DOCTYPE html>
<html>
<head>
<title>Titulo da pagina</title>
</head>
<body>
<img src='imagens/logo-da-companhia.png' alt='Companhia' />
<h1 class='hello-world'>Olá, mundo!</h1>
</body>
</html>
````

**Exemplo correto:**

````html
<!DOCTYPE html>
<html>
  <head>
    <title>Titulo da pagina</title>
  </head>
  <body>
    <img src="imagens/logo-da-companhia.png" alt="Companhia">
    <h1 class="hello-world">Olá, mundo!</h1>
  </body>
</html>
````


### HTML5 doctype

Aplique o padrão a seguir, para cada browser possivel com um simples tipo de documento (doctype) no começo de cada pagina em HTML.

````html
<!DOCTYPE html>
````


### Pragmatism over semantics

Esforce-se para manter o HTML padronazado e semantico, mas não sacrifique o pragmatismo. Use o menor numero possivel de marcações complexas.


### Ordem dos atributos 

Atributos HTML devem ter a seguinte ordem para deixar a leitura ao código mais facil.

* class
* id
* data-*
* for|type|href

A sua marcação devera conter este aspecto:

````html
<a class="" id="" data-modal="" href="">Exemplo de link</a>
````

### Marcações através do Javascript

Escrever marcações em um arquivo javascript faz com que o contéudo lá inserido, fique dificil de encontrar e editar, e menos performatico. NÃO FAÇA ISSO.



----------



## CSS

### CSS syntaxe

* Use tabulações suaves  com dois espaços
* Onde um  agrupamento de seletores, mantenha seletores individuais em uma unica linha
* Inclua um espaço antes de abrir o bloco de declaração
* Feche a declaração em uma nova linha
* Include one space after <code>:</code> in each property
* Inclua um espaço depois de <code>:</code> em cada propriedade
* Cada declaração ficara em sua própria linha
* Ao final de todas as declarações devera conter ponto e virgular
* Valores separados por virgulas incluem um espado depois de cada virgula
* Não inclua espaços depois das virgulas em cores RGB ou RGBA, e não prefacie valores com o valor zero
* Todos os valores decimais em minusculas, ex.: <code>#fff</code> ao invés de <code>#FFF</code>
* Use atralhos para valores hexadecimais quando disponiveis, ex.: <code>#fff</code> ao invés de <code>#ffffff</code>
* Utilize aspas em valores de propriedados nos seletores, ex.: <code>input[type="text"]</code>
* Não especifique unidades para valores do tipo zero, ex.: <code>margin: 0</code> no lugar de <code>margin: 0px;</code>

**Exemplo incorreto:**

````css
.selector, .selector-secondary, .selector[type=text] {
  padding:15px;
  margin:0px 0px 15px;
  background-color:rgba(0, 0, 0, 0.5);
  box-shadow:0 1px 2px #CCC,inset 0 1px 0 #FFFFFF
}
````

**Exemplo correto:**

````css
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin: 0 0 15px;
  background-color: rgba(0,0,0,.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
````

Qualquer questão em relação aos termos utilizados aqui? Veja a [sessão de syntaxe do CSS](http://en.wikipedia.org/wiki/Cascading_Style_Sheets#Syntax) no Wikipedia.



### Ordem de declaração

Relacionado a declarações devem ser agrupadas, colocando o posicionamento e propriedade de "box-model" proximas do topo, seguindos pela tipografia e propriedades visuais.

````css
.declaration-order {
  /* Positioning */
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  /* Box-model */
  display: block;
  float: right;
  width: 100px;
  height: 100px;

  /* Typography */
  font: normal 13px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;

  /* Visual */
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  /* Misc */
  opacity: 1;
}
````

For a complete list of properties and their order, please see [Recess](http://twitter.github.com/recess).


### Formatando exceções

Em muitos casos, elas fazem sentido para desviar ligeiramente para o padrão [syntaxe](#css-syntax).


#### Propriedades prefixadas

Onde a utilização de prefixos de propriedades de navegadores especificos, indentam cada propriedade com uma igualação vertical para facilitar a edição.

````css
.selector {
  -webkit-border-radius: 3px;
     -moz-border-radius: 3px;
          border-radius: 3px;
}
````

No Textmate, use **Text &rarr; Editando cada linha da selação** (&#8963;&#8984;A). No Sublime Text 2, use **Seleção &rarr; Add linha anterior** (&#8963;&#8679;&uarr;) e **Seleção &rarr;  Add proxima linha** (&#8963;&#8679;&darr;).

#### Regras com declarações unicas

Em instancias onde regras severas estão presentes com uma unica declaração para cada uma, considere remover quebras de linhas para uma melhor leitura e rápida edição.

````css
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }

.sprite {
  display: inline-block;
  width: 16px;
  height: 15px;
  background-image: url(../img/sprite.png);
}
.icon           { background-position: 0 0; }
.icon-home      { background-position: 0 -20px; }
.icon-account   { background-position: 0 -40px; }
````


### Legibilidade para humanos

Código é escrito e mantido por pessoas. Mantenha o seu código descritivo, bem comentado, e que possa ser abordado por outros.

#### Comentarios

Bons comentarios no código transmitem o contexto ou o propósito e não devem simplismente explicar um componente ou o nome de uma classe.

**Mal exemplo:**

````css
/* Modal header */
.modal-header {
  ...
}
````

**Bom exemplo:**

````css
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
````

#### Nomes de classes

* Keep classes lowercase and use dashes (not underscores or camelCase)
* Mantenha as classes em minusculas e use hifens (e não sublinhados ou tudo junto com apenas o começo das palavras capitalizado "camelCase")
* Evite abriviações como notação
* Mantenha classes com nomes pequenos e sucintos quando possivel
* Use nome siginificativos; use nomes estruturais ou que denotem o proposito como apresentação
* Use prefixos de classes baseado em parentes mais proximos do componente base daquela classe

**Mal exemplo:**

````css
.t { ... }
.red { ... }
.header { ... }
````

**Bom exemplo:**

````css
.tweet { ... }
.important { ... }
.tweet-header { ... }
````

#### Seletores 

* Use classes em elementos que representem abstrações genericas
* Mantenha o mais curto e limite o numero de elementos em cada arvore de seletor
* Scope classes to the closest parent when necessary (e.g., when not using prefixed classes)
* Mantenha-se no escopo de classes que tem um parentes mais proximo ( ex.:, onde não usam classes com prefixo )

**Mal examplo:**

````css
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
````

**Bom exemplo:**

````css
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
````

### Organização 

* Organize seleções do código por componente
* Desenvolva uma concistente hierarquia comentada
* Se você estiver utilizando varios arquivos para CSS, quebre eles em componentes



----------



## Cópia 

### Caso de sentença 

Sempre escreva uma cópia, incluindo cabeçãlhos e comentarios do código, em [caso de sentença](http://en.wikipedia.org/wiki/Letter_case#Usage). Em outras palavras, ao lado dos titulos e nomes próprios, sempre capitalize a primeira palavra.



----------



### Obrigado 

Fortemente inspirado pelo [CSS Idiomatico](https://github.com/necolas/idiomatic-css) e O [Guia de estilo do Github](http://github.com/styleguide). Feito com todo amor do mundo por [@mdo](http://twitter.com/mdo).
