## Validando formulário dentro do método

```php
public function contact(Request $request)
{
	$this->validade(
		$request,
		'name'    => 'required',
		'email'   => 'required|email',
        // 'email' => ['required', 'email'],
        'message' => 'required|min:5',
	);

	return $request->all();
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUzODQ5ODU1N119
-->