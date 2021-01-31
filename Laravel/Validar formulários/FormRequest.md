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
	$data = $request->all();
	
	return redirect()
		->route('contact')
		->with('info', 'Mensagem enviada com sucesso!');
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbODQ1MjM1NDMwLDU2NDUyODA2NF19
-->