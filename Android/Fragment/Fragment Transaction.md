#android 

Операции управления фрагментами выполняются внутри транзакции
Можно сохранить в back-stack - `addBackStack(tag: String?)`

Для выполнения транзакции необходимо вызвать один из commit-методов:
- commit() - асинхронное выполнение транзакции
- commitNow() - синхронное выполнение транзакции без возможности добавления в back-stack
- commitAllowingStateLoss() - асинхронная транзакция с возможностью выполнения вызова после Activity.onSavedInstanceState
- commitNowAllowingStateLoss() - синхронная транзакция с возможностью выполнения после Activity.onSavedInstanceState

Eсли случится ошибка, всё просто откатится к предыдущему фрагменту/