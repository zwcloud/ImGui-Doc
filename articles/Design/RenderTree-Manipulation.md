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

Every frame we should check each node if it is `Dirty`. And if it is, we update, namely re-draw/re-layout it.

__How to determine whether a node need to up re-draw/re-layout?__ 

Manually in the control update.

Two steps:

1. Do any action that influences the looking or layout. See [*What triggers a re-layout in the render tree?*](https://github.com/zwcloud/ImGui.Docs/blob/master/articles/Design/RenderTree-Manipulation.md#implementation-thoughts).
2. Set the node dirty for drawing or layout.
3. Re-draw or re-layout.

__How to re-draw?__

Let's take `BuildInPrimitiveRenderer` on Windows for example, this is an OpenGL based renderer. Graphic data is represented as mesh.

Just come across an article about GPU-accelerated rendering of Chrome: [Accelerated Rendering in Chrome - The Layer Model](https://www.html5rocks.com/en/tutorials/speed/layers/) by Tom Wiltzius. It's better to do some research on how other existing GPU-accelerated renderer functions. A perfect option is webkit. (I have got some kownledge on how it does GPU-based rendering but that's not enough.)

But for now let's just stick to a simplest solution below.

Each node's primitive is rendered into the mesh and then rendered by `Win32OpenGLRenderer`. Only part of the mesh corresponds to the primitive. So if a node changes its primitive, the corresponding part of the mesh should be updated/recreated.

We will update mesh like this:

1. A node is changed or deleted and becomes dirty.
2. The rendering loop detects the node is dirty, so it redraw the node's primitive into a mesh taken from the mesh pool. Then the mesh is added to a linked list called mesh list.
3. Clear the previous mesh buffer and append each mesh to the mesh buffer.
4. The OpenGL renderer renders the mesh buffer.

__furtherly improve current rendering pipeline__

Just luckliy came across an article about firefox's new WebRenderer: [The whole web at maximum FPS: How WebRender gets rid of jank](https://hacks.mozilla.org/2017/10/the-whole-web-at-maximum-fps-how-webrender-gets-rid-of-jank/).

![How WebRender works with the GPU](https://2r4s9p1yi1fa2jd7j43zph8r-wpengine.netdna-ssl.com/files/2017/10/31.png)

It is a very good reference for how should ImGui implement the render-tree and OpenGL based rendering backend.

See also greggman's [Rethinking UI APIs](https://games.greggman.com/game/rethinking-ui-apis/).
