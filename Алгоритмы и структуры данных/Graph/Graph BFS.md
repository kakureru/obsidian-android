
``` kotlin
edges = [[0,1],[1,2],[2,0]]
```

[[Graph#Построение графа|buildGraph()]]
``` kotlin
// существует ли путь в графе между source и end
fun validPathBFS(n: Int, edges: Array<IntArray>, source: Int, end: Int): Boolean {  
	val graph = buildGraph(n, edges)
    val queue: Queue<Int> = LinkedList<Int>()  
    val visited = BooleanArray(n)  
    // first node  
    queue.add(source)  
    visited[source] = true  
    // process  
    while (queue.isNotEmpty()) {  
        val curr = queue.poll()  
        if (curr == end) return true  
        graph[curr].forEach {  
            if (!visited[it]) {  
                visited[it] = true  
                queue.add(it)  
            }  
        }  
    }  
    return false  
}
```