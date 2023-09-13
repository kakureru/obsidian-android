#kotlin 

``` kotlin
class Line(val pointA: Point, val pointB: Point)

class Point(val x: Int, val y: Int) {
	infix fun connectTo(other: Point): Line = 
		Line(pointA = this, pointB = other)
}

val pointA = Point(x = 1, y = 1)
val pointB = Point(x = 1, y = 1)

val line: Line = pointA connectTo pointB
```