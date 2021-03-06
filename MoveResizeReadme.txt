Move & Resize UI:
Scripts for UI Windows and Objects

Version 5.0

Description:

This is a collection of scripts that allow the user to move and resize UI windows and objects at runtime. They are written to use with Unity's new UI system. Version 2 scripts allow the user to scale two objects at once (like a slider) at runtime and anchor the alignment and position of one object onto another. Version 3 includes new scripts to maximize/minimize/restore an object or to allow one object to push and pull another object or its edges by a defined amount. It also contains many updates to pre-existing scripts to fix potential problems and be more effective as well as adding new features such as custom cursors and restraining objects to the screen and/or parents. Version 4 completely overhauled most of the existing scripts to use a single script as a main controller.

Version 5 adds limited functionality to canvases not set to Screen Space - Overlay as well as a movement multiplier setting.




Script Features:

	Simplicity:
	They are simply scripts that attach to an object.

	No jumping to the cursor:
	The object will not jump to center around the cursor. If you begin dragging an object from the corner, your drag will remain at the corner of the object.

	Move smoothly or by intervals:
	You have the options to move and resize objects smoothly or by defined intervals. Smooth is the default method, however, the interval method may be desired if using a grid-based system or if you want easier alignment.

	Customizable border and inset sizes:
	Variable-based thickness of borders and insets for easy customization. Borders are used for resizing. Insets are used for moving. They can easily be configured to work together.

	Set minimum size:
	You can set how small your objects can resize to both vertically and horizontally. They will never shrink so small that they cannot be enlarged again... unless you want them to.

	Event friendly:
	Use in accordance with events to make a window work how you want it to work. Do you want to be able to choose between the smooth and interval methods at runtime? All you need is a button or toggle. Do you want to lock the window in place for now, but unlock it later? A single button is the answer. Do you want to be able to drag your mouse freely in a window without moving anything? A panel with Pointer Enter/Exit events can do the job!
	
	Fully commented scripts:
	Want to know how the scripts work? Just follow along. It should make it much easier to add onto or modify.

	Demonstration scenes:
	Multiple scenes using the various scripts. See how the scripts work independently and together.

	Customizable cursors (limited):
	Set your own images to be used as custom cursors when the cursor is over a moveable/resizable position.

	Restrain to screen/parent:
	Restrain an object from being moved or resized off the screen or outside of its parent. Completely optional.

	Single control script:
	A new script has been added to control raycasting, custom cursors, and activation of other scripts.

	*NEW IN VERSION 5*

	Unity 5:
	Officially for Unity 5!

	Movement multiplier:
	The ratio of movement or resizing based on the mouse movement can be customized.




Included Scripts:

	Move:
	Moves the scripted object when the mouse is dragged.

	MoveParent:
	Moves the direct parent of the scripted object when the mouse is dragged.

	MoveOther:
	Moves an object that has a distant or no relation to the scripted object when the mouse is dragged. Suggested use is for relations more distant than direct parent-child, though there may be other creative uses.
	
	Resize:
	Resizes the scripted object when the mouse drags its borders (edges).

	ResizeParent:
	Resizes the direct parent of the scripted object when the mouse is dragged.

	ResizeOther:
	Resizes an object that has a distant or no relation to the scripted object when the mouse is dragged. Suggested use is for relations more distant than direct parent-child, though there may be other creative uses.

	BringToFront:
	Brings the object and its children to the front of the UI overlay by clicking or automatically.
	Note: This feature is included in all of the above scripts as well. This script is only needed if an object has no script attached to itself or to its (grand)parent(s), but you still wish to bring the object to the front of the UI overlay.

	DisableMoveResize:
	A script used as a reference to the Move and Resize series of scripts to disable their actions if the object this script is attached to is clicked. It affects only its object, not its children or grandchildren.

	ScaleHorizontal:
	Scales two objects horizontally when the scripted object is dragged. As one gets wider, the other gets thinner.

	ScaleVertical:
	Scales two objects vertically when the scripted object is dragged. As one gets taller, the other gets shorter.
	
	Anchor:
	Anchors the alignment and/or positioning of one object to the scripted object. User can define the alignment and positioning in the inspector or can use the current alignment and positioning of the object.

	MaximizeMinimizeRestore:
	As the name implies, this script gives the ability to maximize an object to the size of its parent or screen, to minimize it to pre-defined or user-defined positions and sizes, and to restore its original size and position.

	PushPull:
	Allows one object to push another object or its edge then pull it back by defined amounts. Similar to anchoring, but with more versatility.

	Ignore:
	Used as a reference for raycasting. Any object with this script attached will be ignored by a raycast, returning the object that is behind it.

	UIController:
	Controls the raycasting and activation of the other scripts. Also sets the cursor to the correct custom cursor depending on the cursor position.



