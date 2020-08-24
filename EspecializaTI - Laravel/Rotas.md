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
Route::get('/');
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk4MDIyNDg2OV19
-->