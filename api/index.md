---
uid: api/index.md
---
v0.1

# manual-positioning controls

| Method                    | Description														|
|---------------------------|-------------------------------------------------------------------|
| @ImGui.GUI.Button(ImGui.Rect,System.String,System.String)																			| Show a button that execute something immediately.					|
| @ImGui.GUI.Label(ImGui.Rect,System.String,System.String)																			| Show a label.														|
| @ImGui.GUI.Toggle(ImGui.Rect,System.Boolean,System.String)																		| Show a toggle(check-box).											|
| @ImGui.GUI.HoverButton(ImGui.Rect,System.String,System.String)																	| Show a button inside a @ImGui.Rect.								|
| @ImGui.GUI.Slider(ImGui.Rect,System.Double,System.Double,System.Double,System.String)												| Show a horizontal slider that user can drag to select a value.	|
| @ImGui.GUI.VSlider(ImGui.Rect,System.Double,System.Double,System.Double,System.String)											| Show a vertical slider that user can drag to select a value.		|
| @ImGui.GUI.ToggleButton(ImGui.Rect,System.String,System.Boolean,System.String)																	| Show a button that acts like a toggle.							|
| @ImGui.GUI.PolygonButton(ImGui.Rect,System.Collections.Generic.IReadOnlyList{ImGui.Point},ImGui.Rect,System.String,System.String) | Show a converx polygon button.									|
| @ImGui.GUI.Image(ImGui.Rect,System.String,System.String)																			| Show a image.														|

# auto-layout controls

| Method							| Description														|
|-----------------------------------|-------------------------------------------------------------------|
| @ImGui.GUILayout.Button(System.String,System.String,ImGui.LayoutOption[])																			| Show a button that execute something immediately.	 				|
| @ImGui.GUILayout.Label(System.String,System.String,ImGui.LayoutOption[])																			| Show a label.							 							|
| @ImGui.GUILayout.Toggle(System.Boolean,System.String,ImGui.LayoutOption[])																		| Show a toggle(check-box).											|
| @ImGui.GUILayout.HoverButton(System.String,System.String,ImGui.LayoutOption[])																	| Show a button inside a @ImGui.Rect.								|
| @ImGui.GUILayout.Slider(ImGui.Size,System.Double,System.Double,System.Double,System.String,ImGui.LayoutOption[])												| Show a horizontal slider that user can drag to select a value.	|
| @ImGui.GUILayout.VSlider(ImGui.Size,System.Double,System.Double,System.Double,System.String,ImGui.LayoutOption[])											| Show a vertical slider that user can drag to select a value.		|
| @ImGui.GUILayout.ToggleButton(System.String,System.Boolean,System.String,ImGui.LayoutOption[])																	| Show a button that acts like a toggle.							|
| @ImGui.GUILayout.PolygonButton(System.Collections.Generic.IReadOnlyList{ImGui.Point},ImGui.Rect,System.String,System.String,ImGui.LayoutOption[]) | Show a converx polygon button.									|
| @ImGui.GUILayout.Image(System.String,System.String,ImGui.LayoutOption[])																			| Show a image.														|

## layout containers

| Method						| Description								|
|-------------------------------|-------------------------------------------|
| @ImGui.GUILayout.BeginHorizontal(ImGui.LayoutOption[])	| Begin a horizontal layout group.			|
| @ImGui.GUILayout.EndHorizontal		| End a horizontal layout group.			|
| @ImGui.GUILayout.BeginVertical(ImGui.LayoutOption[])		| Begin a vertical layout group.			|
| @ImGui.GUILayout.EndVertical		| End a vertical layout group.				|

## layout options

| Method						| Description								|
|-------------------------------|-------------------------------------------|
| @ImGui.GUILayout.Width(System.Double)				| Set the width of a control.				|
| @ImGui.GUILayout.Height(System.Double)			| Set the height of a control.				|
| @ImGui.GUILayout.ExpandWidth(System.Boolean)		| Set whether the width of a control should be expanded to occupy as much space as possible. |
| @ImGui.GUILayout.ExpandHeight(System.Boolean)		| Set whether the height of a control should be expanded to occupy as much space as possible. |
| @ImGui.GUILayout.StretchWidth(System.Int32)		| Set the factor when expanding the width of a control. |
| @ImGui.GUILayout.StretchHeight(System.Int32)		| Set the factor when expanding the height of a control. |

## layout helpers

| Method						| Description									|
|-------------------------------|-----------------------------------------------|
| @ImGui.GUILayout.Space(System.Double)				| Put a fixed-size space inside a layout group.	|
| @ImGui.GUILayout.FlexibleSpace		| Put a expanded space inside a layout group.	|