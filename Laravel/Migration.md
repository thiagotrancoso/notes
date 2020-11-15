```php
// Criando tabela
$ php artisan make:migration create_messages_table --create=messages

// Alterando tabela
$ php artisan make:migration add_phone_to_messages_table --table=messages
```

```php
public function up ()
{
	Schema::create('users', function (Blueprint $table) {
		$table->increments('id');
		$table->string('name');
		$table->string('email')->uniq;
		$table->string('');
		$table->string('');
		$table->string('');
	});
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcyNDE3OTIwMSwtMTQ4MDA4MTY4NiwyMT
M4NzA2Mzc2XX0=
-->