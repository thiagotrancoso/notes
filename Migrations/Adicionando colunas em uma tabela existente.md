# Alterando uma tabela
## Comando
```bash
#. Sintaxe
$ php artisan make:migration {nome_da_migration} --class={nome_da_tabela}

#. Comando
$ php artisan make:migration add_status_to_users_table --class=users
```

## Migration
```php
use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

class AddStatusToUsersTable extends Migration
{
	/**
	 * Executa a migração.
	 * 
	 * @return void
	 */
	 public function up()
	 {
		 Schema::table('users', function (Blueprint $table) {
			 $table->string('status', 100);
		 });
	 }
	 
	/**
	 * Reverte a migração.
	 * 
	 * @return void
	 */
	 public function down()
	 {
		 Schema::table('users', function (Blueprint $table) {
			 $table->dropColumn('status');
		 });
	 }
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNTk2NTE3NDNdfQ==
-->