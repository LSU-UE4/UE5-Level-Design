<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

### Lock Cameras and Mechanics

<sub>[previous](../setting-up/README.md#user-content-setting-up-unreal--github) • [home](../README.md#user-content-ue4-hello-world) • [next](../holodeck/README.md#user-content-setting-up-holodeck)</sub>

<img src="https://via.placeholder.com/1000x4/45D7CA/45D7CA" alt="drawing" height="4px"/>

Blocking out or **Gray Blocking** a level is standard practice in most level based video game genres.  It allows us to navigate and play through a space to judge game mechanics and decide if the level works or not.  There is no use to adding lots of custom great art, to then realize that the game play does not work as designed.  This allows us to test the interactivity first before adding artwork to a level.

Now the first step before gray blocking is to make a final decision on physics of our main controllable character.  How would I know how to place platforms without knowing how far the player can jump.  We also need a near final camera as it will need to fit or adapt to the environment you set up.  We will do a very quick version of this first step that sometimes takes months/years on novel mechanics design.

The same thing could be true of any other application.  Why not as an architect, build a very simple version of the structure and navigate it first.  See what you like and don't like about your rough draft.  Then when you are happy you can go back to your modelling software and prepare a final detailed structure.

In this case I am envisioning a third person platformer like **Mario** and we will customize the default settings to alter the behabior to be more appropriate for this genre. Lets take a quick look at defining our paramters.

<br>

---

##### `Step 1.`\|`SUU&G`|:small_blue_diamond:

Now open the **ThirdPersonCharacter** blueprint that you find in **Content | ThirdPersonBP | Blueprints | ThirdPersonCharacter**. Make sure you are in the **Viewport** tab. Now click on the **Camera Boom** component.  It is the parent of the FollowCamera.  This acts as a spring so that when the camera collides with geometry it acts as a spring to keep the camera from going into geometry. This is represented with the **red** arrow in the editor.

![open the thirdpersonncharacter blueprint](images/image_04.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 2.`\|`FHIU`|:small_blue_diamond: :small_blue_diamond: 

The camera is very tight to the player light an action shooter.  We want a camera that is a bit further away.  In our charactre blueprint there is a boom that adjusts the distance and angle of the camera from the player. Select the **Camera Boom** component.  Change the **Target Arm Length** to a number like `750`.  Then adjust the **Target Offset Z** value to a value like `218`. Now the camera is above and further away but is not rotated facing the player.  Lets fix that.

![pull camera away from the player](images/image_07.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 3.`\|`SUU&G`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:
Now select the **FollowCamera** component and adjust the **Rotation Y** to `345`.  This will pitch the camera down 15 degrees pointing towards the back of the player's head.

![rotate camera to face player](images/image_20.png)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 4.`\|`SUU&G`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Press **Compile** in the blueprint then run the game and run into the back wall to see that the spring arm stops (and the player sort of disappears).  We will fix that in a later lesson when we dig more into blueprints. For now you can see that our camera is further back and high up looking down at the player.

https://user-images.githubusercontent.com/5504953/127748065-7bff5778-c2d0-49a4-a289-3b4acd6a01c1.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 5.`\|`SUU&G`| :small_orange_diamond:

Run the game again and look how the arrow keys for left and right differ from the a and d key in the game.  The **AWSD** moves the player and on the arrow keys left and right move the camera.  Lets make them the same.

https://user-images.githubusercontent.com/5504953/127748151-95a8dc2a-8508-4d69-9ca6-1f58dbb5ea4a.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 6.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond:

The controls are defined in the project settings.  Select the **Settings** button and go to **Project Settings**.  Go to **Engine | Input** and open up the arrow next to **Axis Mappings**.  Go to **Left** and **Right** under **TurnRate** and press the **X** to delete both of them.

![go to settings and remove turn rate](images/image_09.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 7.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Open the **Axis Mappings | Move Right** variable and press the **+** (plus symbol) button twice to add controls for left and right.  Add a **Right** keyboard button and set the **Scale** to `1.0` and a**Left** keyboard button with a **Scale** of `-1.0`. Press the **Compile** button in the blueprint.

![add left and right controls to game](images/image_11.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 8.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Run the game again and now the arrow keys act just like the **WASD** keys and we are at parity.  Try plugging in a controller to play it as well!

https://user-images.githubusercontent.com/5504953/127748315-f24cc98e-51c8-4da0-aa54-86a93d065816.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 9.`\|`SUU&G`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Open up the **ThirdPersonCharacter** blueprint and select the **CharacterMovement** component.  This is where all the adjustments for player physics is held.  Let's first change the gravity.  We want a bit of moon like physics for **Gravity**. If you hover the cursor over **Gravity Scale** you will get a description of what it does.  The most common type of setting normalizes between a range of 0 and 1.  In this case 0 would be no gravity, 1 is earth gravity and anything larger than 1 will apply a greater gravitational force.  Let's make it more like the moon and set it to `.75`.

![adjust gravity for jump](images/image_13.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 10.`\|`SUU&G`| :large_blue_diamond:

Press the **Compile** button on the blueprint and run the game.  Now look at how the player's gravity changes and the player floats more when jumping. The physics feel like you are on the moon.

https://user-images.githubusercontent.com/5504953/127748436-979e1cfc-2cc7-417a-8b61-8c1ec1c15d1f.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 11.`\|`SUU&G`| :large_blue_diamond: :small_blue_diamond: 

Lets make a few more changes.  Lets make our character run a bit faster.  In the blueprint change the **Character Movement: Walking | Max Walk Speed** to `800`. Play the game and tune the value to your liking.

![make player run faster](images/image_14.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 12.`\|`SUU&G`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Now lets make the player jump higher and give the ability for the player to adjust his direction mid flight.  In **Character Movement: Jumping / Falling** change **Jump Z Velocity** to `700.0` to make the player jump height. To give you more control in the air after you jump you can increase the **Air Control** to `0.5`. Play the game and tune the numbers to your liking. None of these numbers are \"correct\" or \"right\".  These are all up to you and how you want your character to move.

![make player jump higher](images/image_15.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 13.`\|`SUU&G`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

We will make one final change and have very snappy turning speed.  We will adjust the **Character Movement (Rotation Settings) | Rotation Rate Z** to `1000`. Play the game and tune the numbers to your liking.

![adjust rotation rate of player character](images/image_16.jpg)

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>

##### `Step 14.`\|`SUU&G`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Play the game and make any changes to what I suggested.  Get the player to move the way you envision a player should move in an arcady third person game.

https://user-images.githubusercontent.com/5504953/127748602-74b22262-4dc7-41c8-9465-a3b14ce6b8e3.mp4

<img src="https://via.placeholder.com/500x2/45D7CA/45D7CA" alt="drawing" height="2px" alt = ""/>


##### `Step 15.`\|`SUU&G`| :large_blue_diamond: :small_orange_diamond: 

Commit and push your changes in GitHub Desktop and we will move on to setting up a new level to do some prepatory work before we can commence gray blocking.

![commit and push changes to github](images/CommitChangesToGitHub.jpg)

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

<img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Set Up Level">

<img src="https://via.placeholder.com/1000x4/dba81a/dba81a" alt="drawing" height="4px" alt = ""/>

| [previous](../setting-up/README.md#user-content-setting-up-unreal--github)| [home](../README.md#user-content-ue4-hello-world) | [next](../holodeck/README.md#user-content-setting-up-holodeck)|
|---|---|---|
