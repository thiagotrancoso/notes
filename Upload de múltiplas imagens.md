# Upload de múltiplas imagens
### Script JS na view
Script para exibir as imagens selecionadas no input type file.
```javascript
<script>
	$(function () {
		$('input[name="files[]"]').change(function (files) {
			// Limpa o conteúdo da div ".content_files"
			$('.content_files').text('')

			// Foreach para cada arquivo selecionado
			$.each(files.target.files, function (key, value) {
				// O "FileReader" lê o arquivo
				var reader = new FileReader()
				reader.onload = function (value) {
					$('.content_files').append(
						'<div class="file_item">' +
						'<div class="embed radius" ' +
						'style="background-image: url(' + value.target.result + '); background-size: cover; background-position: center center;">' +
						'</div>' +
						'</div>'
					)
					reader.readAsDataURL(value)
				}
			})
		})
	})
</script>
```

# Controller
Controlador responsável por fazer o upload das imagens.
```php
/**
 * Faz o upload de múltiplos arquivos
 *
 * @param Request $request
 * @return void
 */
public function store(Request $request)
{
    $files = isset($request->allFiles()['files']) ? $request->allFiles()['files'] : [] ;

    if (! $files)
        return redirect()->back()->with('alert-warning', 'Não foi possível fazer o upload');

    foreach ($files as $file) {
        $originalNameWithExtension = $file->getClientOriginalName();
        $originalExtension = $file->getClientOriginalExtension();

        $originalName = str_replace(".{$originalExtension}", '', $originalNameWithExtension);
        $imageExists  = Storage::exists("uploads/{$originalNameWithExtension}");

        if ($imageExists) {
            $images = Storage::files('uploads');

            $count = 1;
            foreach ($images as $image) {
                if ($image == $originalNameWithExtension)
                    $count++;
            }

            $file->storeAs('uploads', "{$originalName}-{$count}.{$originalExtension}");
        } else {
            $file->storeAs('uploads', "{$originalNameWithExtension}");
        }
    }

    return redirect()->route('admin.midia.index')->with('alert-success', 'Upload concluído com successo');
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTIwMDQwNjE2XX0=
-->