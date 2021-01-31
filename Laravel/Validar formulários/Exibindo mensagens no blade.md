```php
// Obtém o primeiro erro de um campo
{{ $errors->first('name') }}
{!! $errors->first('name', '<span class="error">:name</span>') !!}

// Persistir a informação de um campo
{{ old('name') }}

@if()
@
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA1NzM5OTI1Ml19
-->