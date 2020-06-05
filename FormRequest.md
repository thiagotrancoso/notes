# FormRequest
Exemplo:
```php
namespace App\Http\Requests;

use Illuminate\Foundation\Http\FormRequest;

class ExemploRequest extends FormRequest
{
	/**
	 * Determina se o usuário está autorizado a fazer o request.
	 * @return bool
	 */
	public function authorize()
	{
		return Auth::check();
	}
	
	/**
	 * Regras de validação aplicadas ao request.
	 * 
	 * @return array
	 */
	public function rules()
	{
		return [
			'prop_1' => 'required',
			'prop_2' => 'required|different:prop_1',
			'prop_3' => 'required_if:prop_1,on',
		];
	}
}
```
```
required
required_if:{propriedade},{valor}
different:{propriedade}
integer
min:{numero_minimo}
max:{numero_maximo}
```

# Controller
Exemplo:
```php
namespace App\Http\Controllers\Admin;

use App\Http\Controllers\Controller;
use App\Http\Requests\ExemploRequest;
use Illuminate\Http\Request;

class ExemploController extends Controller
{
	...
	
	/**
	 * Exemplo de método usando o FormRequest
	 * 
	 * @param \App\Http\Requests\ExemploRequest $request
	 * @return \Illuminate\Http\Response
	 */	
	public function exemplo(ExemploRequest $request)
	{
		// Se as informações do request não passarem pela validação dentro do FormRequest, o laravel redirecionará para a página anterior.
	}
	
	...
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk4NTg0MzkwNl19
-->