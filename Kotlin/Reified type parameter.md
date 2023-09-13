#kotlin 

Данный код не сработает
``` kotlin
fun <T> printClassName() {
	val className = T::class.java.name
	println("Class name = $className")
}
```
потому что при стирании типов мы получим
``` kotlin
fun printClassName() {
	val className = Any::class.java.name
	...
}
```

Решение - reified:
``` kotlin
inline fun <reified T> printClassName() { ... }
```

Reified говорит компилятору "Не стирай наши [[Generics]], нам надо с ними поработать". Reified не работает без [[Inline]]

В итоге с reified из такого кода:
``` kotlin
printClassName<String>()
printClassName<Int>()
```
Мы получим:
``` kotlin
val className = String::class.java.name
println("Class name = $className")
val className = Int::class.java.name
println("Class name = $className")
```
