#android 

### Fragment Result Listener

Предоставляет интерфейс для централизованного взаимодействия между фрагментами путем передачи аргументов через [[FragmentManager]] по ключу

- Если фрагмент подпишется на результат после того, как другой фрагмент вызовет setFragmentResult(), то он немедленно получит результат.
- Каждую связку "Key + Result (Bundle)" слушатель получает только один раз.
- Фрагменты из бек-стека получат результат только после того, как перейдут в состояние onStart()
- После того, как фрагмент перейдет в состояние onDestroy(), подписаться на ResultListener нельзя.

Создаём слушателя:
``` kotlin
override fun onCreate(savedInstanceState: Bundle?) {
	super.onCreate(savedInstanceState)
	setFragmentResultListener(REQUEST_KEY) { key, bundle ->
		val result = bundle.getString(RESULT_KEY)
		// do something with result
	}
}
```

Устанавливаем результат:
``` kotlin
button.setOnClickListener {
	val result = "result string"
	setFragmentResult(REQUEST_KEY, bundleOf(RESULT_KEY to result))
}
```

![[Fragment Result Listener child.png]]

Создаём слушателя:
``` kotlin
override fun onCreate(savedInstanceState: Bundle?) {
	super.onCreate(savedInstanceState)
	childFragmentManager.setFragmentResultListener(REQUEST_KEY) { key, bundle ->
		val result = bundle.getString(RESULT_KEY)
		// do something with result
	}
}
```

![[Pasted image 20230619130658.png]]