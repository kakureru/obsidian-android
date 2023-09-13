#kotlin 

``` kotlin
data class Point(
	val x: Int,
	val y: Int,
)

operator fun Point.plus(other: Point): Point =
	Point(x = x + other.x, y = y + other.y)

println(Point(1, 1) + Point(2, 2)) // Point(x=3, y=3)
```

[[Operator functions]]
[[Extension functions]] 