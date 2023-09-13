#android

Android Services - это компонент, который помогает выполнять **длительные процессы**, такие как обновление базы данных, запуск обратного отсчета или воспроизведение звука. По умолчанию Android Services запускаются **в том же** потоке, что и основные процессы приложения.

Поскольку Android Services не имеет пользовательского интерфейса, он никак не зависит от последовательности выполнения других процессов. Это означает, что вы можете запускать его, даже когда пользователь вообще никак не взаимодействует с приложением.

Виды Service:
- Background
- Foreground - выше по приоритету для системы чем background, по сути просто background, который вызвал внутри себя startForeground
- Bound (редкий случай) A bound service runs only as long as another application component is bound to it. Multiple components can bind to the service at once, but when all of them unbind, the service is destroyed.

Service Lifecycle:
![[Service Lifecycle.png]]

Сервис останавливается если:
- Вырубила система
- Вызвали stopSelf(id)
- Снаружи вызвали Context.stopService()