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

Route::get('contato', function () {
	return 'Olá esta é a página de contato.';
});
```

```php

```

```php
Route::get('/', 'UserController@index');

Route::get('/filme/{title?}', function ($title = null) {
	echo "Titulo: {$title}";
})->where('title', "[A-Za-z]+");
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4MTYyMTMzODldfQ==
-->