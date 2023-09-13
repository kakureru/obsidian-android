Помогает реализовать принцип [[Dependency invertion]]

### @Inject 

Требует предоставления зависимости в:
- Поле
- Конструктор
- Метод

### @Reusable 

Объект может храниться как синглтон, но при недостатке памяти Dagger его убьёт
- Среднее между scoped и unscoped
- Экономит память 
- Для state-less объектов
- Для каждого компонента кэшируется отдельно 

### @Qualifier

``` kotlin
@Qualifier
annotation class SomeQualifier

@Provides
@SomeQualifier
fun provideSomething(): SomeType

class SomeClass @Inject constructor(
	@SomeQualifier
	private val someValue: SomeType
)
```

### Lazy 

Обычный lazy только даггеровский. Объект отложенно создастся только один раз и потом будет переиспользоваться.

``` kotlin
class SomeClass @Inject constructor(
	private val lazyClient: Lazy<OkHttpClient>
) {
	fun someFun() {
		val client = lazyClient.get()
		...
	}
}
```

### Provider

То же самое, что и Lazy, только объект будет создаваться при каждом вызове заново.

``` kotlin
class SomeClass @Inject constructor(
	private val clientProvider: Provider<OkHttpClient>
) {
	fun someFun() {
		val client = clientProvider.get()
		...
	}
}
```

### Multibindings

@IntoSet
@IntoMap + @MapKey (@StringKey)

Возвращаемые объекты соберутся в коллекцию

