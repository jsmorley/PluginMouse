# Options

* The plugin executes bangs when a mouse event happens. The plugin reads and executes all [action options](https://docs.rainmeter.net/manual/mouse-actions/) but are not limited meters. Along with these, the plugin adds additional action types.

  - <code>**MouseMoveAction**</code> gets executed when the mouse moves.
  - <code>**LeftMouseDragAction**</code>, <code>**RightMouseDragAction**</code>, <code>**MiddleMouseDragAction**</code>, <code>**X1MouseDragAction**</code>, <code>**X2MouseDragAction**</code> get executed when their respective mouse button is pressed and the mouse moves - these do not override the MoveAction but are executed after it.\

* In the same way as existing mouse actions do it, the plugin's actions substitute temporary variables <code>$MouseX$</code> and <code>$MouseY$</code> with the mouse coordinates

* RelativeToSkin can be set to <code>0</code> to make the monitor's top-left corner the <code>0,0</code> coordinate, instead of the skin's top-left corner. Default <code>1</code>.

* RequireDragging can be set to <code>1</code> to make the plugin accept [commands](https://docs.rainmeter.net/manual/bangs/#CommandMeasure) with arguments Start and Stop to set mouse capturing to happen outside borders aswell - very useful for implimenting dragging. Default <code>0</code>.

  - Without this option, the plugin's measure can be [paused](https://docs.rainmeter.net/manual/bangs/#PauseMeasure) or [disabled](https://docs.rainmeter.net/manual/bangs/#EnableDisableToggleMeasure) but it has to have <code>DynamicVariables=1</code> and be updated.

# Example Skin

[Download](https://github.com/jsmorley/PluginMouse/releases/download/v3.2.2/MouseExample_3.2.2.rmskin)

```
[Rainmeter]
Update=-1
BackgroundMode=2
SolidColor=000000
ContextTitle=toggle
ContextAction=[!ToggleMeasure measureMouse][!UpdateMeasure measureMouse][!SetOption Text Text "disabled"][!UpdateMeter Text][!Redraw]
ContextTitle2=toggle relative
ContextAction2=[!UpdateMeasure RelativeState][!UpdateMeasure measureMouse]

[Metadata]
Author=NighthawkSLO
Information="Skin that shows all the features of the mouse.dll plugin. | Use the right click "custom skin actions" context menu to toggle some options. | Uses all possible options for help with understanding the plugin's functionality."
Version=3.2.0
License=Creative Commons Attribution - Non - Commercial - Share Alike 4.0
[RelativeState]
Measure=Calc
Formula=(RelativeState + 1) & 1
;1 at startup, either 0 or 1

[measureMouse]
Measure=Plugin
Plugin=Mouse
MouseMoveAction=[!SetOption Text Text "mouse move#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
LeftMouseDownAction=[!SetOption Text Text "Left mouse down#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
LeftMouseUpAction=[!SetOption Text Text "Left mouse up#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
LeftMouseDragAction=[!SetOption Text Text "Left mouse drag#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
RightMouseDownAction=[!SetOption Text Text "Right mouse down#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
RightMouseUpAction=[!SetOption Text Text "Right mouse up#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
RightMouseDragAction=[!SetOption Text Text "Right mouse drag#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
MiddleMouseDownAction=[!SetOption Text Text "Middle mouse down#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
MiddleMouseUpAction=[!SetOption Text Text "Middle mouse up#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
MiddleMouseDragAction=[!SetOption Text Text "Middle mouse drag#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
X1MouseDownAction=[!SetOption Text Text "X1 mouse down#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
X1MouseUpAction=[!SetOption Text Text "X1 mouse up#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
X1MouseDragAction=[!SetOption Text Text "X1 mouse drag#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
X2MouseDownAction=[!SetOption Text Text "X2 mouse down#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
X2MouseUpAction=[!SetOption Text Text "X2 mouse up#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
X2MouseDragAction=[!SetOption Text Text "X2 mouse drag#CRLF#$mouseX$, $mouseY$"][!UpdateMeter Text][!Redraw]
DynamicVariables=1
RelativeToSkin=[RelativeState]

[Text]
Meter=String
X=60
Y=20
W=120
H=40
FontFace=Consolas
AntiAlias=1
StringAlign=CenterCenter
FontColor=FFFFFF
Y=R
FontSize=8
Text=nothing#CRLF#0, 0
```
