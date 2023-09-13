#android 

Внешнее хранилище телефона (SD карта)

- Не всегда доступно, необходимо проверять доступность:
``` kotlin
Environment.getExternalStorageState() in setOf(
	Environment.MEDIA_MOUNTED // хранилище доступно для чтения/записи
	Environment.MEDIA_MOUNTED_READ_ONLY // хранилище доступно только для чтения
)
```
- Доступен для чтения сторонним приложениям
- Требуются разрешения на запись/чтение: WRITE_EXTERNAL_STORAGE и READ_EXTERNAL_STORAGE

Разрешение на запись неявно дает разрешение на чтение
Начиная с API 19 чтение и запись из приватного внешнего хранилища с помощью getExternalFilesDir() не требует разрешений на запись/чтение. 
Если вы поддерживаете API 18 и ниже, то разрешения необходимо указать.

``` kotlin
Context.getExternalFilesDir()
Context.getExternalCacheDir()
```