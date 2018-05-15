# General

1. Redraw every meshes every frame. __No dirty region__ that marks rectanges needs to be repaint like legacy CPU-based rendering system. If any control is *hot*, then repaint it every frame.
2. Optimization:
	* Clip the meshes against the scroll rectangle, the window and the form.
	* Update only hot control's primitive: no dirty flag.
	* how to reduce mesh size and number, texture size and number, off-screen buffer size and buffer and other GPU resources.

# Details

__Hot__: Briefly, a hot control is a control that has the focus. But it may also mean that the control is animated.