Breadth first search / Обход в ширину

``` kotlin
class Node(val value: Any, val left: Node?, val right: Node?)
```

``` kotlin
fun bfs(node: Node?): MutableList<Any> {  
    val queue: Queue<Node> = LinkedList<Node>()  
    val values = mutableListOf<Any>()  
    queue.add(node)  
    while(queue.isNotEmpty()) {  
        val tempNode = queue.poll()  
        values.add(tempNode.value)  
        if (tempNode.left != null) queue.add(tempNode.left)  
        if (tempNode.right != null) queue.add(tempNode.right)  
    }  
    return values  
}
```