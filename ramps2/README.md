<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Finish Remaining 3 Ramps

<sub>[previous](../ramp/README.md#user-content-creating-custom-meshes) • [home](../README.md#user-content-ue4-intro-to-level-design) • [next](../readme/README.md#user-content-readmemd-file)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Lets create three more ramps at each other end of the the center platform.  We will have different angles that we would like to use in our final level. This is just a testbed to make sure that the game plays as we want given these different factors.

<br>

---


##### `Step 1.`\|`SUU&G`|:small_blue_diamond:

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

Name and lock the ramps again to organize the **World Outliner**.

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Type `Text Render` in the modes panel to add a 2-D text to add on top of the ramps to identify it from afar.  Type in as the **Text** field: `Ramps`. Change the **Horizontal Alignment** to `Center`. Move it to ontop of the ramp.

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Make it really big and place it on top of the ramp. Set the **World Size** to `258` and readjust the position.  Pick a color so that it constrasts nicely with the sky. Now we want to see if from most parts of the level so duplicate the text render and rotate it 90 degrees so you can see the text from all angles (as the text is not 3-D). Raise one so they don't occlude each other and run the game to test whether they get in the way.  They shouldn't mess with the player movement.  When you are happy rename these text render components to `Ramps Title 1` and `Ramps Title 2` and lock their transforms.

![alt_text](images/.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

OK, lets save and update our repository.  Press **File | Save All** in **Unreal**. Press the <kbd>Source Control</kbd> button and select `Submit to Source Control...`. Add a **Commit** message and press the <kbd>Submit</kbd> button.

Open **GitHub Desktop** and press <kbd>Push origin</kbd> to update the server.  If you do not do this it will be saved locally but not on **GitHub**.

We will move on next to adding our first ramp to the game.

![save and commit changes to github](images/SaveAndCommit.jpg)

![push changes to github](images/PushToOrigin.jpg)

___


<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Double Jumping">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../ramp/README.md#user-content-creating-custom-meshes)| [home](../README.md#user-content-ue4-intro-to-level-design) | [next](../readme/README.md#user-content-readmemd-file)|
|---|---|---|
