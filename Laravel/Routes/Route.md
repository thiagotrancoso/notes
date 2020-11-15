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
	return 'Página home.';
});

Route::get('sobre', function () {
	return 'Página sobre.';
});
```

### Passando parâmetros pela url
**Parâmetro obrigatório**
```php
Route::get('user/{name}', function ($name) {
	return "Olá {$name}.";
});
```

**Parâmetro opcional**
```php
Route::get('user/{name?}', function ($name = 'convidado') {
	return "Olá {$name}.";
});
```

**Validar parâmetro**
Valida parâmetro com expressão regular.
Ex: não permitir que seja passado números pelo parâmetro.
```php
Route::get('user/{name?}', function ($name = 'convidado') {
	return "Olá {$name}";
})->where('title', "[A-Za-z]+");
```

**Nomear rotas**
```php
Route::get('contato', function () {
	return 'Página de contato.';
})->name('contact');
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTQ1NDA5NjAxXX0=
-->