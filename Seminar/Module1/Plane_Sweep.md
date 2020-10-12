# PLANE SWEEP: CONCEPT

## Problem Statement
- **Given:** A set of line segments
- **Compute:** All intersections between line segments
![image](https://user-images.githubusercontent.com/48788781/94458330-ff731900-01df-11eb-822a-afc923e725ff.png)

## Plane Sweep: Algorithm design technique
- Simulate sweeping a vertical line from left to right across the plane.
- Maintain **cleanliness property**: At any point in time, to the left of sweep
line everything is clean, i.e., properly processed.
- **Sweep line status**: Store information along sweep line
- **Events**: Discrete points in time when sweep line status needs to be
updated

### **Algorithm** Generic_Plane_Sweep:
Initialize sweep line status `S` at time $x = -\infty$<br>
Store initial events in **event queue** `Q`, a priority queue ordered by $x-coordinate$<br>
 while $Q\not ={\emptyset}$:<br>
$\qquad$// extract next event e:<br>
$\qquad$e = Q.extractMin();<br>
$\qquad$// handle event:<br>
$\qquad$Update sweep line status<br>
$\qquad$Discover new upcoming events and insert them into Q<br>

### Plane sweep PseudoCode:
```python
def sweepLineIntersection(Points[0..2n-1]):
    1. Sort Points[] from left to right (according to x coordinate)
    2. Create an empty Self-Balancing BST(AVL tree) T. It will contain all active line Segments ordered by y coordinate.
    # Process all 2n points 
    3. for i in range(2n-1):
        # If this point is left end of its line 
        if (Points[i].isLeft):
            T.insert(Points[i].line())
        # Check if this points intersects with its predecessor and successor
        if ( doIntersect(Points[i].line(), T.pred(Points[i].line()) )
            return true
        if ( doIntersect(Points[i].line(), T.succ(Points[i].line()) )
            return true
    4. return False
```
