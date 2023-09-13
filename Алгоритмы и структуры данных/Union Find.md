``` kotlin
edges = [[0,1],[1,2],[2,0]]
```

``` kotlin
// существует ли путь в графе между start и end
class Solution {  
    fun validPath(n: Int, edges: Array<IntArray>, start: Int, end: Int): Boolean {  
        val dSet = DisjointSet(n, edges)  
        return dSet.areConnected(start, end)  
    }  
}  
  
class DisjointSet(n: Int, edges: Array<IntArray>) {  
    private val parent = IntArray(n) { it }  
  
    init {  
        edges.forEach { union(it[0], it[1]) }  
    }  
  
    fun union(u: Int, v: Int) {  
        val rootU = find(u)  
        val rootV = find(v)  
        if (rootU != rootV) parent[rootU] = rootV  
    }  
  
    fun find(u: Int): Int {  
        var x = u  
        while (x != parent[x]) {  
            x = parent[x]  
        }  
        parent[u] = x  
        return x  
    }  
  
    fun areConnected(u: Int, v: Int): Boolean = find(u) == find(v);  
}
```