#kotlin 

Соотношение типов.

- Инвариантность - поведение [[Generics]] по умолчанию. И пишем и читаем.
- Ковариантность - используем, если только читаем, писать не можем. Можем использовать наследников указанного типа
``` kotlin
class List<out T> {
	fun get(index: Int): T
	// Нет методов, принимающих T
}
```
- Контрвариантность - используем если только пишем, читать не можем. Можем использовать родителей указанного типа.
``` kotlin
class Consumer<in T> {
	fun accept(param: T)
	// Нет методов, возвращающих T
}
```