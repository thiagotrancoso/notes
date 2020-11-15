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
		$table->string('email')->unique();
		$table->string('password');
		$table->rememberToken();
		$table->timestamps();
	});
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MTIzMDA2MDYsLTE0ODAwODE2ODYsMj
EzODcwNjM3Nl19
-->