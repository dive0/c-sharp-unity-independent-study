# Entry 6: Animation And Adding NPCs

## Recap
In the previous entry, I talked about what I learned about creating animations for my character. In this entry, I will talk about the animations I created and adding NPCs to the game by downloading models from the asset store.

## Character Animation
The model that my partner sent me can't be animated since the limbs will not move. I downloaded a robot model for me to test how to animate. I animated the robot's right leg incorrectly, so it looks weird. 

When I get the actual character model from my partner, I will be able to have a clear idea of how I want to animate it.

![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/character_animation.gif)
![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/Animate_character.png)

## NPCs
These are the models that will be walking/flying around the map. The animations came with the models, so I used the one provided.

![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/troll.gif)
![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/lancer.gif)
![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/Demon.gif)
![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/boar.gif)
![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/dragon.gif)
![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/angel.gif)

## Moving Around The Map

![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/move.gif)

## Make The Animation Slower
The animation for the lancer was too fast, so I need to make it slow down.

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Slower : MonoBehaviour
{

    public Animator anim;

    void Start()
    {
        anim = gameObject.GetComponent<Animator>(); // get the animator gameObject
    }

    void Update()
    {
        anim.speed = 0.5f; // slow the speed the animation is played
    }
}
```

## Putting Music
My partner created music for the game and I need to know how to play the music when the game start. To play the music, there should be an Audio `gameObject` that allows the music to be played. Then, the `AudioClip` need to be set to the music file.

![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/audio_source.png)

## Models Credits
* [Robot](https://assetstore.unity.com/packages/3d/characters/robots/space-robot-kyle-4696)
* [Lancer](https://assetstore.unity.com/packages/3d/characters/monster-lowploygon-mobile-lancer-140601)
* [Troll](https://assetstore.unity.com/packages/3d/characters/humanoids/troll-giant-122206)
* [Demon](https://assetstore.unity.com/packages/3d/characters/humanoids/demon-blade-lord-140993)
* [Boar and Dragon](https://assetstore.unity.com/packages/3d/characters/creatures/dragon-the-terror-bringer-and-dragon-boar-77121)
* [Fallen Angel](https://assetstore.unity.com/packages/3d/characters/humanoids/fallen-angel-pack-125164)

## Takeaways
* **Give Credits** If you are using someone else's creation, remember to give them credit.
* **Use Samples** If you are working in partnership, don't just wait for your partner to get their part done so that you can continue to the next step. You can use a sample that helps you become familiar with what you will be doing next before getting your partner's part of the project.

[Back](entry-5.md) | [Next](entry-7.md) <br><br>
[Table of Contents](../README.md)
