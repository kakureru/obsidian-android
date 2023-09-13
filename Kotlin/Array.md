#kotlin 

Есть типизированный массив:
``` kotlin
class Array<T>(size: Int, init: (Int) -> T) // arrayOf()
```
А есть специфичные типы массивов:
``` kotlin
class CharArray(size: Int) // charArrayOf()
class IntArray(size: Int) // intArrayOf()
class LongArray(size: Int) // longArrayOf()
...
```

И предпочтительно использовать конкретные типы, потому что типизированные массив хранит не примитивы, а ссылки:
![[Array.png]]