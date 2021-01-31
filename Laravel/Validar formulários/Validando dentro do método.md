## Validando formulário dentro do método

```php
public function contact(Request $request)
{
	$this->validade(
		$request,
		'name'  => 'required',
		'email' => 'email',
	);

	return $request->all();
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU5NTQyNjYwMF19
-->