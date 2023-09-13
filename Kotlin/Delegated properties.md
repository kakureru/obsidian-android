#kotlin 

Можно определить кастомные геттеры и сеттеры через делегирование:
``` kotlin
class Delegate {
	operator fun getValue()
	operator fun setValue()
}
var x: String by Delegate()
```

Основной usecase:
`by lazy {}`
Блок инициализации выполнится только один раз, когда мы обратимся к свойству, затем будет просто отдаваться кэшированное значение.

[[Delegation]]