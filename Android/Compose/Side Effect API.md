
**A side-effect in Compose is a change to the state of the app that happens outside the scope of a composable function.** For example, opening a new screen when the user taps on a button, or showing a message when the app doesn't have Internet connection.

## LaunchedEffect

To call suspend functions safely from inside a composable, use the `LaunchedEffect` API, which triggers a coroutine-scoped side-effect in Compose.

When `LaunchedEffect` enters the Composition, it launches a coroutine with the block of code passed as a parameter. The coroutine will be canceled if `LaunchedEffect` leaves the composition.

## DisposableEffect

You need a side effect that tells you when the effect is leaving the Composition so that you can perform some cleanup code? The side-effect API you're looking for is `DisposableEffect`.

`DisposableEffect` is meant for side effects that need to be cleaned up after the keys change or the composable leaves the Composition.

## LaunchedEffect vs rememberCoroutineScope

Using `LaunchedEffect` in this case wasn't possible because you needed to trigger the call to create a coroutine in a regular callback that was outside of the Composition.

Looking back at the landing screen step that used `LaunchedEffect`, could you use `rememberCoroutineScope` and call `scope.launch { delay(); onTimeout(); }` instead of using `LaunchedEffect`?

You could've done that, and it would've seemed to work, but it wouldn't be correct. As explained in the [Thinking in Compose documentation](https://developer.android.com/jetpack/compose/mental-model#any-order "‌"), composables can be called by Compose at any moment. `LaunchedEffect` guarantees that the side-effect will be executed when the call to that composable makes it into the Composition. If you use `rememberCoroutineScope` and `scope.launch` in the body of the `LandingScreen`, the coroutine will be executed every time `LandingScreen` is called by Compose regardless of whether that call makes it into the Composition or not. Therefore, you'll waste resources and you won't be executing this side-effect in a controlled environment.