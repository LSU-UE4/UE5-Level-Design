<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Finish Remaining 3 Ramps

<sub>[previous](../ramp/README.md#user-content-creating-custom-meshes) • [home](../README.md#user-content-ue4-intro-to-level-design) • [next](../double-jump/README.md#user-content-double-jumping)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Lets create the final ramp to complete the four touching ramps.  We will then add a center column that the player can run over.  We will have different angles that we would like to use in our final level. This is just a testbed to make sure that the game plays as we want given these different factors. 

<br>

---


##### `Step 1.`\|`SUU&G`|:small_blue_diamond:


Now lets add a ramp to run up and down and see how it feels.  It looks like **Content | Geometry | Meshes | SM_Wedge_B** will work as a ramp.  Drag it into the level and place and rotate it in front of the player start.  Remember that the **Red** or **X** axis is forward in Unreal. To get it to snap to the ground press the <btn>end</btn> button on the keyboard.

Run the game and you will see that the ramp is way too small and too steep to climb.  The player can not traverse it.  Lets fix this.

![run game ramp to small and can't climb](images/RunUneditedRamp.jpg)

Now this static mesh has a different grid material.  It is **MI_LDGrid_Local** which is different than the material we have on the floor.  On the floor the grid stays in world space and doesn't move with the actor.  In the **MI_LDGrid_Local** materail the grid moves with the static mesh in local space.  We will use this for all meshes we add to our floor plane.  Also, when you scale it the material keeps the 1 meter by 1 meter reference.

https://user-images.githubusercontent.com/5504953/127868139-d13a3926-b00b-415d-92de-797a435411ae.mp4

| `geometry.brushes`\|`Introduction To Level Design`| 
| :--- |
| :floppy_disk: &nbsp;&nbsp;"*Geometry Brushes are the most basic tool for level construction in Unreal. Conceptually, it is best to think of a Geometry Brush as filling in and carving out volumes of space in your level. Previously, Geometry Brushes were used as the primary building block in level design. Now, however, that role has been passed on to Static Meshes, which are far more efficient. However, Geometry Brushes can still be useful in the early stages of a product for rapid prototyping of levels and objects, as well as for level construction by those who do not have access to 3D modeling tools. This document goes over the use of Geometry Brushes and how they can utilized in your levels.<br><br>In general, you can think of Geometry Brushes as a way to create basic shapes for use in your level design process, either as permanent fixtures or as something temporary to test with while your artists finish creating final meshes.*" - [Unreal Engine Documentation](https://docs.unrealengine.com/4.26/en-US/Basics/Actors/Brushes/) |

Now lets adjust the scale of the ramp.  Change the **Scale X** to `10.0`, **Scale Y** and **Scale Z** to `5.0`. This will make the ramp longer and shorter and hopefully the player can climb it.

![alt_text](images/ResizeScaleOfFirstRamp.jpg)

Run the game and run up and down the ramp. I am happy with these settings.

https://user-images.githubusercontent.com/5504953/127868743-810ccfed-6592-46d4-8e58-509b8083ed21.mp4
So in a pinch we can use a geometry brush to create a static mesh without having to learn another software package. We want a cylinder in the middle of 4 ramps to act as a platform to connect them. Go to **Geometry | Cylinder** and drag on in front of the ramp.

![add cylinder to level in front of ramp](images/CylinderInLevel.jpg)

Now we can move to **Top** view and change it to **Lit** mode so we can make the radius so that then column thickness matches the ramp thickness.  If found that a value for the **Brush Settings | Outer Radius** of `600` matches the width nicely.

![alt_text](images/ScaleCylinderDiameter.jpg)
Now we can add materials to brushes just like we can to static meshes.  The problem is that each face is a separate material.  This means we have to select all the faces first.

Go to **Geometry | Select | Select All Adjacent Surfaces** to select all faces on the model.  Then drag **MI_LDGrid_Base** to the model.  The local one cannot be used as it is only for static meshes. 

![add base material to all faces of column](images/AddMaterialToBrush2.jpg)

Now we need to make the column as tall as the ramp. We can use the **Geometry | Z** setting and make it `500`.  Remember that it scales from the middle so the column could be buried under the ground.  Raise it and press the <btn>end</btn> key to place it back on the ground. Also adjust it so that it lines up right at the end of the ramp.  Use the different views to properly align the shape.

![make z height of column](images/MatchHeight.jpg)

Now for brushes we can adjust the pivot point. Sometimes it is not where we want it to be. For objects that lie on the ground, it is common to have the pivot point in a bottom corner (usually the same one) or the bottom center (say for the player character).  We can see that the ramp and the cylinder have different locations for their pivot points.

![notice wrong pivot location for cylinder compared to ramp](images/WeirdPivots.jpg)

You need to switch to an orthographic view, I picked **Right**.  Then on a vertice right mouse click to snap the pivot point.  I have to move the cylinder a bit out of the way of the other geometry to get this to work right.

Right click on the open graph while the cylinder is selected and press 

![right click on bottom vertice in right orthogrpahic view](images/MovePivotStep1.jpg)

![pivot moved to this vertice](images/PivotMoved.jpg)

![pivot moved to this vertice](images/PivotMoved.jpg)

![set pivot offset](images/SetPivotOffset.jpg)

Now to be more efficient we can convert this brush to a static mesh.  Select the cylinder brush and expand the **Brush Options** by pressing the arrow at the bottom exposing the **Create Static Mesh** button.  Press <kbd>Create Static Mesh</kbd> and select the **Geometry | Meshes** folder and call it `SM_Ramp_Cylinder` and press the green <kbd>Create Static Mesh</kbd> button on the **Select Path** pop-up.

![convert brush to static mesh](images/ConvertToStaticMesh.jpg)

Now it is converted to a static mesh so you can readjust the position if you had to move it back into the correct position.

![reposition column](images/RepositionMesh.jpg)

Now that it is a static mesh we can change the material to `M_LDGrid_Local`.

![change material to M_LDGrid_Local](images/ChangeSMMaterialToLocal.jpg)

![](../images/line2.png)

Now run the game and go on the ramp.  Woops, there is an issue there is NO collision on this converted brush!  Lets fix that.

https://user-images.githubusercontent.com/5504953/127878402-8ed214ca-144d-4d53-b6f4-4819be8e9a56.mp4

So lets open up the **SM_Ramp_Cylinder** in the static mesh editor.  Notice that it only has 48 vertices, so we do not need a seperate smaller model for collisions and can use the same mesh for rendering as we do for collisions.  Go to **Collision | Colision Complexity** and change it from **Project Default** to `Use Complex As Simple`.  Now you can preview this in the editor by selecting **Collision | Simple**.  You will see the vertices light up.

![use complex as simple for collision on cylinder](images/SetComplexAsSimple.jpg)

Run the game and you will see that the collisions are working again!

https://user-images.githubusercontent.com/5504953/127881414-51b2b02f-7708-4400-adff-d4b4169864b9.mp4

![](../images/line2.png)

| `lock.meshes`\|`Introduction To Level Design`| 
| :--- |
| :floppy_disk: &nbsp;&nbsp; Now when we are happy with our level design so far.  Our floor and our ramp and cylinder work the way I want.  Now there is a way in Unreal to lock these static meshes so they don't accidentally move.  It is very easy to accidentally move pieces out of position so this is a good precautionary measure. |

Select all the floor meshes (you can't just select the folder) and right click and press **Transform | Lock Actor Movement**.  Now when you go to move a floor piece it has a red slash and cannot be moved.  This can of course be deselected so you can move these meshe(s) again.

![lock floor meshes](images/LockFloorMeshes.jpg)

![lock transforms on two ramps](images/LockRampTransforms.jpg)


Create a folder called **Ramps** and place the ramp and cylinder in it.  Rename those objects so that they make sense to you.  Also, repeat locking the actor movement for these to static meshes as well if you are happy with them.


OK, lets save and update our repository.  Press **File | Save All** in **Unreal**. Press the <kbd>Source Control</kbd> button and select `Submit to Source Control...`. Add a **Commit** message and press the <kbd>Submit</kbd> button.

Open **GitHub Desktop** and press <kbd>Push origin</kbd> to update the server.  If you do not do this it will be saved locally but not on **GitHub**.

We will move on next to adding our first ramp to the game.

![save and commit changes to github](images/SaveAndCommit.jpg)

![push changes to github](images/PushToOrigin.jpg)

Unlock the ramps transform movement and move <btn>alt</btn> click on the widget and make a duplicate and rotate it around to other side. Use your views to line up exactly in place.  You can also use <btn>End</btn> to make it stick to the ground if you moved it along the Z axis by accident.

https://user-images.githubusercontent.com/5504953/127900627-d2023450-bba7-4461-af79-9691440a7ee8.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

The reason we build test levels is to confirm that our interactions and cameras work.  It is devlishly hard to get a 3-D camera to work without occlusion in busy levels (or not so busy levels). Test the game and make sure you can run up and down both ramps without getting hung up on a ledge. Also make sure the camera sees the player correctly going up and over the ridge.  Make changes to the camera if necessary.  I am happy with mine.

https://user-images.githubusercontent.com/5504953/127901204-ce6047d1-74d8-4719-b4e6-106feed194c1.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`SUU&G`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to the game and now lets make the ramp a different slope.  Lets make it less steep.  Select the second ramp and change the **X** Static Mesh Scale and make it `15`.  Reposition the mesh back into place.

https://user-images.githubusercontent.com/5504953/127902011-7c375442-8faa-45f1-b8d2-bc4bf8894f14.mp4


<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`SUU&G`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now lets duplicate the final two ramps and rotate them 90 degrees into position.  Make the lenght on one `8` and the other `15`.

https://user-images.githubusercontent.com/5504953/127903077-5d5d8cde-12e8-4e70-81a5-20c1e386c46a.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`SUU&G`| :small_orange_diamond:

Run the game and test the ramps out.  Again, look for issues with the camera.  In a later tutorial we will adjust the player angle and speed based on the ramp.

https://user-images.githubusercontent.com/5504953/127903749-18c1504a-0e4e-46db-bbae-917d0a9691b0.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond:

Renamethe ramps with a postfix indicating the different scalesz along **X**. Freeze the transforms on the ramps to properly organize the **World Outliner**.

![rename and freeze four ramps](images/FreezeTransformFourRamps.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Type `Text Render` in the modes panel to add a 2-D text to add on top of the ramps to identify it from afar.  Type in as the **Text** field: `Ramps`. Change the **Horizontal Alignment** to `Center`. Move it to ontop of the ramp.

![add ramps text render](images/AddRampsTextRender.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Make it really big and place it on top of the ramp. Set the **World Size** to `258` and readjust the position.  Pick a color so that it constrasts nicely with the sky. Now we want to see if from most parts of the level so duplicate the text render and rotate it 90 degrees so you can see the text from all angles (as the text is not 3-D). Raise one so they don't occlude each other and run the game to test whether they get in the way.  They shouldn't mess with the player movement.  When you are happy rename these text render components to `Ramps Title 1` and `Ramps Title 2` and lock their transforms.

https://user-images.githubusercontent.com/5504953/128019875-39f769c8-b0a2-49bd-aa18-13dce32bc4b2.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Rename the text actors in the **World Outlinder** and move them to the ramps folder.

Now it is time to save and update the repository.  Press **File | Save All** in **Unreal**. Press the <kbd>Source Control</kbd> button and select `Submit to Source Control...`. Add a **Commit** message and press the <kbd>Submit</kbd> button.

Open **GitHub Desktop** and press <kbd>Push origin</kbd> to update the server.  If you do not do this it will be saved locally but not on **GitHub**.

We will move on next to adding our first ramp to the game.

![save and commit changes to github](images/SaveAndCommit.jpg)

![push changes to github](images/PushToOrigin.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Double Jumping">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../ramp/README.md#user-content-creating-custom-meshes)| [home](../README.md#user-content-ue4-intro-to-level-design) | [next](../double-jump/README.md#user-content-double-jumping)|
|---|---|---|
