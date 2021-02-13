
# ![Hidden Histories Logo](/images/hiddenhistories-logo.png) Hidden Histories 
<< Need an overview? Go to the [Hidden Histories Artist Documentation Overview](http://hiddenhistoriesjtown.org/documentation).

Or puzzled by the lingo? See the [Glossary of Terms >>>](https://github.com/Hidden-Histories/Public-Resources/blob/master/documentation/ARpoiseGlossary.md#-hidden-histories-artists).

.

# Tutorial: Creating Sub-Layers

## Overview
This tutorial tells you how to use sub-layers to create more complex POIs in **ARpoise** or **AR-vos**.

- The POIs in the sub-layer inherit the same properties (scale, GPS or Relative position, animations etc.) of the POI from which they are referenced.

- Especially in image trigger and SLAM layers, in which only one POI can be triggered by a image or placed in SLAM at one time, sub-layers allow you to create much more complex augments. 



## Example SlamBoxes: one tap places all these boxes

If we look at the layer example **SlamBoxes** of the [Using the AR-vos app tutorial](UsingAR-vosApp.md#slam-example), one tap will place a yellow center box surrounded by four other boxes. The central yellow cube seems to be static, whereas all the other boxes have various animations. 

BUT if you click the yellow BellCube, all the cubes start rotating around, with the yellow BellCube at the origin. Since the other 4 cubes also have their own animations, it seems that the boxes have a very complex behavior.

![AR-vosSLAMBoxes1x_horiz512h](/documentation/images/AR-vosSLAMBoxes1x_horiz512h.png)

. 

## SlamBoxes: layer definition

If we look at the porPOIse definition of the layer Example SlamBoxes, it contains only a single POI, called **BellCube.** This is just the single yellow box that is at the center.

![SubLayers-DefaultSLAMBoxes_LayerDefinition](/documentation/images/SubLayers-DefaultSLAMBoxes_LayerDefinition.png)

. 

## SlamBoxes: POI BellCube

In the POI BellCube definition, the **Layer name** references a sub-layer **Slam-Example.** 
- The single, central POI **BellCube** has a rotate animation when clicked (and also a bell sound). 
- As this POI references the sub-layer **Slam-Example,** this sub-layer is shown whenever the parent POI **BellCube** appears.
- When you click the parent POI **BellCube,** the sub-layer **Slam-Example** is rotated along with it. Remember that they still keep their individual animations as well!

![SubLayers-DefaultSLAMBoxes_PoiDefinition](/documentation/images/SubLayers-DefaultSLAMBoxes_PoiDefinition.png)

. 

## Sub-Layer "Slam-Example"

The sub-layer Slam-Example doesn't look much different from a normal layer, although we didn't bother to give it a Layer title (since that won't show up anywhere), and the the refresh rate is set to 0 (so it will have the same refresh rate as the main layer). 

It contains the four cube POIs that will appear surrounding the main layer's yellow BellCube POI. 

![SubLayers-SubLayerDefinition](/documentation/images/SubLayers-SubLayerDefinition.png)

. 

## Sub-Layer POI Definition for one of the cube POIs

Each of the POIs in the sublayer is a simple POI, defined as in the example - **and can have an animation of its own, different from that of the parent POI in the main layer.**

**NOTE:**
- The **Lat and Lon** have to be set to **0.**
- The **Relative location (x,y,z)** will be its **offset from the position of the main layer's POI.**
- Remember the sub-layer will also inherit all the other main layer's properties - such as scale, verticle rotation, etc.
- **Leave the URL for trigger image field blank** - this will be inherited from the main layer's POI as well.

## Sub-Layer POI "StripesCube":
![SubLayers-SubLayerPoiDefinition](/documentation/images/SubLayers-SubLayerPOIDefinition.png)

. 

**SO WHAT'S THE BIG DEAL???**
- Say you have an image trigger or SLAM layer. 
- You want to have a lot of POIs, each of which is clickable to produce a completely different animation. In geolocative this would be easy to do - just set up a lot of POIs, each with its own animation.
- For a given trigger image however, you can only have one POI. In SLAM, you can have multiple POIs, but they have to be placed one after another by the user - you can't control where they will be.
- With sub-layers, you can control the position exactly because they are always placed centered at the POI of the parent layer. AND each POI in the sub-layer can have its own event and type of animation.