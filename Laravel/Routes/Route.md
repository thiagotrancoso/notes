### Exemplos:
Sintaxe:
`$param2` = Endereço a ser acessado.
`$param2` = Closure.
```php
Route::get($param1, $param2);
```

```php
Route::get('/', function () {
	echo 'Teste';
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
eyJoaXN0b3J5IjpbLTExNTQ2OTM5NjhdfQ==
-->