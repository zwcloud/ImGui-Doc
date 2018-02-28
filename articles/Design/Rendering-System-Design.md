## Infrastructure

There are four levels of rendering layers from top to base:

* Layer 1: __control__
* Layer 2: __render tree__
    Each control corresponds with a sub-tree in the render tree. Each node on the render tree corresponds to a primitive.
* Layer 3: __primitive__
    The minimal abstract rendering unit: line-segments, rectangles, triangles, circles, polygon, ployline, arcs, bezier-curves, quadratic-curves and so on.
* Layer 4: __basic rendering API (interface)__
    Possible implementations:

    * [built-in] Path-based rendering API on top of OpenGL
    * cairo
    * other platform specific rendering API like Direct2D and Quartz

## Implementation Thoughts

__concepts__

* Brush: fill shapes with colors, images and patterns. It should be implemented in layer 2.
* Pen: draw outlines of a shape with colors, images and patterns. It should be implemented in layer 2.

__examples__

* Button  
  ![button](img/button.svg)

* Slider  
  ![slider](img/slider.svg)

__function of a render-tree node__

1. a visual data container: position(rectangle) and style
2. a layout unit

So, the current implementaion should be rewritten.

__implementaion changes__

* Current implementation:

	1. modifiy the style on the fly
	2. create layout unit on the fly and reuse it when the layout is not changed

* Future implementation based on render-tree:

	We will modify the render-tree structure and nodes when calling control methods like `GUILayout.Button`:

	1. modify the style of a sub-tree(a control), of the render-tree
	2. associate the layout engine to the render-tree structure

	So, we need to refactor all control code and the layout engine, and finally the rendering pipeline.
