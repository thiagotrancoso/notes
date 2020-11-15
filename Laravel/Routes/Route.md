### Exemplos:
Sintaxe:

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
eyJoaXN0b3J5IjpbLTQyNTY2NTk5Ml19
-->