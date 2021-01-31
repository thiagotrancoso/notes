```php
// Obtém o primeiro erro de um campo
{{ $errors->first('name') }}
{!! $errors->first('name', '<span class="error">:name</span>') !!}

// Persistir a informação de um campo
{{ old('name') }}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY5NjUxMjczNiwyMDM0ODE0MjddfQ==
-->