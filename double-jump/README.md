![](../images/line3.png)

### Double Jumping

<sub>[previous](../ramps2/README.md#user-content-finish-remaining-3-ramps) • [home](../README.md#user-content-ue4-intro-to-level-design) • [next](../gameplay-scale/README.md#user-content-gameplay--scale-register)</sub>

![](../images/line3.png)

Now we are going to figure out how high the player can jump for getting onto platforms.  This is our core mechanic so it is important to be happy with this and understand it better.  Lets start by making a hole in a column to vertically jump through.  This will give us information about the size of the portal to fit the player **and** the camera.  We will do this for easy single jump, hard single jump, easy double jump and hard double jump.   We also should add a double jump to the physics in the **ThirdPersonCharacter** blueprint.

<br>

---


##### `Step 1.`\|`UE5LD`|:small_blue_diamond:

Go to **Select Mode** and switch back to **Modeling** mode.  Select a **Box** and make it a **Width** of `400`, **Depth** of `800` and **Height** of `1000`. Press the <kbd>Complete</kbd> and put it on the ground.

![Add a bxp box and move player start in front of it](images/createNewBox.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5LD`|:small_blue_diamond: :small_blue_diamond: 

Now go back to ??? mode and lift the box and press the <kbd>End</kbd> key and place it next to the ramps you just created (give yourself some breathing room). 

![Resize box to make it larger](images/snapToGround.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5LD`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Lets create a second box that we will use to cut a hole in the existing one. Go back to the **Modeling** mode and create another **Box** that is a **Width** of `775`, **Depth** of `408` and **Height** of `750`. Press the <kbd>Complete</kbd> and put it on the ground next to the other box.

![create second smaller box](images/secondBox.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5LD`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Place smaller box through bigger box.  Use the top, side and front views to center it through the shape. You will want the smaller box to cut a hole through the middle of the bigger one.  This will create our jump platform.  I have adjusted it to a meter in height.

![center small box in larger one](images/topFrontView.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5LD`| :small_orange_diamond:

We are able to use these shapes as a positive volume, or we can use it as a negative volume to subtract one shape from a positive volume.  This is by using a Mesh Boolean function.

Select both boxes in the scene. Now go to the **PolyModel** group and select **MshBool** (Mesh Boolean).  This will allow us to subtract one shape from the other.  Depending on the order you clicked them on it will be either **Difference A-B** or **Difference B-A**. When you are ready, press the <kbd>Accept</kbd> button to create a new shape. 

![use MshBool to subtract shapes](images/meshBool.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond:

Create a new folder called 
 
![add subtractive volume](images/newShape.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now lets fix the pivot so it is at the ground plane.  Change to **Front** view and right click the bottom right vertex.

![fix pivot to bottom right](images/RightClickBottomRightVertice.jpg)


![](../images/line2.png)

##### `Step 8.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Right click on the open graph and select **Pivot | Set as Pivot Offset**.

![alt_text](images/SetPivotOffset.jpg)

![](../images/line2.png)

##### `Step 9.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now select **both** the additive and subtractive brushes and we will convert them to a single static mesh.  Press the <kbd>Create Static Mesh</kbd> button then select the **Geometry | Meshes** folder and call this mesh `SM_JumpPlatform_Low`. Press the green <kbd>Create Static Mesh</kbd> button to complete the conversion.

![convert to static mesh](images/ConvertToStaticMesh.jpg)

![](../images/line2.png)

##### `Step 10.`\|`UE5LD`| :large_blue_diamond:
Remember there is no collision volume. Open up **SM_JumpPlatform_Low** in the editor and change **Collision | Collisoin Complexity** to `Use Complex Collisions As Simple`.  Now turn on **Collision | Simple Collision** and you should see the collision mesh being the same as the static mesh.

![add collision volume to low jump](images/AddCollisionToLowJump.jpg)

![](../images/line2.png)

##### `Step 11.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: 

Now we want to understand the scale of the world we need to build and this is based on the player physics.  If the player has real world physics we can use real world scale (a floor of a building is 20 feet tall for example).  But with exaggerated physics we need exagerated scale for it to work.  So run the game and jump and my character based on my settings can jump 3 meters (~9.8 feet).

https://user-images.githubusercontent.com/5504953/128029695-3bf2ac00-aa39-4e49-a3ac-c64221fce573.mp4

![](../images/line2.png)


##### `Step 12.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Run the game and jump through the hole. Make sure the camera clears.  In my case it does.  But we need to add a double jump to the game to see if this causes a problem.

https://user-images.githubusercontent.com/5504953/128029891-740da1f1-52d3-464b-9d12-d47390dd9daf.mp4

![](../images/line2.png)

##### `Step 13.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Open the **ThirdPersonCharacter** blueprint and select the **Event Graph** and go to the **Jump** section and make room to add nodes for double jumping.

![add room to jump section in thirdpersoncharacter blueprint](images/image_53.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Right click on the open graph and add a **Event On Landed** node to the blueprint. Connect it to the **Stop Jumping** as we will stop jumping when the player hits the ground.  Disconnect ththe **Stop Jumping** node by right clicking on **InputAction Jump** and select **Break Link to Stop Jumping**. Press the **Compile** button and run the game and it should behave the same way as previously.

https://user-images.githubusercontent.com/5504953/128031003-ef83222c-8552-4e3d-8310-369d8eb11a32.mp4

![](../images/line2.png)

##### `Step 15.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: 

Add a **DoN** node.  This runs a given number of times and stops until it is reset.  Set the **N** value to `2`.  This means that it will start at **0** then when the player presses the **Jump** button it will go to **1**, then when the player presses it again it will go to **2**.  When the player lands it will be reset back to **0**.  Disconnect the **Jump** execution pin and attach the **InputAction Jump** execution pin to the **DoN** execution pin.

![add a DoN node](images/image_55.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

The output of the **DoN** pin is an integer (any whole number, either positive or negative).  The switch will allow us to run a different piece of code dending on the value of the integer which in this case will be **0, 1 or 2**. Pull from the **DoN | Counter** pin and type **Switch on Int** and add this node.

![add switch on int to counter](images/image_54.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Connect the output **Exit** execution pin from **DoN** to the **Switch on Int** node.  Make sure the output of the **Counter** pin goes to the **Switch on Int | Selection** pin.  Press the **Add pin +** three times to get `0, 1, 2` execution pins for the switch statement.

Connect the output of **1** to the input execution pin of the **Jump** node.  Connect the execution pin from the output of the **Stop Jumping** node to the **Reset** pin of the **DoN** node.  This way the **DoN** resets the **N** integer to `0` when this is run when the player lands.So it starts at **0**, the player presses jump then the **Jump** node gets executed. When the player lands it resets back to 0 and the player can jump again.

![add three pins and connect 1 to jump](images/image_56.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Right click on the **Event Graph** and select a **Launch Character** node to give the player an additional vertical force to make them double jump.

![add launch character node](images/image_57.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Connect the output of the **Switch on Int | 2** execution node to the **Launch Character** execution pin. Change the **Z** value in **Launch Velocity** to `300`.

![add upwards force](images/image_58.png)

![](../images/line2.png)

##### `Step 20.`\|`UE5LD`| :large_blue_diamond: :large_blue_diamond:

Go to the blueprint an select the **Character Movement** component.  In the **Details** panel type in `jump` and look for **Jump Z Velocity**.  Change this to `500`.

![adjust jump z velocity](images/image_59.png)

![](../images/line2.png)

##### `Step 21.`\|`UE5LD`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

If you build lighting or run the game you will notice sometimes that the static meshes that go from a brush to a mesh in the editor will show up black.

Open SM_JumpPlatform_Low and in **General Settings | Light Map Resolution** change the value to `256` and in **Light Map Coordinate Index** change this value to `1`.

Now build lighting again and the problem should be fixed.

![black empty texture](images/NoTextures.jpg)

![adjust lightmap resolution and index](images/AdjustLightmapIndex.jpg)

![texture lit properly in game](images/FixedLightingOnModel.jpg)


![](../images/line2.png)

##### `Step 22.`\|`UE5LD`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now we do not judge the distances based on the player model as this is not used for collision.  It is the **Capsule Component** in the **Third Person Character** blueprint. Chnage the **Capsule Component | Rendering | Hiddent in Game** and deselect it.


Run the game and press jump multiple times. You should notice a boost to vertical height on the second press but not a third press.  Also, if you double jump when falling downwards it pauses the player creating an odd hiccup.  On the next page we will fix this.

Save and Commmit all of your changes to github.

https://user-images.githubusercontent.com/5504953/128046337-9a2ae249-7847-40f4-a9a8-9e90c17a433d.mp4

![save and commit changes to github](images/SaveAndCommit.jpg)

![push changes to github](images/PushToOrigin.jpg)

___

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Gameplay and Scale Register"> -->
![next up next tile](images/banner.png)

![](../images/line.png)


| [previous](../ramps2/README.md#user-content-finish-remaining-3-ramps)| [home](../README.md#user-content-ue4-intro-to-level-design) | [next](../gameplay-scale/README.md#user-content-gameplay--scale-register)|
|---|---|---|
