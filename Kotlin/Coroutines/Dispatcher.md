#kotlin 

Аналог [[Scheduler]]

- Default - для интенсивных операций, количество потоков в пуле равно количеству ядер
- IO - для операций ввода-вывода, кол-во потоков в пуле не менее 64
- Main - для выполнения операций на главном потоке
- Unconfined - выполнение в том же потоке, в котором происходит запуск