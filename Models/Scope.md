
# Scope
## Definindo o scope
O `scope` é definido no model.
**Exemplo:**
```php
public function scopeMale($query)
{
	return $query->where('genre', 'M');
}

public function scopeActive($query)
{
	return $query->where('active', 1);
}
```

## Usando o scope
Usando o `scope` no `controller`.
**Exemplo:**
```php
public function home()
{
	$usersActive = Users::active()->get();
	$usersMale = Users::active()->male()->get();
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg2Njk3NTI2Nl19
-->