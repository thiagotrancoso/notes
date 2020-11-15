## Rotas
**Sintaxe:**
`$param1` URL que deseja acessar.
`$param2` Closure.
```php
Route::get($param1, $param2);
```

## Exemplos
```php
Route::get('/', function () {
	return 'Olá esta é a página home.';
});

Route::get('sobre', function () {
	return 'Olá esta é a página sobre.';
});
```

### Passando parâmetros pela url
**Parâmetro obrigatório**
```php
Route::get('user/{name}', function ($name) {
	return "Olá {$name}.";
});
```

**Parâmetro opcional**
```php
Route::get('user/{name?}', function ($name = 'convidado') {
	return "Olá {$name}.";
});
```

**Validar parâmetro**
Valida parâmetro com expressão regular.
Ex: não permitir que seja passado números pelo parâmetro.
```php
Route::get('/filme/{title?}', function ($title = null) {
	echo "Titulo: {$title}";
})->where('title', "[A-Za-z]+");
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbNDAxNjA2Nzk1XX0=
-->