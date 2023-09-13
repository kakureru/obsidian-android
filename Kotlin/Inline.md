#kotlin 

Проблема:
``` kotlin
fun customRepeat(times: Int, action: () -> Unit) {
	for (i in 1..times) { action() }
}

repeat(10) { println("Hi") } // ~200 microsec
customRepeat(10) { println("Hi") } // ~3500 microsec
```

Так происходит потому что `myRepeat()` транслируется в создание анонимной реализации нашего функционального типа:
``` kotlin
customRepeat(
	times = 10,
	action = object : () -> Unit {
		override fun invoke() { println("Hi") }
	}
)
```

А создание анонимной реализации занимает время на выделение памяти + время garbage коллектора.
Исправить ситуацию позволит `inline`:
``` kotlin
inline fun customRepeat(times: Int, action: () -> Unit) {
	for (i in 1..times) { action() }
}
// тогда:
customRepeat(10) { println("Hi") }
// транслируется в:
for (i in 1..10) { println("Hi") } // тело функции подставляется вместо вызова
```