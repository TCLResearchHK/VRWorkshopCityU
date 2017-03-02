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

#### 3.3 Get a Cloud9 account

Create a [Cloud9](https://c9.io/) account. It is an online development platform that includes an editor as well as other development tools (e.g. git).

Note that creating a normal account requires a credit card (no charge, just for varification). We have paid for an [education plan](https://c9.io/pricing), such that via our invitation, you can create an account without providing credit card detail. To get an invitation, send a message to our [workshop chatroom](https://gitter.im/TCLResearchHK/VRWorkshop) providing your email address.

#### 3.4 Create a Cloud9 workspace

[Create a new workspace](https://c9.io/new). Make sure:

 * In the "Team" dropdown menu, select "Don't set a team for this workspace". It is because if you choose our "VR Workshop" team, the workspace could be automatically removed when we terminate our education plan. You should keep your work :)

 * In "Clone from Git or Mercurial URL", enter the GitHub repository url you've just created (e.g. `https://github.com/andyli/vr-room`).
 
 * Choose the HTML5 template.

...
