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
```php
// Parâmetro obrigatório
Route::get('user/{name}', function ($name) {
	return "Olá {$name}.";
});

// Parâmetro obrigatório
```

```php
Route::get('/', 'UserController@index');

Route::get('/filme/{title?}', function ($title = null) {
	echo "Titulo: {$title}";
})->where('title', "[A-Za-z]+");
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg2MjEzNTY0Nl19
-->