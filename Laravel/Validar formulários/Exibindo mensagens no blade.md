```php
// Obtém o primeiro erro de um campo
{{ $errors->first('name') }}
{!! $errors->first('name', '<span class="error">:name</span>') !!}

// Persistir a informação de um campo
{{ old('name') }}

// Exibindo mensagem que está na sessão
@if(session()->has('info'))
	{{ session('info') }}
@endif
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY0MDk1MjM1OF19
-->