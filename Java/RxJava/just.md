[[Disposable]]

Создает поток из одного элемента. Значение в скобках вычисляется сразу при создании потока.

Создаем поток:
``` kotlin
val observable = Observable.just(2 + 2 * 2)
```
Подписываемся:
``` kotlin
observable.subscribe(object : Observable<Int> {
	override fun onSubscribe(d: Disposable) = ...
	override fun onNext(t: Int) = ...
	override fun onError(e: Throwable) = ...
	override fun onComplete() = ...
})
```
Хорошая практика - всегда переопределять onError, иначе будем ловить краш.