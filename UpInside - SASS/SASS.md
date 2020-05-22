## Requisitos
**Linux, Mac e Windows**
- NPM
> OBS: No windows instale o node, pois o npm vem junto.

## Instalação
```bash
$ npm install -g sass
```
**`-g`** define o sass como global.

## Comandos
#### Processar um único arquivo SCSS
```bash
#. Sintaxe
$ sass {arquivo_origem} {arquivo_destino}

#. Exemplo
$ sass cdn/scss/style.scss cdn/css/style.css
```

#### Processar todos os arquivos de uma pasta
```bash
#. Sintaxe
$ sass {diretório_origem}:{diretório_destino}

#. Exemplo
$ sass cdn/scss:cdn/css
```

#### Atributos
```bash
$ sass cdn/scss:cdn/css --watch --style=compressed
```
**`--watch`** deixa um serviço rodando para processar os arquivos `scss` automaticamente sempre que tiver alteração.
**`--style=compressed`** minifica os arquivos `scss`.

## Juntando arquivos SCSS
Exemplo de arvore de arquivos:
```
scss/
	components/
		_buttons.scss
		_footer.scss
		_header.scss
		_titles.scss
	reset/
		_reset.scss
	_variables.scss
	style.scss
```

Juntando vários arquivos `scss` em um único arquivo `style.scss`. 
```scss
@import "reset/reset"
@import "variables"
@import "components/header"
@import "components/footer"

header {
	line-height: 30px;
}

...
```

## Aprofundando no SASS
```scss
.header {
	width: 100%;
	background-color: #069;
	
	.navigation {
		width: 1080px;
		margin: 0 auto;
		padding: 20px;
		
		a {
			color: #FFF;
			padding: 12px;
			
			&:hover {
				color: #F90;
			}
		}
	}
}
```

### Variáveis
De preferência deixe todas as variáveis no arquivo `_variables.scss`.
##### Definindo variáveis
```scss
$width-content: 1080px;
$color-primary: #3E8EBB;
```

##### Usando as variáveis
```scss
.header {
	with: $width-content;
	background-color: $color-primary;
}

.content {
	with: $width-content;
}

.footer {
	with: $width-content;
	background-color: $color-primary;
}
```

## Métodos do SASS
##### lighten
Deixa a cor `x%` mais claro.
```scss
// Sintaxe:
lighten({cor}, {percentual});

// Exemplo:
lighten(#666, 10%);
```

##### darken
Deixa a cor `x%` mais escuro.
```scss
// Sintaxe:
darken({cor}, {percentual});

// Exemplo:
darken(#666, 10%);
```

## IF - ELSE
```scss
.btn {
	padding: 6px 12px;
	
	&:hover {
		@if $button-hover-type == 'darken' {
			background-color: darken(#666, 10%);
		} @else {
			background-color: lighten(#666, 10%);
		}
	}
}
```

## Array
#### Definindo array
```scss
$color-green: #36BA9B;
$color-blue: #39AED9;
$color-yellow: #F5B946;
$color-red: #D94352;

$theme-colors: () !default;
$theme-colors: map_merge((
	"green": $color-green,
	"blue": $color-blue,
	"yellow": $color-yellow,
	"red": $color-red,
), $theme-colors);
```

#### Each
```scss
@each $color, $value in $theme-colors {
	.btn-#{$color} {
		background-color: $value;
	}
}
```

## Mixing (Funções)
```scss
// Definindo o mixin (função)
@mixin button($color) {
	background-color: $color;
	color: #FFF;

	&:hover {
		@if $button-hover-type == 'darken' {
			background-color: darken($color, 10%);
		} @else {
			background-color: lighten($color, 10%);
		}
	}
}

// Usando o mixin (função)
@each $color, $value in $theme-colors {
	.btn-#{$color} {
		@include button($value);
	}
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NzI1MzU5MzRdfQ==
-->