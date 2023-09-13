
``` kotlin
edges = [[0,1],[1,2],[2,0]]
```

[[Graph#Построение графа|buildGraph()]]
``` kotlin
// существует ли путь в графе между source и end
fun validPathDFS(n: Int, edges: Array<IntArray>, source: Int, end: Int): Boolean {  
    val graph = buildGraph(n, edges)  
    val stack = Stack<Int>()  
    val visited = BooleanArray(n)  
    // first node  
    stack.push(source)  
    visited[source] = true  
    // process 
    while (stack.isNotEmpty()) {  
        val curr = stack.pop()  
        if (curr == end) return true  
        graph[curr].forEach {  
            if (!visited[it]) {  
                visited[it] = true  
                stack.push(it)  
            }  
        }  
    }  
    return false  
}
```