![](../images/line3.png)

### Setting up Unreal & Github

<sub>[home](../README.md#user-content-ue4-intro-to-level-design) • [next](../camera-mechanics/README.md#user-content-lock-cameras-and-mechanics)</sub>

![](../images/line3.png)

We will be using Unreal's third person template as a starting point for our 3-D platforming game we will be using for level design.  This will give us all we need for a basic character that we can control with some tweaks to make it to our liking.  Lets start by creating a project in Unreal then using **Perforce** to store our work.

<br>

---


##### `Step 1.`\|`UE5LD`|:small_blue_diamond:

If you have not installed the required software go and add [Epic Games Launcher](https://www.epicgames.com/store/en-US/download), [P4V](https://www.perforce.com/downloads/helix-visual-client-p4v) - this assumes you have a **Perforce** server which is free if you are team of 4 people or less and can be found at [Perforce Helix Core](https://www.perforce.com/products/helix-core/free-version-control).  Make sure it has a `5.0.x` in front of the version so that we know this walk through will be compatible with your version of Unreal. 

If it is not installed press the <kbd>+</kbd> button and install the latest **5.0.x** version of Unreal.  

![screenshot of epic game launcher](images/image_01.png)

![](../images/line2.png)

##### `Step 2.`\|`UE5LD`|:small_blue_diamond: :small_blue_diamond: 
Run the **Epic Games Launcher** and Press **Launch** button to launch the editor.

![button to launch UE4](images/LaunchUnrealEditor.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5LD`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

You can pick from different starting templates with Games, Film/Video & Live Events, Architecture and Automotive Product Design & Manufacturing as options.  You can also load recent projects as well!

We are going to make a game so lets start by selecting **Games** and then select the **Third Person Template**.  

The first settings on the top right is set to **BLUEPRINT**.  You can select between **C++** and **BLUEPRINT**.  Since we will not be doing any C++ programming in this exercise we will leave it with Blueprint.  I am leaving the **Target Platform** as **Desktop** and the **Quality Preset** to **Maximum Quality** as we are developing this for a modern computer.  We do not need the starter content so we will set the **Starter Content** to `false` to keep our project size at bay. We will leave **Raytracing** off as we will not be using it at the moment.  

Select your **Perforce** workspace as the folder to save the project in and call it `IntroToLevelDesign`.  Press the <kbd>Create</kbd> button to start the game with the third person template.

![Unreal Select or Create New Project screen](images/image_03.png)

![](../images/line2.png)

| `version.control`\|`Introduction To Level Design`| 
| :--- |
| :floppy_disk: &nbsp;&nbsp;Version control saves lots of space on our laptops so that all project data can be safely backed up and saved on the server but we only need the assets we are currently using on our local hard drive.  It is also good practice as most game projects use some form of version control. It is absolutely necessary on team projects.  In this case we will be using **Perforce's Helix Core** server. |

![](../images/line2.png)

##### `Step 4.`\|`UE5LD`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

In the editor select the **Edit** menu item then from the drop down menu select **Editor Preferences**. Select **General | Loading & Saving** tab from the left hand side.  Go to *Source Control* and set **Prompt for Checkout on Asset Modification** and **Add New Files when Modified** to `true`.  Leave the other two settings with their default

![select third person ue4 template](images/image_17.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5LD`| :small_orange_diamond:


![Unreal Project Settings screen](images/image_05.png)

![](../images/line2.png)



##### `Step 6.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond:



https://user-images.githubusercontent.com/5504953/127741784-aa262ff8-e4be-4973-9bb7-4ce7abbc171b.mp4

![](../images/line2.png)

##### `Step 7.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Make sure you have a GitHub account and that you are logged into it. Click on the GitHub Classroom [Introduction-to-Level-Design-FA21 Link](https://classroom.github.com/a/bV3pgozG). Accept the prompt if it asks you go join the class and you should get to a **Accept the Assignment – Introduction To Level Design-FA21**. Press the <kbd>Accept this assignment</kbd> button.

![alt text](images/AcceptGitHubClassroomInvite.jpg)


![](../images/line2.png)

##### `Step 8.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

You will get a message saying the repository is geing setup.  Refresh/Reload your web browser as instructed.

![refresh web browser](images/RefreshBrowser.jpg)


![](../images/line2.png)

##### `Step 9.`\|`UE5LD`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Eventually you will get a link for the repository.  Click on this link:

![link to new repository for assignment](images/NewLevelDesignRepository.jpg)

![](../images/line2.png)

##### `Step 10.`\|`UE5LD`| :large_blue_diamond:

Now our server has no files on it. We will be using command line (**Terminal** on the mac Or **Git Bash** on the PC). You can see the commands below.  We are creating a **main** branch and making it our default branch (`-M` switch).  We are then taking the content we **Already Have** in our folder and pushing it to the server.

![empty github repository](images/PushToExistingRepository.jpg)

![](../images/line2.png)

##### `Step 11.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: 

Lets start by copying the link to the clipboard so we can add it to Unreal, and use UE4 to **Initialze** the project.

![Copy repository link](images/CopyRepositoryLink.jpg)

![](../images/line2.png)


##### `Step 12.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Go back to **Unreal Engine** and press the <kbd>Source Control</kbd> button and select the `Connect to Source Control...` dropdown. This brings up the menu to select the source provider (in our game GitHub).

![select github for source control](images/ConnectToSourceControl.jpg)

![select github for source control](images/SelectGitHubForSourceControl.jpg)

![](../images/line2.png)

##### `Step 13.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

In the menu select **Git (beta version)** as the source control you will be using. Paste the directory for your GitHub project into the **Url of the remote server 'origin'** in Unreal.  Then make sure you add a **.gitignore** file, a **README.md** file, a **.gitattributes for Git LFS** file and finally **Make the initial Git Commit** file.  Then press the <kbd>Initialize project with Git</kbd> button and on the next pop up press the **Accept Settings** button. You should see message pop up saying *Connection to source control was successful!*.

![setup github repository](images/SetupGitRepo.jpg)

![press accept settings button](images/AcceptSettings.jpg)

![](../images/line2.png)

##### `Step 14.`\|`UE5LD`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Lets make sure it installed GitHub in our project.  First we need to turn on hidden folders. On the PC follow these [Windows 10 Turn on Hidden Folders](https://support.microsoft.com/en-us/help/4028316/windows-view-hidden-files-and-folders-in-windows-10) directions. On the Mac it is a bit more involved so go and [turn on hidden folders on Mac](https://ianlunn.co.uk/articles/quickly-showhide-hidden-files-mac-os-x-mavericks). You should now see a `.git` hidden folder in the root directory of the project, if you do – you succesfully created a GitHub repo and connected it to the server.

![turn on hidden folders and confirm .git](images/ConfirmDotGitLoder.jpg)

![](../images/line2.png)

##### `Step 15.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: 

Now we are going to use the **Command Line** tools just once.  On a **PC**, right click and run [Git Bash](https://www.windowscentral.com/how-launch-bash-shell-right-click-context-menu-windows-10).  This should have been installed with **Git** when you installed it above.  On a mac, it is a little more involved as you will see by this [website description](https://www.groovypost.com/howto/open-command-window-terminal-window-specific-folder-windows-mac-linux/).  The trick is to navigate to your working Directory (typically `Documents | Unreal Projects | Our First Project`).

![open up terminal or bash](images/OpenUpTerminal.jpg)



![](../images/line2.png)

##### `Step 16.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Type in:

```
git branch -M main
```
in either **Terminal** or **Git Bash**.  This will create a new **Default** branch called `Main`.

![create a main default branch](images/GitBranchMain.jpg)

![](../images/line2.png)

##### `Step 17.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Now lets switch to the **Main** branch by typing

```
git checkout main
```

Now lets take all the work we have done to date on our computer and **Push** it to the server.  This will ensure that all the files are safely stored on the server. It will take a while then you should get a message confirming the branch creation and the push.

```
git push -u origin main
```

![checkout main branch and push](images/GitCheckoutPush.jpg)

![git confirmation message](images/GitConfirm.jpg)


![](../images/line2.png)

##### `Step 18.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to **GitHub** on the web and refesh your browser.  If you did the above correctly you should now see all the folders on **GitHub**:

![all files now on github](images/FirstGitHubPush.jpg)

![](../images/line2.png)

##### `Step 19.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Now I tried doing the above step in **GitHub Desktop** but got some errors.  So now we need to link it to **GitHub Desktop** as we can use this moving forward to push data to the server.  Open up **GitHub Desktop** and select `File | Add local repository`.  Select the <kbd>Choose</kbd> button.

![add repository to github desktop](images/AddRepositoryToGithubDesktop.jpg)

![](../images/line2.png)

##### `Step 20.`\|`UE5LD`| :large_blue_diamond: :large_blue_diamond:

Locate the root folder of your project.  This is the folder that contains the `.git` folder.  This is the top most folder of your Unreal project. In my case it is in the `Documents | Unreal Projects | OurFirstProject` folder.  Press the <kbd>Select Folder</kbd> button.

![find root of project](images/FindRootOfProject.jpg)

![](../images/line2.png)

##### `Step 21.`\|`UE5LD`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Press the <kbd>Add Repository</kbd> button to select this project. Then press the <kbd>Fetch origin</kbd> button to make sure that the permissions all work. 

You will get a pop up asking to **Initialize Git LFS** you will press the <kbd>Initialize Git LFS</kbd> button.

You should now see the message `Last feteched just now`. This means that we are ready to go. 

![add repository](images/AddRepository.jpg)

![initialize git lfs](images/InitializeGitLFS.jpg)


![](../images/line2.png)

##### `Step 22.`\|`UE5LD`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Edit the **README.md** file on GitHub and enter your name as the author and a brief description of the project.  I added `Level design for third person adventure game`.

![enter name and project description in readme.md file](images/image_19.png)

![](../images/line2.png)

##### `Step 23.`\|`UE5LD`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go to **GitHub** and press the **Add file** button and select **Create new file**. Type in `LICENSE`.  A button pops up on the right and press **Choose a license template**. I recommend the **MIT License**. Then you press **Review and submit**. Go back to the main page and select **Compare and pull request**. Press the **Create pull request** button. Select **Merge pull request** and go back to the main page.  The `LICENSE` file should now show up. Now this is on the server so lets bring it onto our laptop.  Go to **GitHub** deskto and press **Fetch Origin** to get the latest.

https://user-images.githubusercontent.com/5504953/127746302-3c6ce54d-0905-4a1d-9273-c9bacabba65c.mp4

![](../images/line2.png)

##### `Step 24.`\|`UE5LD`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Download a thumbnail that you can use on this project [Intro Thumbnail](images/IntroToLevelDesign.png). Press the **Settings** button and select **Project Settings**.  Make sure you are in the **Project Description** tab and press the three dots in the **About** tab next to the thumbnail and attach the thumbnail you just downloaded. Enter a **Description**, **Project Name**.  Put your name as the **Publisher | Company Name** and you can add your email in **Support Contact**. Add the **Project Displayed Title** and **Project Debug Title Info**.

Go back to the game screen, press **Source Control** add a message and press submit.  Open up **GitHub** desktop and push to the server.

https://user-images.githubusercontent.com/5504953/127775522-662de1a2-997c-4bbe-ae35-beb582a67cd1.mp4

![](../images/line2.png)


##### `Step 25.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: 

Press play and lets see what we get? Run around using the **UP | DOWN | LEFT | RIGHT** keys on the keyboard. Press **Space Bar** to jump.  Get used to teh controls - we will make some changes in the next section.

https://user-images.githubusercontent.com/5504953/127747095-54362efe-c04c-4607-8cbc-e1adf34156e8.mp4

![](../images/line2.png)

##### `Step 26.`\|`UE5LD`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: 

OK, that is a good start for now.  Lets save and upload our progress to GitHub.  Open up **GitHub Desktop** and add a **Commit** message.  Press the <kbd>Commit to main</kbd> button. All you need to do to get it to the server is the press the <kbd>Push origin</kbd> button.

![commit changes to main](images/CommitToMain.jpg)

![push to origin](images/PushOrigin.jpg)

![](../images/line.png)

![next up lock camera and mechanics](images/banner.png)

![](../images/line.png)

| [home](../README.md#user-content-ue4-intro-to-level-design) | [next](../camera-mechanics/README.md#user-content-lock-cameras-and-mechanics)|
|---|---|