What the scripts do NOT do:

The interval method does not align the objects/windows to grids. It simply moves/resizes based on defined distances. It's up to you to set the placement and size to any grid-base that you desire.

The scripts do not save the position and size of objects or windows. They simply move and resize objects when they are present.

The border thickness and inset variables do not effect anything visually. They are only numbers that the scripts read in order to determine how far inside an object a cursor may be in order to begin resizing/moving. It's up to you to make any visual borders/insets correspond to the scripts' border thickness/insets if you desire.

Parent scripts do not affect any object except the DIRECT parent. Not the object itself, not a grandparent. Only the direct parent.

Scripts and scripted objects do not work as a team. Each script and each scripted object works independently. That's why there are multiple scripts and multiple customization features, so you can use the right tools at the right places to make them work with each other instead of against each other. The exception to this is the UIController script.

Scripted objects also do not communicate with one another. Each one has its own settings. It can be easy to forget to change the settings on all of them instead of just one or a few. When things don't work well and you don't know why, this could be the problem. The exceptions to this are the DisableMoveResize and Ignore scripts which are used as a references other scripts as well as the UIController script which controls the others.

Scripts do not choose the appropriate anchors for your objects. If your objects move or resize in undesired ways, check the anchors. The exception to this is the MaximizeMinimizeRestore script. When minimizing, anchors are changed to use Middle/Center for simple placement of the minimiazed object. The anchors are restored when the object is restored.



How the scripts work:

The Move/Resize series of scripts simply find out where the cursor is. If it's over a designated area when the button is pressed, a raycast determines if the foremost object is the scripted object, and tracks the movement over each frame. It moves the object or the object's sides to the new position.

The BringToFront and Move/Resize series of scripts set the selected object as the last sibling in the hierarchy, making it the foremost object in the UI overlay.

The DisableMoveResize script is used as a reference for the Move/Resize series of scripts. Anything with this Disable script attached will suppress the other scripts' actions when clicked.

Borders are designated areas on the edges of an object used for resizing. The larger the border thickness, the larger the area the cursor may begin dragging from. There are eight sectors to each border: four sides and four corners. The corner sectors are where the horizontal and vertical sectors overlap.  The borders will also provide a default minimum width and height if others are not defined. The object should never be able to be resized to less than to twice the thickness of a border. This is to protect the object from being resized into nothingness.
Note: For ResizeParent/Other scripts, there is no border thickness. Instead, the minimum size of the resizable object will be set by default to twice the width/height of the scripted object (not the object being resized).

Insets are designated areas inside  the edges of an object used for moving. Think of them as the opposite of borders. Each of the four insets (top, bottom, left, right) can be set independently. This is to make it easier to use with objects such as buttons on only one side of the object.
NOTE: Insets will only affect objects on a canvas set to Screen Space - Overlay.

Inside the Move/Resize scripts, there are also offsets. They are simply used to get the position of the cursor relative to the position of the object. Using them, the cursor can move the object around without the object jumping to center around the cursor.

The Scale scripts use the concepts of the Move and Resize scripts. They move an object, but also resize two other objects at the same rate.

