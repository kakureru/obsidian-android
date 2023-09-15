### remember

Запоминает значение через рекомпозицию

``` kotlin
var text by remember { "" }
```

### rememberSaveable

Запоминает значение через смену конфигурации и тп.

``` kotlin
var text by rememberSaveable { "" }
```

### rememberCoroutineScope

As LaunchedEffect is a composable function, it can only be used inside other composable functions. In order to launch a coroutine outside of a composable, but scoped so that it will be automatically canceled once it leaves the composition, use rememberCoroutineScope. Also use rememberCoroutineScope whenever you need to control the lifecycle of one or more coroutines manually, for example, cancelling an animation when a user event happens.

Using the `rememberCoroutineScope` API returns a `CoroutineScope` bound to the point in the Composition where you call it. Скоуп автоматически закроется как только покинет композицию.

``` kotlin
@Composable
fun MoviesScreen(
snackbarHostState: SnackbarHostState
) {
    // Creates a CoroutineScope 
    // bound to the MoviesScreen's
    // lifecycle
    val scope = rememberCoroutineScope()

    Scaffold(
        snackbarHost = {
            SnackbarHost(hostState = snackbarHostState)
        }
    ) { 
        Button(
            onClick = {
                    // Create a new coroutine in the event handler to show a snackbar
                    scope.launch {
                        snackbarHostState.showSnackbar("Hello!")
                    }
                }
            ) {
                Text("Press me")
        }
    }
}
```

### rememberUpdatedState

You should use `rememberUpdatedState` when a long-lived lambda or object expression references parameters or values computed during composition

### collectAsStateWithLifecycle

collects values from the `StateFlow` and represents the latest value via Compose's [State](https://developer.android.com/reference/kotlin/androidx/compose/runtime/State "‌") API in a lifecycle-aware manner. This will make the Compose code that reads that state value recompose on new emissions.

### produceState

If you wanted to move the `uiState`mapping logic to the Compose world, you could use the `produceState` API.

`produceState` allows you to convert non-Compose state into Compose [State](https://developer.android.com/reference/kotlin/androidx/compose/runtime/State "‌"). It launches a coroutine scoped to the Composition that can push values into the returned `State` using the `value` property. As with `LaunchedEffect`, `produceState` also takes keys to cancel and restart the computation.

```kotlin
    val uiState by produceState(initialValue = DetailsUiState(isLoading = true)) {
        val cityDetailsResult = viewModel.cityDetails
        value = if (cityDetailsResult is Result.Success<ExploreModel>)
            DetailsUiState(cityDetailsResult.data)
        else
            DetailsUiState(throwError = true)
    }
```

### derivedStateOf

Use `derivedStateOf` when you want a Compose `State` that's derived from another `State`. The `derivedStateOf`calculation block is executed every time the internal state changes, but the composable function only recomposes when the result of the calculation is different from the last one. This minimizes the amount of times functions reading new state recompose.

### snapshotFlow

The `snapshotFlow` **API** converts Compose `State<T>` objects into a [Flow](https://developer.android.com/kotlin/flow "‌"). When the state read inside `snapshotFlow` mutates, the Flow will emit the new value to the collector.
