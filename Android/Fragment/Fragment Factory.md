#android 

Позволяет сделать [[Fragment]] со своими кастомными конструкторами.

``` kotlin
class FragmentFactoryImpl(val message: String): FragmentFactory() {
	override fun instatiate(classLoader: ClassLoader, className: String): Fragment {
		return when (className) {
			MessageFragment::class.java.name -> MessageFragment(message)
			else -> super.instantiate(classLoader, className)
		}
	}
}
```

``` kotlin
// activity onCreate()
supportFragmentManager.fragmentFactory = FragmentFactoryImpl("HelloWorld")
```