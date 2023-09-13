Также известен как обратный / инфиксный

![[In-order.png]]

В таком случае мы получаем: 
A,B,C,D,E,F,G,H,I

```kotlin
class Node(val value: Any, val left: Node?, val right: Node?)
```

Рекурсивный метод:
``` kotlin
fun inOrder(node: Node?) {  
	if (node == null) return 
	inOrder(node.left)
	print(node.value) // обработка узла
	inOrder(node.right)
}
```

Итеративный метод:
``` kotlin
fun contInOrder(top: Node?) {  
    var node = top  
    val stack = Stack<Node>()  
    while (node != null || stack.isNotEmpty()) {  
        if (stack.isNotEmpty()) {  
            node = stack.pop()  
            print(node.value) // обработка узла  
            node = if (node.right != null)  
                node.right  
            else  
                null        
        }  
        while (node != null) {  
            stack.push(node)  
            node = node.left  
        }  
    }  
}
```