#android 

Handler используется для связи между потоками, чаще всего для передачи действия из фонового потока в основной поток Android (вы не можете обновлять пользовательский интерфейс из любого потока, кроме основного). 
Handler производит обработку сообщений из MessageQueue по их содержимому.  

Асинхронное выполнение работы с помощью Handler:
``` java
public static final int SEND_RESULT = 1

Handler handler = new Handler(getMainLooper(), 
	new Handler.Callback() {
		@Override
		public boolean handleMessage(Message msg) {
			if (msg.what == SEND_RESULT) {
				String data = (String) msg.obj
				textView.setText(data)
			}
			return true;
		}});

public void load() {
	new Thread(() -> {
		String data = loadData();
		Message message = handler.obtainMessage(SEND_RESULT, data);
		handler.sendMessage(message);
	}).start();
}
```
