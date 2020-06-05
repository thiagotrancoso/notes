## Validando o upload de múltiplas imagens
```php
$validator = Validator::make($request->only('files'), ['files.*' => 'image']);

if ($validator->fails() === true) {
	return redirect()->back()->withInput()->with([
		'color' => 'orange',
		'message' => 'Todas as imagens devem ser do tipo JPG ou PNG',
	]);
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU1NjYzNjY0M119
-->