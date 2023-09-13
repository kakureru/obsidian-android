#kotlin

- Позволяет проверять состояние корутин во время выполнения
- Позволяет завершать выполнение корутин
- Сигнализирует об ошибках
- Поддерживает принцип Structured Concurrency:
	- отмена scope - отмена запущенных в нем корутин
	- имеет ссылки на все запускаемые в нем корутины
	- ждет завершения всех дочерних корутин
- Нужно закрывать функцией cancel(), когда он не нужен

``` kotlin
public interface CoroutineScope {
	public val coroutineContext: CoroutineContext
}
```

[[Coroutine Context]]

Создание Coroutine Scope с помощью фабричной функции:
``` kotlin
val scope = CoroutineScope(CoroutineName("some name") + Job())
```
Переданные параметры преобразуются в Coroutine Context - map из CoroutineName и Job

``` kotlin
scope.launch {
	println(coroutineContext[CoroutineName]?.name) // "some name"
}

scope.launch(CoroutineName("child name")) {
		println(coroutineContext[CoroutineName]?.name) // "child name"
}
```