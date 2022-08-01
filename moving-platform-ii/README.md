![](../images/line3.png)

### Moving Platform II

<sub>[previous](../moving-platform/README.md#user-content-moving-platform) • [home](../README.md#user-content-ue4-hello-world)</sub>

![](../images/line3.png)

Lets finish up the moving platform so it can go from beginning to end and back.

<br>

---


##### `Step 1.`\|`UE5LD`|:small_blue_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5LD`|:small_blue_diamond: :small_blue_diamond: 

![alt text](images/.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5LD`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5LD`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5LD`| :small_orange_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 9.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 10.`\|`UE5LD`| :large_blue_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: 

![alt text](images/.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

![alt text](images/.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt text](images/.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

![alt text](images/.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: 

![alt text](images/.png)

![](../images/line2.png)

##### `Step 16.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

![alt text](images/.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 20.`\|`UE5LD`| :large_blue_diamond: :large_blue_diamond:

![alt text](images/.png)

![](../images/line2.png)

##### `Step 21.`\|`UE5LD`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

![alt text](images/.png)



Add another **Branch** node then connect the execution pin from the **False** execution pin from the previous **Branch** node.  So if the player doesn't press the **Set Start Position** then we need to check to see if they are pressing the **Set End Position**.  Drag the **Get bSet End Position** variable and connect it to the **Branch | Condition** pin. Drag and add a **Set bSet End Position** to reset the second destination boolean. Make sure it is set to `false`. Add a **Set Ending Postion** varibale to the graph. Drag a Connect the execution pins from the **Set Ending Position** node to the **Set bSet End Position** node. Add a **Get Actor Location** node and connect it to the **Ending Position** pin. With the mouse drag with left button pressed and highlight all the nodes and press the **C** button and add a comment `Set Start and End Location of Platform`. Press the **Compile** button and you should see a green checkmark.  If there is a red X correct the error as the blueprint will not run.

https://user-images.githubusercontent.com/5504953/128609018-c9af3276-e29b-498f-abb8-b03a3af7b67d.mp4

Now lets test our work to see what this does.  First clean up our **World Outliner** and make sure all objects are named and in the appropriate folders. Go to the game window. Adjust the starting position for the platform and press the **Set Start Position** box in the **Details** panel.  Notice that the **Starting Position** vector updates with the current location.  Then **move** the platform up a few meters and set the **Set End Position** and notice that it updates the **Ending Position** variable.  It should look like this:

https://user-images.githubusercontent.com/5504953/128609437-f3c2f011-0091-4694-ae88-ebe4685af1ab.mp4

We need to add a new event that sends the platform to one location to another. Click on the **Event Graph** tab where we will put the logic to move the platform. .  Right click on the empty graph and lets add a **Add Custom Event** node. Name this event: `Go To Location And Back`.

Remove the **Event Tick** and **Event ActorBeginOverlap** event nodes as we will not use these. Go to **Begin Play** and pull off of the execution pin and call the above custom event  by adding a node to trigger the event we just created **Go To Location And Back**.  This will run this function when you press the **Play** button.  It will run the **Event Begin Play** execution node once.

![call node go to location and back from begin play event](images/CallGoToLocation.jpg)

Pull off of the **GetToLocationAndBack** node's execution pin and add a **Move Component To** node. Drag a reference of the **Static Mesh Component** from the **Component** section onto the graph.  Attach its output to the **Component** input pin on the **Move Component To** node. Add a **Get End Position** node and put it into the **Target Relative Location** pin.  Connect the output of the **Ending Position** pin to the **Target Relative Location** in the **Move Component To** node.

Add a **Get Speed** node and connect it to the **Over Time** pin in the **Move Component To** node. Right click on the empty graph and add a **Get Actor Rotation** node. Connect the output of the **Get Actor Rotation** it to the **Target Relative Rotation** node.

https://user-images.githubusercontent.com/5504953/128609875-8979cd30-77ea-4438-a33e-42ca8c8dd6e7.mp4

Add comment `Move Component` to the work done in the blueprint.

![alt_text](images/image_87.png)

Now the actors default to being **Static**. This actor **will not** move.  This means that when you build lighting Unreal bakes in the actor's shadows because it will not move it through physics or through code.  We will be moving this platform so lets set **BP_MovingPlatform | Mobility** from **Static** to **Movable**.  Press **Build | Build Lighting Only** to make this change.

![alt_text](images/image_86.png)

Now lets see if it works.  Set a start and end position for the animation.  Then press play.  Move the platform back to close to the start position. Notice that the platform goes right to the end position when you press play.  why?

https://user-images.githubusercontent.com/5504953/128610218-21d9ff0a-4f23-4577-af41-d7e2bb2f2cfe.mp4


Basically we are not resetting the actor to the begining before starting. Also, our **Speed** is set to **0** seconds which would make it go there with no animation.Open up **BP_MovingPlatform** and go to the **Event Graph** tab.  Add a **Get Starting Location** node. Pull off the pin and add a **Set Actor Location** node.  This will reset the actor to the starting postion of the platform.  Add it between the **Event Begin Play** and **Go to Locatiion and Back** nodes.  Add a comment `Set Actor Location Then Call Animation Event`.  Change the default **Speed** variable from **0** to `5`. Press the **Compile** button.

Move the platform away from its start position.  Press the **Play** button and you will see it jump to the start position and move to the end position over 5 seconds.

https://user-images.githubusercontent.com/5504953/128610390-8fcf1ad3-76c3-4198-9b06-18d5d9b92d19.mp4

Lets add the ability to move the platform between the start and end positions so we can test them in game.  Go to **BP_MovingPlatform** and add a **boolean** variable called `bGoToStartPosition` and makes ure it is set to **Private** and **Instance Editable** are both set to true.  Make sure **Category** is set to `Platform`. Add a **Tooltip** `Return to starting position`. Duplicate this variable and call it `bGoToEndPosition` and change the **Tooltip** to 'Return to ending position`.

Go to **Contruction Script** tab and pull from the **False** execution pin of the last **Branch** node. Add another **Branch** node.  Drag a **Get bGoToStartPosition** and drop it on the graph. Plug it into the **Condition** pin in the **Branch** node.  Pull from the **True** execution pin and select **Set Actor Location** node. Drag a **Get Starting Position** node and plug it into the **New Location** pin in the **Set Actor Location**.

Woops we forgot to reset the boolean back to false.  Add a **bGoToStartPosition** and set it to false.  Put it before the **Set Actor Location** event.

Pull off of the exectution pin exit of **Set Actor Location** and select **Set Go to Start Position.  Select all the nodes and add a comment by pressing the **C** key and enter `Move to Starting Position of Platform`.

Repeat the above for going to the end position but with the **Go To End Position** and **Ending Position** nodes. I copied and pasted and changed the variables for the end.

Press **Compile** on the **BP_MovingPlatform** blueprint and go to the editor.  Set the begining and end positions. Now go to both begining and end and you should see the platform go to the beginning and the end. Move the platform away and you should be able to send it back. This way we can tell that if we join two parts of the level that the platform will start and end at the right spot.

https://user-images.githubusercontent.com/5504953/128610999-8d89f913-22cd-4387-bdd2-6dde403dc519.mp4


Select all the nodes that attach to **Move Component** inclusive and copy and paste them.  We will use this copy to return to the starting position from the end position.  Remove the **End Position** node and replace it with a **Get Starting Position** and plug it into the **Target Relative Location**.

Now we want to check to see if we have **Platform is Looping** set to true or not.  If true then we want the platform to go back to the begining and go to the end again.  Drag a copy of **bPlatform Is Looping** and drag off of hte pin and get a **Branch** node. Connect the execution pin from **Move to Component | Completed** that will run when the platform reaches its target to the **Branch** node.

Now we want a potential delay that gives the player time to get onto the platform.  Add a **Delay** node.  Get a **Get Delay** node to the variable we created and plug the output to the **Delay | Duration** pin.  Change the default value of the **Delay** variable to `5.0`.

Plug the output of the **Branch** node to the **Delay** node then onto the second **Move Component To** node which will move it back to the starting position after a delay.

Go to the game window and select the platform.  Make sure **Platform is Looping** is set to `true` and then run the game.  The platform should move to the end postion then back to the start.

https://user-images.githubusercontent.com/5504953/128611053-e9773924-13f8-4602-8f8e-0defe6018979.mp4


Select all the nodes that attach to **Move Component** inclusive and copy and paste them.  We will use this copy to return to the starting position from the end position.  Remove the **End Position** node and replace it with a **Get Starting Position** and plug it into the **Target Relative Location**.

Now we want to check to see if we have **Platform is Looping** set to true or not.  If true then we want the platform to go back to the begining and go to the end again.  Drag a copy of **bPlatform Is Looping** and drag off of the pin and get a **Branch** node. Connect the execution pin from **Move to Component | Completed** that will run when the platform reaches its target to the **Branch** node.

Now we want a potential delay that gives the player time to get onto the platform.  Add a **Delay** node.  Get a **Get Delay** node to the variable we created and plug the output to the **Delay | Duration** pin.  Change the default value of the **Delay** variable to `5.0`.

Plug the output of the **Branch** node to the **Delay** node then onto the second **Move Component To** node which will move it back to the starting position after a delay.

Go to the game window and select the platform.  Make sure **Platform is Looping** is set to `true` and then run the game.  The platform should move to the end postion then back to the start.

https://user-images.githubusercontent.com/5504953/128611591-6c815996-321d-4834-b828-6aad58621d8d.mp4

Now this goes to the end and back once.  We want this to loop endlessly for the entire life of the level.  We do this by adding another delay then calling our own event.  This is a recursive call that will just keep calling itself as long as the level exists.  Copy and paste the **Delay** and **Get Delay** variable nodes and put it after the second **Move Component To**.  Connect the **Completed** to the **Delay** node execution pin. Add a **Go to Location and Back** event node to call oneself. Go to the game and it should loop forever now!

https://user-images.githubusercontent.com/5504953/128611772-5d00eec6-0231-4f86-b93d-cc1469cdd0c5.mp4

Lets save our work by pressing **File | Save All**.  Press the **Source Control | Submit to Source Control** button then enter a message of what you did last.  Press the **Submit** button.  Make sure it is succesful then run **GitHub Desktop**.  Press the **Publish Origin** button.

Now you should have all the components you need to create your own level.  Create p a new level and use what you have learned her to construct a level that you can navigate around.  Take a look at what can be done within a week or so of consistent work.

![save, commit and push to github](images/Github.jpg)

| `level.design`\|`THE END`| 
| :--- |
| **That's All Folks!** Thanks for sticking around. That's it for this lesson. |

___

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Next Title"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../moving-platform/README.md#user-content-moving-platform)| [home](../README.md#user-content-ue4-hello-world) | 
|---|---|
