#kotlin 

inner class - держит ссылку на внешний объект

Kotlin:
``` Kotlin
class A {
    inner class B { }
}
```
Java:
``` java
class A {
    class B { }
}
```

static inner class / nested class - не держит ссылку на внешний объект

Kotlin:
```Kotlin
class A {
    class B { }
}
```
Java:
```Java
class A {
    static class B { }
}
```