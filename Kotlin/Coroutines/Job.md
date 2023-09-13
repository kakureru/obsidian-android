#kotlin  

- Получаем при вызове корутины
- Позволяет узнать статус корутины
- Позволяет завершить работу корутины

Единственный наследник CoroutineContext.Element, который не наследуется, родительские Job используются для родственной связи корутин, которая и обеспечивает strucruted concurrency.
Корректное поведение корутин ломается, если передать в аргумент корутин-билдера неродительскую Job.

### Связь Job:

- Запускаемые корутины находятся в отношении родитель-ребенок. Поддерживается эта связь при помощи Job.
- Стартовой Job является Job Coroutine Scope'а
- Родительская Job будет ждать пока выполнятся все дочерние корутины
- При завершении родительской Job, отменятся все дочерние корутины

![[Job lifecycle.png]]

Ошибка в Job приводит к завершению родительской Job:
![[Pasted image 20230621142524.png]]

Чтобы предотвратить такое поведение, используется Supervisor Job - cпециальный вид Job, завершение которого не приведет к завершению родительской Job. 
- Может быть создан фабричной функцией
- По умолчанию используется в SupervisorScope