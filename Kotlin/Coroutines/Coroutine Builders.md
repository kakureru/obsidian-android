#kotlin 

Используются для запуска корутин.

[[Coroutine Scope]]
[[Coroutine Context]]

launch:
``` kotlin
public fun CoroutineScope.launch(
	context: CoroutineContext = EmptyCoroutineContext,
	start: CoroutineStart = CoroutineStart.DEFAULT,
	block: suspend CoroutineScope.() -> Unit
): Job
```

async:
``` kotlin
public fun CoroutineScope.async(
	context: CoroutineContext = EmptyCoroutineContext,
	start: CoroutineStart = CoroutineStart.DEFAULT,
	block: suspend CoroutineScope.() -> Unit
): Deffered<T>
```
[[Deferred]].await() возвращает результат блока. 

CoroutineStart.DEFAULT - корутина стартует автоматически при её создании.
CoroutineStart.LAZY- корутина стартует только после явного запуска.

![[Pasted image 20230621133907.png]]
