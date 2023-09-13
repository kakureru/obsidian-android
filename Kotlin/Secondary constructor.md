#kotlin 

Явно или неявно должен вызывать primary constructor

``` kotlin
class Data(val one: Int, val two: Int) {
	constructor(two: Int) : this(one = 0, two)
	constructor() : this(one = 0, two = 0)
}
```

Можно сократить с помощью значений по умолчанию.