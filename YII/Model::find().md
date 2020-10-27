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
print_r($command->params);

// retorna todas as linhas do resultado da query
$rows = $command->queryAll();
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAxNzQ4MDAwN119
-->