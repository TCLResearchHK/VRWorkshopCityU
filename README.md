# VR Workshop

[![Join the chat at https://gitter.im/TCLResearchHK/VRWorkshop](https://badges.gitter.im/TCLResearchHK/VRWorkshop.svg)](https://gitter.im/TCLResearchHK/VRWorkshop?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

A VR workshop organized for the Department of Media and Communication, City University of Hong Kong.

## Abstract

You will have hands on experience in creating VR applications using different tools. You will create an interior enviroment (read: a small room) twice, first using [Unity](https://unity3d.com/), and then using [A-Frame](https://aframe.io/).

Firstly, you will model the room with [Sweet Home 3D](http://www.sweethome3d.com/). [Blender](https://www.blender.org/download/) will be used for modifying the 3D models.

Secondly, you will turn the room model into a desktop application using Unity. The resulting application can be viewed on desktop. We will also demostrate what is needed to be done to make it runs in [HTC Vive](https://www.vive.com/), though due to time and hardware limitation, you will only develop a non-VR version.

Finally, you will create a WebVR web page to display the room model using A-Frame. The resulting page can be visited on desktop browsers in 3D, and, on mobile browsers in VR with the help of [Google Cardboard](https://vr.google.com/cardboard/).

## Preparation

Download and install the softwares as follows:

 * [Unity](https://store.unity.com/download?ref=personal)
   personal edition, version 5.5.x or up.

    * During installation, select 64-bit (32-bit is also fine), choose components including "Unity 5.5.x", "Documentation", "Standard Assets".

    * We don't plan to build native Android / iOS apps, so leave those components as unchecked.
    

 * [Blender](https://www.blender.org/download/)
   version 2.78 or up, 64bit or 32bit
 
 * [Sweet Home 3D](http://www.sweethome3d.com/download.jsp)
   free edition available at SourceForge.net, version 5.4 or up

## Procedures

### 1. Interior 3D modeling

### 2. Unity application development

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

You can now preview the web page by selecting "Preview" -> "Live Preview File (index.html)".

Now modify the code to load the interior 3D model indstead of displaying the premitive shapes. Tips:

 * Upload files by "File" -> "Upload Local Files...".

 * Use [`<a-obj-model>`](https://aframe.io/docs/0.5.0/primitives/a-obj-model.html) and [`<a-collada-model>`](https://aframe.io/docs/0.5.0/primitives/a-collada-model.html).
 
 * Use the [A-Frame Inspector](https://aframe.io/docs/0.5.0/guides/using-the-aframe-inspector.html) to navigate and play with different settings.

#### 3.6 Publish the web page

In the bottom "bash" termainal panel, input the commands as follows:
``` bash
git add --all
git commit -m "update web site"
git push
```

The files in the Cloud9 workspace will be synchronized to your GitHub repository. You can now use the GitHub Pages link created in the earlier step to view the web page.
