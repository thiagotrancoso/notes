## Validando formulário dentro do método

```php
public function contact(Request $request)
{
	$this->validade(
		$request,
		'name'  => 'required',
		'email' => 'required|email',
        // 'email' => ['required', 'email'],
	);

	return $request->all();
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM5MzM3NDI5M119
-->