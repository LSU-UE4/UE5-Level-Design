<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Long Jump

<sub>[previous](../gameplay-scale/README.md#user-content-gameplay--scale-register) • [home](../README.md#user-content-ue4-intro-to-level-design) • [next](../moving-platform/README.md#user-content-moving-platform)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

We also want to know how far a player can jump to overcome gaps in buildings or platforms.  How far can a player jump before they land on the ground again? We will look at standing jumps (players jumping from a confined space) and running jumps where players have room to run.  The player is only able to jump forwards so this will always be along the **X** axis locally in player space.

<br>

---


##### `Step 1.`\|`SUU&G`|:small_blue_diamond:

Lets move to an empty side of the level where you will put the platforms. Duplicate a new title on top of that area and call it `Jump Ramps`. Create a new folder called `Jump Ramps` in the **World Outliner** and move the text into it. Rename the text appropriately.


![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

For a change lets add a staircase instead of a ramp to run onto a flat ramp to jump over.  Add a **Geometry | Linear Stair Brush** to the level. Change **Number of Steps** to `15`.",

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`SUU&G`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Since each step is 20 units this is `300` units high.  Add another **Box** bsp and make it `300` units high.  Line it up perfectly with the stairs. Make it narrow so that you have to do a standing jump.

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`SUU&G`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:
Lets make a change to the material. Lets color code it to warn the person playing it that there is a specific meaning to this area.  We can use the color green to indicate that the player will be constrained from running in some way.  Maybe there will be a cut scene and when they get to the top of the stairs that the exit will be blocked and all they can do is a standing jump.

Now in gray blocking we can't implement all the mechanics of the level as we are just trying to get a sense of the space.  So we can create materials that indicate **beats** we want.

We will use a material instance to alter the color of the texture.  Right click on **M_????** and rename it to `MI_????_ConstrainedMovement`.

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`SUU&G`| :small_orange_diamond:

Duplicate the stairs and the platform for the other end of the jump. 

![duplicate other end of jump platform](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond:

Use your views to line up the back ramp so that it matches the platform perfectly.  Leave a gap to jump over.  It shouldlook like:

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now do a standing jump while pressing forward (<kbd>up arrow</kbd> or <kbd>W</kbd>) key.  Count the number of tiles the player can cover.  Adjust the gap to match this.

**Gameplay Register**
|Element | Measure|
|-------------|-------------|
|Single Jump | 200 |
|Double Jump | 324|
|Standing Long Jump | ~600 | 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Move player start in front of the ramp and rotate it so that it faces forward.  You should see a blue arrow that shows where the player will start pointing when you run the game.",

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Test the short jump ramp and make adjustments.  You should be able to jump accross it from standing.  No running jump should be necessary.  Measure the jump distance and add text to the ramp by going into an orthoganal view and center right clicking on the middle mouse button and dragging to measure the distance in centimeters.  In my case it was `645` uu.  Finally name the files and organize them in the world outliner.

**Gameplay Register**
|Element | Measure|
|-------------|-------------|
|Single Jump | 200 |
|Double Jump | 324|
|Standing Long Jump | 645 | 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`SUU&G`| :large_blue_diamond:


Your world outliner should have all ramp objects in the **Jump Ramps** folder names appropriately. Duplicate it to have a copy as a starting point for the next ramp.

Select all brushes for the ramp and create a **Static Mesh** called `SM_LongJump_Standing`. Fix any rendering Selissues or collision issues. Change **Collision Complexity** to `Use Complex As Simple` and adjust the **Light Map Coordinate Index** to `1`, and **Light Map Resolution** to `256`.

![organize data in folder](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`SUU&G`| :large_blue_diamond: :small_blue_diamond: 

Take the copy of standing jump ramps and lets make a medium jump.  You should not be able to make this from a standing jump but should be a relatively easy running jump.  Run along the ground and get a good running jump distance. Adjust the distance, update the name of the objects and the jump distance text.

**Gameplay Register**
|Element | Measure|
|-------------|-------------|
|Single Jump | 200 |
|Double Jump | 324|
|Standing Long Jump | 645 | 
|Running Long Single Jump | ~900 |

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`SUU&G`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Make a third jump where you can't make it with a single running jump but need to double jump.  Should be easy to make. Adjust the distance, update the name of the objects and the jump distance text.

**Gameplay Register**
|Element | Measure|
|-------------|-------------|
|Single Jump | 200 |
|Double Jump | 324|
|Standing Long Jump | 645 | 
|Running Long Single Jump | ~900 |
| Running Long Double Jump | ~ 1300 | 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`SUU&G`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Add to GitHub by checking in changes in Unreal and pushing to the server in **GitHub Desktop**.

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`SUU&G`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 15.`\|`SUU&G`| :large_blue_diamond: :small_orange_diamond: 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 16.`\|`SUU&G`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 17.`\|`SUU&G`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 18.`\|`SUU&G`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 19.`\|`SUU&G`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 20.`\|`SUU&G`| :large_blue_diamond: :large_blue_diamond:

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 21.`\|`SUU&G`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

![alt_text](images/.jpg)

___

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Moving Platform">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../gameplay-scale/README.md#user-content-gameplay--scale-register)| [home](../README.md#user-content-ue4-intro-to-level-design) | [next](../moving-platform/README.md#user-content-moving-platform))|
|---|---|---|
