```php
$user = User::find()
	->alias('u')
	->select('id', 'name', 'email')
	->innerJoin(table, on)
	->where(['id' => 20])
	->limit(10)
	->createCommand();

// mostra a instrução SQL
echo $user->sql;

// Mostra os parâmetros que serão ligados
print_r($user->params);

// retorna todas as linhas do resultado da query
$rows = $user->queryAll();

// ->queryAll()
// ->queryOne()
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NzgzMTAxNDZdfQ==
-->