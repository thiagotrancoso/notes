### Comando para criar
```
php artisan make:request ContactRequest 
```

### Modelo da classe
```php
public function authorize()
{
	// Define se o usuário está autorizado para enviar o formulário
	return true;
}

public function rules()
{
	return [
			'name'    => 'required',
			'email'   => 'required|email',
	        // 'email' => ['required', 'email'],
	        'message' => 'required|min:5',
	];
}
```

#### Usando a classe form request
```php
public function contact(ContactRequest $request)
{
	return $request->all();
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTY0NTI4MDY0XX0=
-->