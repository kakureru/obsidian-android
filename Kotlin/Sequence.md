#kotlin 

Например нужно рассчитать длину первых 4 слов, длиннее 3-х букв:
``` kotlin
val words = "The quick brown fox jumps over the lazy dog".split(" ") 
```

Iterable:
``` kotlin
val lengths = words
	.filter { println("filter: $it"); it.length > 3 } 
	.map { println("length: ${it.length}"); it.length } 
	.take(4) 
println(lengths) // [5, 5, 5, 4]
```

![[Iterable scheme.png]]

Sequence:
``` kotlin
val lengths = words.asSequence()
	... // та же обработка
// terminal operation: obtaining the result as a List
println(lengths.toList()) // [5, 5, 5, 4]
```

![[Sequence scheme.png]]