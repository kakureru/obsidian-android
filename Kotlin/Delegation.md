#kotlin 

``` kotlin
interface Base {
	fun print()
}

class BaseImpl(val x: Int) : Base {
	override fun print() { print(x) }
}

class Example(base: Base) : Base by base

val b = BaseImpl(10)
Example(b).print() // output: 10
```

Удобно тем, что можно переопределить только часть методов и делегировать реализацию остальных.