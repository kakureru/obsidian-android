Также известен как концевой / постфиксный

![[Post-order.png]]

В таком случае мы полчаем: 
A, C, E, D, B, H, I, G, F

``` kotlin
class Node(val value: Any, val left: Node?, val right: Node?)
```

Рекурсивный метод:
``` kotlin
fun postOrder(node: Node?){  
	if (node == null) return
	postOrder(node.left)
	postOrder(node.right)  
	print(node.value) // обработка узла
}
```

Итеративный метод:
``` kotlin
fun contPostOrder(top: Node?) {  
    var node = top  
    val stack = Stack<Node>()  
    while (node != null || stack.isNotEmpty()) {  
        if (!stack.isEmpty()) {  
            node = stack.pop()  
            if (stack.isNotEmpty() && node.right == stack.lastElement())  
                node = stack.pop()  
            else {  
                print(node.value) // обработка узла  
                node = null  
            }  
        }  
        while (node != null) {  
            stack.push(node)  
            if (node.right != null) {  
                stack.push(node.right)  
                stack.push(node)  
            }  
            node = node.left  
        }  
    }  
}
```