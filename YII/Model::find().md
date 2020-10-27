```php
$user = User::find()
	->select(['id', 'email'])
	->from('user')
	->where(['last_name' => 'Smith'])
	->limit(10) ->createCommand();

// mostra a instrução SQL
echo $command->sql;

// Mostra os parâmetros que serão ligados
print_r($command->params);

// retorna todas as linhas do resultado da query
$rows = $command->queryAll();
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU3ODcxNjM4OV19
-->