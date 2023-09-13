#java 

После компиляции дженерики преобразуются в [[Сырой тип]], а в обращениях появляется каст. Это называется стирание типов / type erasure.

Таким образом данный код не скомпилируется:
``` kotlin
interface Consumer<T> {
	fun accept(param: T)
}

class MyClass : Consumer<String>, Consumer<Integer> {
	override accept(param: String) {}
	override accept(param: Integer) {}
}
```
так как после компиляции мы получим два одинаковых метода:
``` kotlin
interface Consumer<T> {
	fun accept(param: T)
}

class MyClass : Consumer, Consumer {
	override accept(param: Any?) {}
	override accept(param: Any?) {}
}
```