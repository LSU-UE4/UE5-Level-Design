![](../images/line3.png)

### Long Jump

<sub>[previous](../gameplay-scale/README.md#user-content-gameplay--scale-register) • [home](../README.md#user-content-ue4-intro-to-level-design) • [next](../moving-platform/README.md#user-content-moving-platform)</sub>

![](../images/line3.png)

We also want to know how far a player can jump to overcome gaps in buildings or platforms.  How far can a player jump before they land on the ground again? We will look at standing jumps (players jumping from a confined space) and running jumps where players have room to run.  The player is only able to jump forwards so this will always be along the **X** axis locally in player space.

<br>

---


##### `Step 1.`\|`UE5LD`|:small_blue_diamond:

Lets move to an empty side of the level where you will put the platforms. Duplicate a new title on top of that area and call it `Long Jumps`. Create a new folder called `Jump Ramps` in the **World Outliner** and move the text into it. Rename the text appropriately to `Long Jump Title` and `Long Jump Title2` .

![Add long jump text to empty part of level](images/longJumps.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5LD`|:small_blue_diamond: :small_blue_diamond: 

For a change lets add a staircase instead of a ramp to run onto a flat ramp to jump over for a long jump.  Enter into **Modeling Mode** and select the **Shapes | Stairs**.  Now adjust the **Width** to be 3 meters wide by setting it to `300` cm.  Now the height will be 8 steps of `20`cm which will be 1.6 meters high. Now make sure you zero out the **Rotations** so they are set to `0`, `0`, `0`. Press the <kbd>Complete</kbd> button.

![add stairs to modeling](images/addStairs.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5LD`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now lets add a ramp after the to top of stairs so you can get a running jump.  Now add a **Shape | Box** that is a **Width** of `300`, **Depth** of `200` and **Height** of `160`.  Now make sure you zero out the **Rotations** so they are set to `0`, `0`, `0`. Press the <kbd>Complete</kbd> button.

![add a ramp](images/addRamp.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5LD`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Align the stairs and ramp. In your top down and side/front views make sure they all line up so that the edges are perfectly aligned as if it is one shape. 

![Align the stairs and ramp](images/placeNextToEachOther.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5LD`| :small_orange_diamond:

In **Modeling Mode** select both the stairs and the ramps.  Select **Mesh Ops | Merge**.  Keep the default settngs.  Notice that it will remove the original two pieces which is what we want, we just need the merged shape.  Now make sure you zero out the **Rotations** so they are set to `0`, `0`, `0`. Press the <kbd>Complete</kbd> button.

![duplicate other end of jump platform](images/mergeMeshes.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond:

Now select the new merged shape back in **Select Mode**.  Right click and choose **Browse to Asset**. In my case I had some failed attempts so I **Deleted** them.  I then renamed the new mesh to `SM_LongJump` and moved it to the **Meshes** folder.

![name and store new jump platform](images/organizeData.png)


![](../images/line2.png)

##### `Step 7.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now make sure the end of the platform matches a line marker on the ground.  We want to count the length in meters a player can jump.  Also rename the object to `LongJump1_Short` and place it in the **Long Jumps** folder in the **World Outliner**.

![align jump platform and rename in world outliner](images/alignRename.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now lets move the **Player Start** actor in front of the jump platform so it is facing dead on so we can make a jump.

![mvoe player start in front of jump platform](images/movePlayerStart.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now do a standing jump while pressing forward (<kbd>up arrow</kbd> or <kbd>W</kbd>) key.  Count the number of tiles the player can cover. My player covered roughly 8 meters.

**Gameplay Register**
|Element | Measure|
|-------------|-------------|
|Single Jump | 200 |
|Double Jump | 324|
|Standing Long Jump | ~800 | 

https://user-images.githubusercontent.com/5504953/182170440-a4f2a526-232c-45a9-9ce0-9ea74f5cb894.mp4

![](../images/line2.png)

##### `Step 10.`\|`UE5LD`| :large_blue_diamond:

Duplicate the stairs and the platform for the other end of the jump and rotate it 180°. Place it so that there is a 8 meter gap (8 cubes on the floor tile). It is easiest to do the placment from the **Top** view.

![duplicate and rotate jump platform](images/dupeAndRotate.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: 

Run the game and jump.  Test the short jump ramp and make adjustments. I can clear 8 meters perfectly from a standing jump.

https://user-images.githubusercontent.com/5504953/182174672-d14dcdab-427a-44ec-ba3a-e8b7be0e6080.mp4

![](../images/line2.png)


##### `Step 12.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Now on your own calculate a running single jump and running double jump.  I ran up the stairs and jumped as late as possible.

![single double jump](images/singleDouble.png)

Update the gameplay register.

**Gameplay Register**
|Element | Measure|
|-------------|-------------|
|Single Jump | 200 |
|Double Jump | 324|
|Standing Long Jump | ~800 | 
|Running Single Jump | ~1100 | 
|Running Double Jump | ~1650 | 

![](../images/line2.png)


##### `Step 13.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Lets start with duplicating the ramps for the Running Single Jump of 11 meters.

**Gameplay Register**
|Element | Measure|
|-------------|-------------|
|Single Jump | 200 |
|Double Jump | 324|
|Standing Long Jump | ~800 | 
|**Running Single Jump** | **~1100** | 
|Running Double Jump | ~1650 | 

![duplicate ramps for running jump of 1100 cm](images/runningJump.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Lets do the same again by duplicating the ramps for the Running Double Jump of 16.5 meters. Make sure you name the new jump platforms in the **World Outliner**.

**Gameplay Register**
|Element | Measure|
|-------------|-------------|
|Single Jump | 200 |
|Double Jump | 324|
|Standing Long Jump | ~800 | 
|Running Single Jump | ~1100 | 
|**Running Double Jump** | **~1650** | 

![duplicate ramps for running double jump of 1650 cm](images/runningDouble.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: 

![alt text](images/.png)

![](../images/line2.png)

Add to GitHub by checking in changes in Unreal and pushing to the server in **GitHub Desktop**.

![alt_text](images/Github.jpg)

![](../images/line2.png)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Moving Platform">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../gameplay-scale/README.md#user-content-gameplay--scale-register)| [home](../README.md#user-content-ue4-intro-to-level-design) | [next](../moving-platform/README.md#user-content-moving-platform)|
|---|---|---|
