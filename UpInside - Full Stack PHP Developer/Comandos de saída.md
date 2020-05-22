# Comandos de saída
- echo
- print
- print_r
- printf
- sprintf
- vprintf
- vsprintf
- var_dump

### echo
```php
echo "<p>Olá Mundo!", " ", "Estou estudando programação.", "</p>";
// Olá Mundo!, Estou estudando programação.
```

### print
```php
print "<p>Olá Mundo! Estou estudando programação.</p>";
// Olá Mundo!, Estou estudando programação.
```

### print_r
```php
$array = [
	'a' => 'Valor 1',
	'b' => 'Valor 2',
	'c' => 'Valor 3',
];
print_r($array);
// Array
// (
//     [a] => Valor 1
//     [b] => Valor 2
//     [c] => Valor 3
// )
```

### printf
```php
$title = "O filme %s tem %s minutos de duração";
printf($title, 'O Senhor dos Anéis', '180');
// O filme O Senhor dos Anéis tem 180 minutos de duração
```

### sprintf
```php
$title = "O filme %s tem %s minutos de duração";
$movie = sprintf($title, 'O Senhor dos Anéis', '180');
echo $movie;
// O filme O Senhor dos Anéis tem 180 minutos de duração
```

### vprintf
```php
$array = ['A', 'B', 'C', 'D', 'E'];
$text = "Letras %s, %s, %s, %s, %s";
vprintf($text, $array);
// Letras A, B, C, D, E
```

### vsprintf
```php
$array = ['A', 'B', 'C', 'D', 'E'];
$text = "Letras %s, %s, %s, %s, %s";
$result = vsprintf($text, $array);
echo $result;
// Letras A, B, C, D, E
```

### var_dump
```php
$array = ['A', 1, true];
var_dump($array);
// array (size=3)
//     0 => string 'A' (length=1)
// 	   1 => integer (length=1)
// 	   2 => boolean true
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMzg2MTkwNDQzXX0=
-->