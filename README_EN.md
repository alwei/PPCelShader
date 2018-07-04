Unreal Engine 4 Postprocess cell shader
=======================================================
Supported Ver. UE 4.19.2


Description
------
The post process based cell shader implementation UE4.

Compared with existing post process based cell shaders, here are notable features of this cell shader.


1.Focusing only on cell shading. (Pursued cell like visual)

2.Almost no features out of the focus.

3.Flexible 4 types of outline rendering.

4.Adjustable with UE4 standard lights (Reflects light colors properly)

5.Customizable shadow color and hightlight color.

6.Automatically exclude Unlit material and meshes in distance from the target of this shader.

7.The switch to apply this shader only to target meshes with Custom Depth setting.

8.Diffusion filter shader as an option.

9.Apply ambient light of Skylight an option.

As above, this shader has enough features as a cell shader.

In addition, it is very easy for everyone to install and works out of the box.


Basic usage
------------------
Apply "PPI_CelShader" as a Post Process Material.

https://docs.unrealengine.com/en-US/Engine/Rendering/PostProcessEffects/PostProcessMaterials

"PPI_CelShader" exposes various parameters. So please adjust as you want.
All parameters have pop-up help.
Please apply "PPI_Diffusion" if you want.

By opening the level with this shader applied, you can confirm the result.


Adjustments for characters
--------------------
For the material used by Characters and Actors, this shader uses "specular" to detect highlights.

By using texture maps with specular value for highlight, you can show the highlights only where you specify.

You can adjust where to show shadow by "emissive color" of the material.

If emissive color is more or equal to 1, this shader will not render shadow on there. Please adjust where to render shadow with texture map.


Outline
------------
There are 4 types of outline render modes.

First, "Depth Line" and "Normal Line" renders the outline in the same way regardless the distance between the mesh and the camera.

As a result, these modes can't adjust rendering precisely but the line rendering is more stable.

"Edge Line" and "Crease Line" heavily depends on the distance between the mesh and the camera. But they have more adjustment options those aren't available for "Depth Line" and "Normal Line".

You can omit some parameters if you don't need. Please adjust as you want.


Restriction and warning
--------------
Since this shader is implemented by post processing, there are more restrictions than the shaders applied to individual targets.

1.Can't use different shadow colors and highlight colors for different targets.

2.Can't detect objects with low brightness. Lights in the scene should have appropriate brightness.

3.Can't detect transparent objects such as smoke. Those must be created as opaque objects.

4.This shader uses G-Buffer in post process. So this isn't compatible with forward rendering for mobile devices, etc...

5.This shader doesn't consider optimizations for games.


Known issues
-----------------
・When you use this shader on Mac, it crashes at custom nodes in "PP_Diffusion". Please remove the nodes for now.

・When you use subsurface color, the color isn't reflected. Shading model is not applied in Subsurface Profile.Subsurface, Preintegreted Skin will be applied.


License
-------------------------
Published under the public domain.

https://github.com/alwei/PPCelShader/blob/master/LICENSE


Contact
------------------
Twitter : @aizen76

mail : altaizen76@gmail.com