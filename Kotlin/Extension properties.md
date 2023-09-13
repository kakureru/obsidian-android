#kotlin 

``` kotlin
val Int.isEven: Boolean = 
	get() = this % 2 == 0

var <T> Array<T>.firstElement: T
	get() = this[0]
	set(value) {
		this[0] = value
	}
```

Не имеет backing field, поэтому не может хранить никакие значения.