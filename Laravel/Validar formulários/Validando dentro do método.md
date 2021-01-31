## Validando formulário dentro do método

```php
public function contact(Request $request)
{
	$this->validade(
		$request,
		'name'    => 'required',
		'email'   => 'required|email',
        // 'email' => ['required', 'email'],
        'mensage' => 'required|min:5',
	);

	return $request->all();
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA5NDk4NjI5Nl19
-->