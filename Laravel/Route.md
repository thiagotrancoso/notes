# Rotas

**Arquivo de rotas**
```php
/routes/web.php
```

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
```php
// Ex: não permitir que seja passado números pelo parâmetro.

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

**Exibindo uma view do blade**
```php
Route::get('/', function () {
	return view('nome-da-view');
});
```

**Enviando dados para a view**
```php
Route::get('user/{name?}', function ($name = 'convidado') {
	// Formas de passar dados para a view
	// return view('user', ['name' => $name]);
	// return view('user')->with(['name' => $name]);
	// return view('user', compact('name'));
});
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA1MjE5MzMwMiwtMTY0MDY4MDk0OV19
-->