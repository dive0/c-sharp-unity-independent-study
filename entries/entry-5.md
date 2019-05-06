# Entry 5: Learning About Animation

## Recap
In the previous entry, I talked about the codes I used to create my MVP, which is to control the character using the keyboard and mouse. In this entry, I will talk about what I learned about creating animation in Unity.

## Displaying Model
My partner sent me a sample model that he created using Blender. I tried to figure out how to get the model to show. At first, I read that to make the model from Blender to show, I can just drag the .blend file into the assets folder. However, that wasn't the case. I need to the file to be .fbx, so I downloaded Blender on my own laptop to convert .blend to .fbx.

![alt text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/sample_model.png)

## Code Changes
Since the model was really big compared to the small capsule that I was testing with, I have to change the offset of the camera and also change the degree the camera rotates since the model will cover more than half of the screen if I didn't.

`transform.Rotate(-25, player.position.y, 0); // rotate the camera`

## Useful Links
* [Using The Animation View](https://docs.unity3d.com/Manual/animeditor-UsingAnimationEditor.html)
* [Creating a New Animation Clip](https://docs.unity3d.com/Manual/animeditor-CreatingANewAnimationClip.html)
* [Animating a GameObject](https://docs.unity3d.com/Manual/animeditor-AnimatingAGameObject.html)
* [Tutorials On Animating In Unity](https://unity3d.com/learn/tutorials/s/animation)

## Animation View
### Dopesheet Mode
Edit the keys for each frame of the animation

![alt text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/Dopesheet.png)

### Curve View Mode
Edit the property that can be animated at different frame

![alt text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/curve.png)

## Clips To Play
This window will show the animations that will be played when "run" is clicked. I will make this so that when the controls for the movements are clicked, the animation for moving the character will play. When nothing is clicked, the character will stay still.

![Clips](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/clips.png)

## Model Display
The model needs to be in a T-pose in order for Unity to accurately see the model's bone and determine it as a humanoid. My model was not in a T-pose, so there are bones not found by Unity and the ones found were not the actual position of the bone. For example, the right hand was set as the right foot.

![bones](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/bones.png)

## Takeaways
* **Know What To Research!!!** It is important to research the components that can help you understand what you need to do. For me, that is the animation view. I know for a fact that I won't be able to create animation on Unity without it. By knowing what is necessary, you can use more of your time understanding how to use it. This way, you may not have to understand something else that you may never need to use.
* **Learning is a never-ending process** It is not a bad idea to learn something new after you completing something. I finished with the controls of my characters and I decided to also learn about animation since the characters need to look like they are moving. There is always something deeper to learn after you learned one thing.

[Back](entry-4.md) | [Next](entry-6.md) <br><br>
[Table of Contents](../README.md)
