#android 

**SharedPreferences** — постоянное хранилище, используемое приложениями для хранения своих настроек, например. Это хранилище является относительно постоянным, пользователь может зайти в настройки приложения и очистить данные приложения, тем самым очистив все данные в хранилище.

Представляет собой xml файл с парами ключ-значение
Эти данные не защищены, поэтому не стоит хранить там что-то такое.

Способы получения экземпляра:

Объект SharedPreferences, указывающий на дефолтный файл, используемый в данном контексте
``` kotlin
PreferenceManager.getDefaultSharedPreferences(Context)
```

Объект SharedPreferences, указывающий файл, указанный в параметре name. Если файла нет, он создастся при первой записи.
``` kotlin
Context.getSharedPreferences(name: String, mode: Int)
```

Объект SharedPreferences для доступа в переделах активити. Если переименовать активити, файл потеряется.
``` kotlin
Context.getPreferences(mode: Int)
```

apply() - синхронное сохранение на том потоке, откуда вызвали
commit() - асинхронное сохранение. Если сохранить и сразу считать, все равно получим актуальные данные из кэша.

## Context Mode

MODE_PRIVATE - созданный файл доступен только в пределах приложения (и всех приложений которые используют тот же user_ID)

Остальные моды deprecated