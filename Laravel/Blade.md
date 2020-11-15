# Blade

**Diretório de views**
```php
/resources/views/
```

**Exibindo dados passados para a view**
```php
// Exibindo o valor de uma variável.
{{ $name }}
```

**Passando parâmetro pela URL**
```html
<a href="{{ route('user', 'Thiago') }}">Usuário</a>
```

**IF - ELSE**
```php
@if (auth()->guest())
	Login
@else
	Olá {{ auth()->user()->name }}
@endif
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1OTEzODA5MywtMjEwNTYyMzE2MF19
-->