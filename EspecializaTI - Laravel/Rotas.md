## Rotas
### Parâmetros obrigatórios
```php
Route::get('/categoria/{category}/posts', function ($category) {
});
```
### Parâmetros opcionais
```php
Route::get('/produtos/{id?}', function ($id = 'false') {
});
```
### Redirecionar rotas
```php
Route::get('/sobre', function () {
	return redirect('/visao');
});
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMzNzc4MTUxMF19
-->