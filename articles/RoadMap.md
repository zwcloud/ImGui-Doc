# ImGui v0.1

*v0.1 will be the first release of ImGui. Following is the TODO list of this release.*

# General
*General features.*
- ✅single window application.
- ✅rendering text.
- 🔲anti-aliasing for text rendering.
- ✅GPU Rendering.
- 🔲Repaint when needed instead of every frame.


# Built-in Control
*built-in controls*
- ✅button
- ✅label
- ✅toggle(checkbox)
- ✅hover-button
- ✅slider
- ✅vslider
- ✅toggle-button
- ✅polygon-button
- ✅image
- 🔲textbox
- 🔲combobox


# Built-in Container
*built-in containers*
- ✅box

# Layout Methods
*layout functions used to layout controls and containers*
- ✅grid (recursively)

# Platform Dependent Implementation
*some platform-dependent Implementations*
- Window (window creation and management)
    + ✅Windows: Win32 API    
- Input (input device management)
    + ✅Windows/Keyboard: Win32 API
    + ✅Windows/Mouse: Win32 API
    + 🔲Windows/TouchPen: Win32 API or Wacom only    
- Rendering
    + ✅Windows: OpenGL 4    
- Text
    + ✅Windows: DirectWrite
