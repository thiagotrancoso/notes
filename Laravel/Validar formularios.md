## Forma 1

```php
public function contact(Request $request)
{
	$this->validade(
		$request,
		'name' => 'required'
	);
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUxNTAxNjg5OV19
-->