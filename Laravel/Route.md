
```php
Route::get('/', function () {
	echo 'Teste';
});

Route::get('/', 'UserController@index');

Route::get('/filme/{title?}', function ($title = null) {
	echo "Titulo: {$title}";
});
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM2NDAwMzIzMF19
-->