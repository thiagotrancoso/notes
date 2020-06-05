# Html
Exemplo de html para o ajax.
```html
<a href="javascript:void(0)" class="btn image-delete" 
	data-action="{{ route('admin.image.delete', ['image' => $image->id]) }}">
	Botão
</a>
```

# Ajax
Exemplo de disparo de ação com ajax.
```javascript
$(function () {
	// Configurações do ajax
	$.ajaxSetup({
		headers: {
			'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content')
		}
	})

	$('.image-delete').click(function (event) {
		event.preventDefault()
		var button = $(this)

		$.ajax({
			// Url destino
			url: button.data('action'),
			// Método utilizado para se comunicar: get|post|put|delete ...
			type: 'delete',
			// Tipo da resposta
			dataType: 'json',
			// Se tiver sucesso
			// response = os dados retornados do servidor
			success: function (response) {
				
			}
		})
	})
})
```

# JQuery
`closest` Retorna o elemento pai do elemento acessado.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NjM3MjYwOV19
-->