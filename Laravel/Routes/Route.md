### Exemplos:
```php
Route::get('/', function () {
	echo 'Teste';
});
```

```php

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
eyJoaXN0b3J5IjpbLTMyMzQ3MDA2Ml19
-->