The Anchor script moves and resizes another object based on the scripted object's size and positioning depending on what options the user selects in the inspector tab. Alignments are based on the corresponding sides of the two objects. Spacing is based on the opposite sides of the two objects.

The PushPull script acts similar to the anchor script above, except it only affects the other object under certain conditions and to a limited extent.

The Ignore script is used as a reference for raycasting. Any object with this script attached will be completely ignored by a raycast.

The UIController is the script that controls the Move/Resize/Scale series of scripts. It performs raycasts, sets custom cursors, and activates and deactives the other scripts.



How to use the scripts:

The first step is to create a canvas with its Render Mode set to Screen Space - Overlay. It is important to use the default setting on its Canvas Scaler. These scripts use pixels for most of the calculations.
NOTE: Version 5 scripts may have limited functionality with canvases that are not set to Screen Space - Overlay, but it is not recommended, especially the basic Resize script (ResizeParent/Other should be used instead). The only true way to know if it will work as desired is to try.

The second step is to create an empty gameobject (or other permanent object), and attach the UIController script to it. Without it, most of the scripts will NOT work.

For Move/Resize scripts:
Simply add the desired script to the object you wish to move or resize, or to the child of the parent object you wish to move or resize, or even to an object that has a distant or no relation to the object you wish to move or resize. If using an Other script, drag the object you wish to move/resize from the hierarchy into the Other Object slot on the inspector tab of the scripted object. The inspector tab also offers the different customization options under the Script component of the object.

For Scale scripts:
Create an object that will be used as a "slider." Attach the desired script to the slider object. Create one or two objects that will be scaled. Drag them from the hierarchy into the specific slots on the inspector tab. The inspector tab also offers the different customization options under the Script component of the object.

For the Anchor script:
Create an object that will be used as an anchor. Add the Anchor script to it. Create an object you wish to anchor to the first object. Drag from the hierarchy into the Anchored Object slot on the inspector tab. You may define the alignments or spacings manually in the inspector tab or you may place the anchored object manually and select the Get Position option in the inspector tab.
Note: You may use multiple anchor scripts on the same object in order to anchor multiple objects. You may also use the anchor scripts on objects that are anchored to another object, though this may not work as well as you wish, especially with multiple anchor generations.

For the MaximizeMinimizeRestore script:
Unlike the others, this script is dependent on events. For example, if you wished to maximize an object with a button press, create the object you with to be maximized. Add the script to it. Create a button. In the Inspector tab for the button, there will be the Button (script) component. In the On Click () section of the component, click the + symbol. Drag the scripted object from the hierarchy into the empty slot. Click the button that reads No Function, first select MaximizeMinimizeRestore, then select Maximize (). Everything should be set. Now, when you click that button at runtime, the scripted object will be maximized. Substitute Minimize () and Restore () for those functions.

For the PushPull script:
Create an object that will be used to push/pull another object. Attach the script to it. Create an object you wish to be pushed/pulled. In the Inspector tab for the scripted object, select which movement options you desire. You should select only one push and one pull option for each side if any. Currently, pulling an object will only work after it has been pushed, so selecting only a pull option will have no effect. Set the Correct Distance to the amount of space you wish to keep the two objects separated by. Set the maximum push/pull amounts or leave them at zero.

The main advice I can give is to experiment with the scripts, objects, and events. You can use the included demo scenes (especially the two example scenes) to understand how they work together. Once you do, the best thing to do is to plan out the designs of your windows beforehand. Know what script you will need for each object, if any, and what events you will need in order to modify or disable those scripts and functions.

Also, just so you are made aware, the UIController script does include an option to ignore text boxes for raycasting. That means that you don't have to be as strict with their sizing and confinement as you probably should be. It also means that buttons and other objects with text boxes natively attached can be scripted directly without having to also script their text boxes. But if you choose to not ignore text boxes, get ready for a lot of time scratching your head wondering why things aren't working as they should be.



Custom cursors:

