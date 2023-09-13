#java 

Чтобы перенести наши операции на определенный [[Scheduler]], используем:
- observeOn() - меняет scheduler для всего, что ниже, до этого, если ничего не задано, операции будут выполняться на потоке, в котором произведена подписка. Каждый следующий observeOn заменяет предыдущий.
- subscribeOn() - меняет scheduler с самого верха цепочки. Актуален до первого observeOn. При наличии нескольких subscribeOn актуален только первый.

### Базовые типы

- [[Observable]]
- [[Single]]
- [[Completable]]
- [[Flowable]]
- [[Maybe]]

Виды потоков:
- Холодные - поток начинает отправлять события только после подписки и делает это заново для каждого нового подписчика (just, fromArray, fromCallable*, create*)
- Горячие - отправляет события независимо от подписчиков (ConnectableObservable, [[Subject]])

### Side-effects

Операторы, не меняющие цепочку. Нужны чтобы реагировать на какое либо событие в потоке.
- doOnNext
- doOnError
- doOnComplete
- doOnSubscribe
- и другие

## Операторы 

Модифицируют поведение потока без изменения оригинального:
https://reactivex.io/documentation/operators.html

- map - преобразует каждый элемент
- filter - отсеивает элементы по предикату
- distinct - пропускает только те элементы, которые еще не были отправлены
- distinctUntilChanged - не пропускает одинаковые элементы подряд
- toList - преобразует цепочку элементов в список
![[Operator toList.png]]

### Объединение потоков

- flatMap
``` kotlin
Observable.just("abc", "def")
	.flatMap { str ->
		Observable.fromArray(*str.toTypedCharArray())
	}
		.subscribe { c -> print(c) } // abdcef
```

![[Pasted image 20230620235022.png]]

- concatMap
``` kotlin
Observable.just("abc", "def")
	.concatMap { str ->
		Observable.fromArray(*str.toTypedCharArray())
	}
		.subscribe { c -> print(c) } // abcdef
```

![[Pasted image 20230620235507.png]]

- concat - сначала элементы первого потока, потом второго

![[Pasted image 20230620235647.png]]

- zip - один к одному

![[Pasted image 20230620235713.png]]

- combineLatest - последний элемент из первого с последним элементом из второго

![[Pasted image 20230620235900.png]]

- merge - объединение без гарантии последовательности

![[Pasted image 20230621000025.png]]

- debounce (по дефолту переключает на computation)

![[Pasted image 20230621001741.png]]

- switchMap - откидывает менее актуальные элементы

![[Pasted image 20230621002105.png]]