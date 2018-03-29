*Thoughts on Why What and How to manipulate the render-tree.*

## Operations

There are four kind of operations (i.e. CURD):

* Create: Create a node or sub-tree when needed.
* Update: Update properties of a node.
* Read: Read properties of a node.
* Delete: Delete a node or sub-tree from the render-tree.

## Implementation Thoughts

__When to create?__

1. When the application starts up, we need to create an initial render-tree hierarchy.
2. When we need to react to a user action by creating, updating, deleting the control.
3. When the control logic requests creating, updating, deleting a node or sub-tree.

__How to create in an *immediate* way?__

In retained mode GUI, nodes are created, updated and deleted when an event is triggered. 
But in an immediate mode GUI, the controls are always being updating and we do not use event to handle user input. 

Let's take the creation of a node when the application starts up for example. If we put the code of creating nodes inside the control method, 
we will adding duplcated nodes to the render-tree every time when the method is called. And that is not the expected behavior.
What we need is to create only once when the application starts up.

The first solution to this come to my mind is to use a *dirty flag*. It just works. ImGui will use this approach for now. I think there are some more flexible solutions.

__When to update?__

__How to determine whether a node need to up re-draw/re-layout?__ 