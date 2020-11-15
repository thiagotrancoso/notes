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
Route::get('user/', function () {
	return 'Olá esta é a página sobre.';
});
```

```php
Route::get('/', 'UserController@index');

Route::get('/filme/{title?}', function ($title = null) {
	echo "Titulo: {$title}";
})->where('title', "[A-Za-z]+");
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc2OTM4MTk0NV19
-->