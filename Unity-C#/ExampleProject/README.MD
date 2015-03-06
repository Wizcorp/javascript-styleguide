#Preamble 
Most of this project structure was taken directly from the document training drafted by Almir.  I will be updating this readme with decisions made around this folder structure and why.


#Basic Folder Structure

##Components
Holds global helpers such as NavTree, SoundManager, GameSettings.

##Editor
Unity editor folder see:
http://docs.unity3d.com/Manual/SpecialFolders.html

##Libraries
Third party libraries such as Mage, Singleton, XOR128

##Modules
Mage frontend modules

##Resources
Unity resources folder see:
http://docs.unity3d.com/Manual/SpecialFolders.html

##Scenes
Contains scenes view which are not limited to .Unity files but also contain any code that goes with that scene.  The game model will come under the folder Game

##Content
This folder is for most of the Assets, Resources folder should be used sparingly and it makes a clear definition between assets on the game scene and assets for the menus.