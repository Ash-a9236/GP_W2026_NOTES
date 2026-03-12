<!--@ash-a9236 2025 : please see license for -->

<!--VARIABLES-->

<style>

  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Fira+Code&display=swap');

  :root {
    /*--text: #b693fa;*/
    --title: #b8a6dd;
    --highlight: #f7ebe5;
    --link: #dac8f1;
  }

  body {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  }
</style>

# <span style="color: var(--title)">GAME PROGRAMMING WITH UNITY 0

## <span style="color: var(--title)">INTRODUCTION

<br>
TABLE OF CONTENTS <br> <br>

[<span style="color: var(--link)">01 . . Base Concepts</span>](#base-concepts) <br>
&emsp; [<span style="color: var(--link)">01 . . Main</span>](#base-concepts-main) <br>
[<span style="color: var(--link)">02 . . Console</span>](#console) <br>
&emsp; [<span style="color: var(--link)">01 . . Console Print</span>](#console-print) <br>
&emsp; [<span style="color: var(--link)">02 . . Console Output</span>](#console-output) <br>
&emsp; [<span style="color: var(--link)">03 . . Console Input</span>](#console-input) <br>
&emsp; [<span style="color: var(--link)">04 . . Console Errors</span>](#console-errors) <br>
[<span style="color: var(--link)">03 . . Access Modifiers</span>](#access-modifiers) <br>
[<span style="color: var(--link)">04 . . Static vs Non-Static</span>](#static-vs-nonstatic) <br>
[<span style="color: var(--link)">05 . . Return Types</span>](#return-types) <br>
[<span style="color: var(--link)">06 . . Naming</span>](#naming) <br>
[<span style="color: var(--link)">07 . . Input</span>](#input) <br>
[<span style="color: var(--link)">08 . . Documentation</span>](#documentation) <br>

<br> <br>

<hr>

### <a name="base-concepts"><span style="color: var(--title)">01.00 BASE CONCEPTS</span></a> 

<hr>

<br>



<br>

#### <a id="base-concepts-game-engine"><span style="color: var(--title)">01.01 GAME ENGINE</span></a>

<hr>

<br>

A game engine is a <span style="color: var(--highlight)">set of tools</span> that is like an IDE but for game creation.
It contains everything a creator needs to make a video game, including

| TOOL                | USE                                                     |
|---------------------|---------------------------------------------------------|
| rendering engine    | 2D and 3D graphics rendering                            |
| physics engine      | movement <br>collision detection                        |
| sound engine        | sound in 2D and 3D space                                |
| scripting tools     | also links to prefered IDE (visual studio, rider, etc.) |
| animation framework | playing with animations                                 |
| AI                  | NPC behaviour <br>level navigation                      |
| networking tools    | multiplayer games                                       |
| memory manager      | monitoring memory and managing it                       |
| scene graph         | manager objects in the virtual space                    |


<br>

#### <a id="base-concepts-scene-graph"><span style="color: var(--title)">01.02 SCENE GRAPH & GAME OBJECTS</span></a>

<hr>

<br>

The <span style="color: var(--highlight)">scene graph</span> is a <span style="color: var(--highlight)">structured representation</span> of a scene that shows the objects, their attributes, and their relationships

The scene graph allows you to specifically also see the parent-children relationships (local relationships), which helps see how the objects will move in relation to one another.

A <span style="color: var(--highlight)">game object</span> is a <span style="color: var(--highlight)">node</span> of the scene graph, which acts as a <span style="color: var(--highlight)">containers for components</span>
All game objects have the <span style="color: var(--highlight)">transform component</span>, which contains the <span style="color: var(--highlight)">position, rotation, and scale</span> of the object, in form of vectors.

Basically : <br> 

    |_ GameObject 
        |_ Transform
            |_ Position
                |_ Vector X
                |_ Vector Y
                |_ Vector Z
            |_ Scale
                |_ Vector X
                |_ Vector Y
                |_ Vector Z
            |_ Rotation
                |_ Vector X
                |_ Vector Y
                |_ Vector Z






<br> <br>

<hr>

### <a name="console"><span style="color: var(--title)">02.00 VECTORS</span></a>

<hr>

<br>

A <span style="color: var(--highlight)">vector</span> is basically an 'arrow' (more technically a quantity or a phenomenon), which has a <span style="color: var(--highlight)">magnitude</span> and a <span style="color: var(--highlight)">direction</span>
In Unity, declaring a vector is :

```csharp
using UnityEngine;

Vector3 3dVector = new Vector3(X, Y, Z);
Vector3 normalizedVector = Vector3.normalize(3dVector); // has the same direction as 3dVector but has a length of 1.0
```

For example, to have a vector 5 units above the ground (or even a player) : 

```csharp
using UnityEngine;

var calculatedPoint = groundCoordinates + new Vector2(0, 5); // Vector 2 is a 2D vector
```

<br>

#### <a id="vector-addition"><span style="color: var(--title)">02.01 VECTOR ADDITION</span></a>

<hr>

<br>

Adding two vectors together is like walking the first vector then walking the second one (the order doesn't matter). the destination is the result.

> for $c = a + b$ : <br>
> $a = \begin{pmatrix} 3, 5 \end{pmatrix}$ <br>
> $b = \begin{pmatrix} 2, -1 \end{pmatrix}$ <br>
> $c = \begin{pmatrix} a_x + b_x, a_y+b_y \end{pmatrix} = \begin{pmatrix} 5, 4 \end{pmatrix}$

or

```csharp
using UnityEngine;

Vector2 a = new Vector2(3,5);
Vector2 b = new Vector2(2,-1);
Vector2 c = a + b;
```

<br>

#### <a id="vector-substraction"><span style="color: var(--title)">02.02 VECTOR SUBSTRACTION</span></a>

<hr>

<br>

When subtracting vectors (or points in space), you get a vector that point from object A (or point A) to object B (or point B)
> $c = \begin{pmatrix} a_x - b_x, a_y - b_y \end{pmatrix} = \begin{pmatrix} 1, 6 \end{pmatrix}$

```csharp
using UnityEngine;

Vector3 heading = target.position - player.position; // gets a vector that points from the player's position to the target's position
```

Subtracting vectors is mostly used to get the <span style="color: var(--highlight)">direction</span> and the <span style="color: var(--highlight)">distance</span> of one object compared to another. The resulting vector when subtracting two points give you the <span style="color: var(--highlight)">path to take</span> to get to the second object.

```csharp
using UnityEngine;

Vector2 pointA = new Vector2(12, 5);
Vector2 pointB = new Vector2(29, 16);

// what is the point from pointA to pointB ? -> pointB - pointA
Vector2 path = new Vector2((pointB.x - pointA.x), (pointB.y - pointA.y));

// OR
Vector2 path2 = pointB - pointA;
```
> to only get the direction of a vector, you need to *normalize it*

<br>

#### <a id="vector-magnitude"><span style="color: var(--title)">02.03 VECTOR MAGNITUDE</span></a>

<hr>

<br>

A <span style="color: var(--highlight)">vector's magnitude</span> is equal to the distance between two positions. It is basically <span style="color: var(--highlight)">the way the vector is pointing</span>

> formula for the magnitude : $|v| = \sqrt{x^2 + y^2 + z^2}$

> If you are given two points : $|AB| = \sqrt{((x_2 - x_1)^2 + (y_2 - y_1)^2 + (z_2 - z_1)^2)}$

```csharp
using UnityEngine;

Vector3 heading = target.position - player.position;
var distance = heading.magnitude // magnitude method
```

Since magnitude calculations are very CPU-hungry (in terms of calculating the square root), using the ```.sqrMagnitude``` method is better as it only returns the magnitude squared. It is useful to calculate the distance between two points (or objects) to check if they are, for example, within shooting range.

```csharp
using UnityEngine;

Vector3 heading = target.position - player.position;
var maxRange = 5;

if (heading.sqrMagnitude < (maxRange * maxRange)) { // -> target is within range
} else { // -> target is outside of range
}

```

<br>

#### <a id="vector-normalization"><span style="color: var(--title)">02.04 VECTOR NORMALIZATION</span></a>

<hr>

<br>

A <span style="color: var(--highlight)">normalized vector</span> is a vector which <span style="color: var(--highlight)">has a direction but a length of 1.0</span>
You can normalize a vector by <span style="color: var(--highlight)">dividing it by its own magnitude</span>


```csharp
using UnityEngine;

Vector3 normaliedVector = Vector3.normalize(vectorN); // note that the current vector (vectorN) remains unchanged and normalizedVector is basically a new vector
```

Going back to the magnitude example : 

```csharp
using UnityEngine;

Vector3 heading = target.position - player.position;

// separating the distance and the direction is better as both calculations are CPU-hungry
var distance = heading.magnitude // magnitude method
var direction = heading / distance; // normalized vector
```

<br>

#### <a id="vector-dot-product"><span style="color: var(--title)">02.05 VECTOR DOT PRODUCT</span></a>

<hr>

<br>

The dot product is a <span style="color: var(--highlight)">float (or scalar) value</span> measuring how much two vectors point in the same direction. It <span style="color: var(--highlight)">multiplies the magnitude of both vectors together with the cosine of their angle</span>. The closer the dot product is to 1, the more the two vectors point in the same direction.

> formula for the dot product : $a * b = |a| * |b| * cos(\theta)$ OR $a * b = (a_x * b_x) + (a_y * b_y)$
> To find the angle of two given vectors by with the dot product formula : $\theta = arccos(\frac{(a * b)}{(|a| * |b|)})$

Remember that if the dot product is equal to : 

| RESULT | MEANING                                                                               | 
|--------|---------------------------------------------------------------------------------------|
| 1      | They are in the exact same directions : they are parallel (since $cos(0\degree) = 1$) |
| 0      | The two vectors are perpendicular ($90\degree$) (since $cos(90\degree) = 0$)          |
| -1     | The two vectors are going in opposite directions                                      |

In C#, you can use the ```.Dot``` method

```csharp
using UnityEngine;

Vector2 vector1 = new Vector2(4, 7);
Vector2 vector2 = new Vector2(4, 7);
Vector2 vector3 = new Vector2(4, 7);


```
 
 
 
 
