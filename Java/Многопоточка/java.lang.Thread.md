#java 

Запуск фонового потока:
``` java
Thread thread = new Thread(new Runnable() {
	@Override
	public void run() { ... }
});
thread.start;
```

Работа с UI:
``` java
runOnUiThread(new Runnable() {
	@Override
	public void run() { ... }
})
```
или
``` java
view.post(new Runnable() {
	@Override
	public void run() { ... }
})
```

Следующий код вызовет утечку памяти:
``` java
Thread thread = new Thread(new Runnable() {
	@Override
	public void run() { 
		String data = loadData()
		runOnUiThread(new Runnable() {
			@Override
			public void run() { 
				textView.setText(data)
			}
		})
	}
});
thread.start;
```
так как на самом деле это:
``` java
MainActivity.this.runOnUiThread(new Runnable() {
	@Override
	public void run() { 
		MainActivity.this.textView.setText(data)
	}
})
```
и поток продолжит выполняться при пересоздании активити, и ссылка на неё останется.

Правильно было бы так:
``` java
public class Downloader {
	private final WeakReference<Callback> callback;
	
	public Downlader(Callback callback) {
		this.callback = new WeakReference<>(callback);
	}
	
	public void load() {
		new Thread(new Runnable() {
			@Override
			public void run() { 
				String data = loadData();
				if (callback.get() != null) {
					callback.get().setResult(data);
				}
			}
		}).start();
	}
	
	interface Callback() {
		void setResult(String result);
	}
}
```