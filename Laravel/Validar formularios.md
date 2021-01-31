## Forma 1

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
eyJoaXN0b3J5IjpbOTM4MDI5MzIxXX0=
-->