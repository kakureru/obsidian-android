#android 

Объявляется контракт, одна [[Activity]] запускает другую через этот контракт, эта вторая активити что-то складывает в setResult, и первая их получает.

``` kotlin
val secondActivityResult = 
registerForActivityResult(StartActivityForResult()) { result ->
	if(result.resultCode == Activity.RESULT_OK) {
		// Do something
	}
}

button.setOnClickListener {
	secondActivityResult.launch(Intent(context, SecondActivity::class.java))
}
```

[[Intent]]