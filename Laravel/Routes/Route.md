
```php
Route::get('/', function () {
	echo 'Teste';
});

Route::get('/', 'UserController@index');

Route::get('/filme/{title?}', function ($title = null) {
	echo "Titulo: {$title}";
})->where('title', "[A-Za-z]+");
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA5NzAyNDI0MF19
-->