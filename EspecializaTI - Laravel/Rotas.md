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
// Opção 1 
Route::get('/sobre', function () {
	return redirect('/visao');
});

// Opção 2 
Route::redirect('/sobre', '/visao');
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg5Njg0NjkzXX0=
-->