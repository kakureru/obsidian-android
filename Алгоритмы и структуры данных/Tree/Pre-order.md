Также известен как прямой / префиксный

![[Pre-order.png]]

В результате Pre-order обхода мы получим такой порядок :
F, B, A,D,C,E,G,I,H

``` kotlin
class Node(val value: Any, val left: Node?, val right: Node?)
```

Рекурсивный метод:
```kotlin
fun preOrder(node: Node?) {  
	if (node == null) return 
	print(node.value) // обработка узла
	preOrder(node.left)
	preOrder(node.right)
}
```

Итеративный метод:
``` kotlin
fun contPreOrder(top: Node?) { 
	var node = top
	val stack = Stack<Node>() 
	while (node != null || stack.isNotEmpty()) { 
		if (stack.isNotEmpty())
			node = stack.pop()
		while (node != null) { 
			print(node.value) // обработка узла
			if (node.right != null) 
				stack.push(node.right)
			node = node.left
		} 
	} 
}
```