#java 

- Типизированный поток данных, потенциально бесконечный
- onNext(T) - вызывается на каждый новый элемент в потоке
- onComplete - окончание потока. После onComplete поток завершается.
- onError(Throwable) - вызывается при ошибке. После него поток завершается.

## Создание потоков

- [[from]], [[just]]
- create - нужно следить за жц потока, не стоит использовать в своих проектах.
- наследование - наследоваться от потока и в subscribeActual() вызывать методы жц. Тоже не особо актуальный вариант.