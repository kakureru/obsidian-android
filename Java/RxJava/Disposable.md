#java 

Интерфейс, описывающий логику по освобождению ресурсов
``` java
public interface Disposable {
	void dispose();
	boolean isDisposed();
}
```

## Composite Disposable

Объект, в который мы складываем все свои disposable'ы, чтобы при выходе с экрана всех их разом очистить.

``` kotlin
class MyActivity : Activity() {
	private val compositeDisposable = CompositeDisposable()
	
	override fun onCreate() {
		val disposable = Observable.just(2 + 2 * 2)
			.subscribe(...)
		compositeDisposable.add(disposable)
	}
	
	override fun onDestroy() {
		super.onDestroy()
		compositeDisposable.clear()
	}
}
```