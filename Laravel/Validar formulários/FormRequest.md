### Comando para criar
```
php artisan make:request MessageRequest
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcxNTkxNTg1OV19
-->