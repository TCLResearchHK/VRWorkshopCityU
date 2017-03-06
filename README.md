# VR Workshop

[![Join the chat at https://gitter.im/TCLResearchHK/VRWorkshop](https://badges.gitter.im/TCLResearchHK/VRWorkshop.svg)](https://gitter.im/TCLResearchHK/VRWorkshop?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

A VR workshop organized for the Department of Media and Communication, City University of Hong Kong.

## Abstract

You will have hands on experience in creating VR applications using different tools. You will create an interior enviroment (read: a small room) twice, first using [Unity](https://unity3d.com/), and then using [A-Frame](https://aframe.io/).

Firstly, you will model the room and furnitures with [Sweet Home 3D](http://www.sweethome3d.com/).

Secondly, you will turn the room model into a desktop application using Unity. The resulting application can be viewed on desktop. We will also demostrate what is needed to be done to make it runs in [HTC Vive](https://www.vive.com/), though due to time and hardware limitation, you will only develop a non-VR version.

Finally, you will create a WebVR web page to display the room model using A-Frame. The resulting page can be visited on desktop browsers in 3D, and, on mobile browsers in VR with the help of [Google Cardboard](https://vr.google.com/cardboard/).

## Preparation

Download and install the softwares as follows:

 * [Unity](https://store.unity.com/download?ref=personal)
   personal edition, version 5.5.x or up.

    * During installation, select 64-bit (32-bit is also fine), choose components including "Unity 5.5.x", "Documentation", "Standard Assets".

    * We don't plan to build native Android / iOS apps, so leave those components as unchecked.
 
 * [Sweet Home 3D](http://www.sweethome3d.com/download.jsp)
   free edition available at SourceForge.net, version 5.4 or up

## Procedures

### 1. Interior 3D modeling

#### 1.1 Open up
Open SweetHome and following the steps below:

#### 1.2 Create a Room
Click “Create room” to create the floor of the room you want to create. 
Then, click “Create wall” and build walls around the floor.

#### 1.3 Set textures and UV map for the walls, floor and ceilings
Select all Walls and Floor-> double click -> Click Display Ceilings -> Choose Texture for the radio button of floor, ceilings and walls, Click the Square box for choosing the texture you want.

#### 1.4 Design your room
Choose different furniture, doors and windows you want from the left menu and Put it to your room, double click the items and choose the texture or color you want. 

#### 1.5 Extra sources
For searching texture online, you can use the link provided by SweetHome (http://www.sweethome3d.com/zh-tw/importTextures.jsp) or you could search the type of texture on google with the word “seamless”, for example, if you want to search leather, you could type in “leather seamless” in search bar, all the texture you find should be in square.

#### 1.6 Export models
3D Vision -> Export to OBJ(All) to one folder.


### 2. Unity application development

#### 2.1 Get a Unity account 
Head to https://id.unity.com/en/conversations/25b5ab91-6398-4ddc-b405-d7147cde2783003f and create your unity account. Or you could click signup when open up Unity. Then Signin to Unity.

#### 2.3 Open a Project
Open a new project, give it a name and click Create Projects.
Window -> layout -> 4split (For comfort display only)
Drag all the files exported from SweetHome to the Hierarchy in Unity 

#### 2.4 Lighting 
Set walls and room to statics
set lighting (Window -> lighting)
Drag Directional light to the source in lighting 
Unclick backed GI
Set Window Glass Materials -> Rendering mode to “Transparent” -> Metallic to 0.8 -> Smoothness to 1 -> Allbedo Alpha around 50%
Add area light for windows

#### 2.5 Components/Effects/Camera Settings
Set collider -> right click in projects -> 3D objects -> Cube -> resizes the size of the cube to the same as the wall
Download “Cinematic effects” from Asset Store -> Click download -> Click import
Delete Main Camera in project
Assets -> import package -> Character
Drag FPSController to Hierarchy
Set character collider -> set Radius and Height to 10
Set walk speed to 300, Stick to ground force to 0, gravity multiplier to 0
Field of view -> ~43, Near -> 10
Check HDR under FPS Controller
Add component under the FPS Controller-> search tone mapping, set color, set exposure
Add component under the FPS Controller -> search anti-aliasing
Set materials (For fine tune)

#### 2.6 Save Scene
Create a "Scene" folder under Hierarchy
File -> Save Scene -> save your scene to scene folder and name it. 

#### 2.7 Project setting and build setting
Edit-> project setting-> player ->Rendering Path chooses “Deferred” -> color space choose “Linear”
File-> Build setting -> Architecture ->x86_64-> Build 
 
#### 2.8 For HTC vive VR Version
Download “SteamVR” from Asset Store->Click download-> Click import
From CameraRig under prefab folder drag to the scene and replace the FPS Controller.
Edit-> project setting->player ->Rendering Path chooses “Forward” 



### 3. WebVR application development

#### 3.1 Get a Github account

Head to https://github.com/, sign up for a free account. It is for hosting the web page we're going to create, such we will have a link for viewing that page and sharing it to friends.

#### 3.2 Create a Github repository

Click the **+** button at the top-right corner to create a new repository. Give it a name (e.g. `vr-room`), check the box labeled "Initialize this repository with a README", click "Create repository".

In the repository page, select the "settings" tab. Scroll down and find the "GitHub Pages" section. In the "Source" dropdown menu, select "master branch" and click "Save". The "GitHub Pages" section should now display something like `Your site is ready to be published at https://andyli.github.io/vr-room/.`.

#### 3.3 Get a Cloud9 account

Create a [Cloud9](https://c9.io/) account. It is an online development platform that includes an editor as well as other development tools (e.g. git).

Note that creating a normal account requires a credit card (no charge, just for varification). We have paid for an [education plan](https://c9.io/pricing), such that via our invitation, you can create an account without providing credit card detail. To get an invitation, send a message to our [workshop chatroom](https://gitter.im/TCLResearchHK/VRWorkshop) providing your email address.

#### 3.4 Create a Cloud9 workspace

[Create a new workspace](https://c9.io/new). Make sure:

 * In the "Team" dropdown menu, select "Don't set a team for this workspace". It is because if you choose our "VR Workshop" team, the workspace could be automatically removed when we terminate our education plan. You should keep your work :)

 * In "Clone from Git or Mercurial URL", enter the GitHub repository url you've just created (e.g. `https://github.com/andyli/vr-room`).
 
 * Choose the HTML5 template.

#### 3.5 Create a WebVR web page

Open the workspace you have just created. In the top menu, select "File" -> "New From Template" -> "HTML file". Save it as "index.html" by selecting "File" -> "Save".

Within `<head>...</head>`, add `<script src="https://aframe.io/releases/0.5.0/aframe.min.js"></script>`.

Within `<body>...</body>`, add the code as follows:
```html
<a-scene>
    <a-sphere position="0 1.25 -5" radius="1.25" color="#EF2D5E"></a-sphere>
    <a-box position="-1 0.5 -3" rotation="0 45 0" width="1" height="1" depth="1" color="#4CC3D9"></a-box>
    <a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="#FFC65D"></a-cylinder>
    <a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="#7BC8A4"></a-plane>
    <a-sky color="#ECECEC"></a-sky>
</a-scene>
```

You can now preview the web page by selecting "Preview" -> "Live Preview File (index.html)". You may use the [A-Frame Inspector](https://aframe.io/docs/0.5.0/guides/using-the-aframe-inspector.html) (<kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>i</kbd>) to navigate and play with different settings.

#### 3.6 Import the interior model

First of all, upload files by "File" -> "Upload Local Files...", or simply drag-and-drop the files from file explorer to the Cloud9 workspace file panel.

Then, convert the .obj file exported from Sweet Home 3D to another format (.dae) first, because A-Frame does not fully support the .obj file exported by Sweet Home 3D. To do so, use a command line program, [assimp](http://www.assimp.org/). In the bottom "bash" termainal panel, input the commands as follows:
``` bash
sudo apt-get update
sudo apt-get install assimp-utils
assimp export interior.obj interior.dae
```
Remember to replace `interior.obj` with the file name of your model.

Replace the primitive shapes to our room model by using the [`<a-collada-model>`](https://aframe.io/docs/0.5.0/primitives/a-collada-model.html) entity.

#### 3.7 Publish the web page

In the bottom "bash" termainal panel, input the commands as follows:
``` bash
git add --all
git commit -m "update web site"
git push
```

The files in the Cloud9 workspace will be synchronized to your GitHub repository. You can now use the GitHub Pages link created in the earlier step to view the web page.
