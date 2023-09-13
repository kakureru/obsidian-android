#android

Не может существовать без [[Activity]], когда мы создаём фрагмент, мы его размещаем в контейнер активити. В любом случае, когда есть фрагмент, мы можем обратиться к активити, в которой он находится.

Чем отличается Fragment от Activity?
- Fragment является частью Activity, которая вносит свой собственный интерфейс. Activity может содержать несколько фрагментов. Fragment в основном является частью Activity.
- Activity может содержать 0 или несколько фрагментов на основе размера экрана. Fragment может быть повторно использован в нескольких местах.
- Fragment не может существовать независимо. Он должен быть всегда частью Activity, тогда как Activity может существовать без какого-либо фрагмента в нем.

Фрагменты бывают 
- статические - добавляются через xml, нельзя заменить
``` xml
<LinearLayout
		...>
	<fragment
		...>
	<fragment
		...>
</LinearLayout>
```
- динамические - можно добавлять удалять и заменять
``` kotlin
supportFragmentManager.beginTransaction()
	.add(R.id.fragmentContainer, SomeFragment(), "tag")
	.commit()
```

# Взаимодействие между Fragment и Activity

Передача аргументов - положить в [[Bundle]]:
``` kotlin
val fragment = SomeFragment().apply {
	arguments = bundleOf { SOME_KEY to someValue }
}
```

Получение аргументов - requireArguments()

Вызов метода фрагмента из активити:
``` kotlin
// activity onCreate()
supportFragmentManager.beginTransaction()
	.add(R.id.fragmentContainer, SomeFragment(), "TAG")
	.commit()
(supportFragmentManager.findFragmentByTag("TAG") as? SaomeFragment)?.someMethod()
```

Вызов метода активити из фрагмента - Shared ViewModel или:
1. Создаём интерфейс и реализуем его в активити
``` kotlin
interface FragmentIteractor {
	fun someMethod(someValue: String)
}
```
2. Получаем экземпляр интерфейса во фрагменте
``` kotlin
class SomeFragment : Fragment() {
	private var fragmentIteractor: FragmentInteractor? = null
	
	override fun onAttach(context: Context) {
		super.onAttach(context)
		if (context is FragmetnInteractor) 
			fragmentIteractor = context
	}
	...
		fragmentInteractor?.someMethod("some string")
	...
	override fun onDetach() {
		fragmentIteractor = null
	}
}
```

Жизненный цикл со стейтами:
![[Fragment Lifecycle.png]]
Жц без стейтов, но со всеми методами:

![[Fragment Lifecycle 2.png]]

![[Fragment and Activity Lifecycle.png]]