These scripts do allow you to use custom cursors. Their use is limited, however. First of all, the documentation for new UI cursors is lacking. So these scripts do not currently allow the ability to resize a cursor's image. This means that you need to use images that have the size and aspect ratio you desire when you import them into Unity. I've found perfect squares to be ideal. Unity seems to stretch whatever image you use into a square, so images will lose their correct aspect ratios if you do not compensate.

The UIController script, however, does allow you to adjust the hotspot of cursors so they can be aligned correctly.

When you import an image to be used as a cursor, do make sure the Format is NOT set to Compressed. If so, the image may not be rendered correctly.



Inspector options:

In the inspector tab, each script has a number of customizable options. See the included documentation "Script Options" for details for each script.



Limitations:

Many of these scripts were written specifically for use with mouse controls, so many will not work with other forms of controllers without modification.

These scripts are tested using a single canvas with the Render Mode set to Screen Space - Overlay with the default settings of the Canvas Scaler component. Using multiple canvases may or may not work as intended. Using a setting other than Screen Space - Overlay may not work due to the method the scripts use to determine where the mouse cursor is located.

Anchors on objects and their parents can cause issues. I've worked to eliminate this issue, though I may have missed some situations. If all else fails, create a panel to fill the canvas, then use it as the main parent for the rest of your UI objects. The safest anchors for this parent to use are Middle/Center or Stretch.

Changing the default pivots on UI objects can and will cause issues. It is advised to not alter them in any way.

Custom cursors, at least in these scripts (using the new UI), are limited to the size and aspect you import them into Unity as. If you do not wish your cursors to be stretched, make sure there is appropriate empty space in the actual image file you import. Perfectly square images are ideal.



Contact and Support:

I must confess, I'm quite slow when it comes to checking email, and I'm a lightweight when it comes to scripting, so I would suggest these scripts be assumed to be "as is." However, if you do find an issue or need assistance, you're more than welcome to contact me at...

dctshinobi@hotmail.com

I can't guarantee a (fast) response, but I'll do my best to look into it and help out. Also, feel free to let me know if you release any projects using these scripts. It's always nice to see your work in action!

Thank you, I wish you great success, and to God be the glory!



Changelog:


	Version 5.0: 7/30/2015


	Updates:
	Now for Unity 5 officially!
	Added a movement multiplier. Also added some very limited functionality for canvases not set to Screen Space - Overlay.

------------------------------------------------------------------------------------------------

	Version 4.0: 3/2/2015


	Added scripts:
	UIController


	Removed scripts:
	IgnoreThisChild, CustomNormalCursor


	Updates:
	The Move/Resize/Scale series of scripts as will as the BringToFront script have been overhauled to work with a single UIController script. Now, there will only be one raycast at a time instead of as many as there were scripts.

	Also, new options in the PushPull script allow immediately pulling without the need for an initial push. 


	Issues resolved:
	Fixed issue of multiple raycasts fired with each frame or each button press.
	
	Fixed issue with Pointer Enter/Exit events enabling/disabling or not enabling/disabling scripts when they needed to.

------------------------------------------------------------------------------------------------

	Version 3.0: 2/14/2015


	Added scripts:
	MaximizeMinimizeRestore, PushPull, Ignore, IgnoreThisChild, CustomNormalCursor


	Updates:
	The Move, Resize, and Scale series of scripts have been updated to include the options to restrain an object to their parent/screen as well as use custom cursors. They have also been rewritten to be more efficient and effective. Raycasting has been improved for use with the new Ignore series of scripts and custom cursors.
	
	The BringToFront script has been given the option to run every frame, keeping an object at the front at all times.

	The Anchor script now uses Positions instead of LocalPositions. It also runs in LateUpdate () instead of Update ().

	All scripts that reference another object have been programmed to print a message in the console instead of creating an error at runtime.

------------------------------------------------------------------------------------------------

	Version 2.0: 1/12/2015


	Added scripts: ScaleHorizontal, ScaleVertical, and Anchor

------------------------------------------------------------------------------------------------

	Version 1.0: 12/11/2014


	Initial Release