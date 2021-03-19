# Create Your Own Track
This guide will explain to you how to create your own track.

## Create a new scene
1) Go to the "Assets/Scenes/".
2) Right click in there, select "Create > Scene".
3) Rename the scene to whatever you want your track to be named.
4) Double click on the scene to open it.
5) you can delete everything in the scene from the Hierarchy tab.

## Add your scene to the Build Settings window
1) To open the Build Settings window, press: CTRL+SHIFT+b
2) select now "Add Open Scenes", it should add a your new scene to the scene list
3) you can now close this window and continue

your build settings should look like that: <br>
<img src="../assets/create_a_track/build_settings.png" height="512">

## Apply the scene prefab
1) In "Assets/Prefabs/" you will find a Prefab called "ScenePrefab".
2) Drag and drop this prefab into the Hierarchy tab of your new scene, you should see the prefab appear.
3) Right click on the prefab and select "Unpack Prefab", this will disociate the object in your scene from the Prefab stored in "Assets/Scenes/".

you should be then leaved with something that looks like that: <br>
<img src="../assets/create_a_track/scene_prefab.png" height="512">


### Quick explanation on the ScenePrefab
This prefab contains everything you need to "donkeyfie" the scene, <br>
it contains some controllers to modify the look of the generated road, the starting line location, etc... <br>
But what will interest you the most here is in "ScenePrefab/world/", in there you will find everything that is related to the scene looking.

## Add your new scene to the menu !
Before adding some fancy textures and add some objects to your scene, I recommend adding your scene to the menu; this could be done at any moment of the scene creation process. <br>

1) So now lets load the "menu" Scene located in "Assets/Scenes/", double click on it
2) Click on the "_TcpMenuController" object in the Hierarchy tab
3) In the Inspector tab,, look at the "Tcp Menu Handler" script, click on the "Scene_names" component to develop it.
4) Enlarge the list by 1 element and add the name of your scene in the last element of the list

From there, you are all set to continue develpping your scene. <br>
Note: you can also click the run button in the menu scene to see how the menu looks, you can also try to click on the button to see if it's redirecting you well to your new scene. It should look like this: <br>
<img src="../assets/create_a_track/menu.png" height="512">

If you are wondering how does the buttons are created at runtime, go see the [menu buttons documentation](../advanced/menu_buttons.md)

For this part, you have two main choices, <br>
you can either choose to use an existing GameObject (mesh) or you can use the RoadBuilder to generate a track at runtime.
* ### Use an existing Prefab/object
    in that case, just drag and drop your object into the scene, maybe apply a texture or two and the job is done

* ### Using track measurements / SVG file
1. If you are creating a relatively smaller scale track that is measurable, it is possible to create an SVG (scalable vector graphic) of the track and maintain dimensions as you scale the image up. Make sure to take note of the resolution and keep the image ratio the same when importing onto the plane in Unity. 
2. To figure out the exact scaled size the track should be, a method is to create a 3D-Object cube. The Donkeycar itself is approximately 25 cm lengthwise, so the cube can be used as a unit of measurement. In most cases, a 1x1x1 cube / rectangular prism will be approximately 10cm in each dimension. You can scale up the prism to a known size, such as the edge-to-edge track width <insert image here of cubwe thing>.  

* ### Using the RoadBuilder (track generation at runtime)
1.  Create a new "Empty" GameObject with component "Path Creator." 
2. If track is flat, select "Top-Down" (x,z is the horizontal plane in Unity), under the space tab. If it is 3-D, it is recommended to adjust for heights later on. 
3. For visibility, under display options, select "constant point size" to see anchor points more clearly. Adjust the anchor and control nodes (red and blue dots) to align with the center of the track, shift+click will create a new anchor, alt+click will delete an anchor. If the track is a loop, you can select "closed path" to connect the first and last nodes together. 
4. Under the "controllers" hierarchy, select PathManager and link the your created path in the PathCreator section. Check the "Do load game object path" box and press play. 




You can have a look at the [PathManager script](../advanced/path_manager.md).

## Add some objects, textures and else
you can add whatever you want to the scene to make it look as you wish. <br>
Ideally, the scene size shouldn't exceed 20Mb, the lower the best !

* ### Generating Assets 
An asset is any object in a scene, it can make it more lifelike or adds 'reality' to the mix.  It is possible to generate assets around the track using the "RandAssetChallenge" under challenges. The script randomly generates your selected assets around a specified range. 
