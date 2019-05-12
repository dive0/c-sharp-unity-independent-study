# Entry 6: Animation And Adding NPCs

## Recap
In the previous entry, I talked about what I learned about creating animations for my character. In this entry, I will talk about the animations I creating and adding NPCs to the game by downloading models from the asset store.

## Character Animation
The model that my partner sent me can't be animated since the limbs will not move. I downloaded a robot model for me to test how to animate. I animated the robot's right leg incorrected, so it looks weird.

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
My partner created a music for the game and I need to know how to play the music when the game start. To play the music, there should be an Audio `gameObject` that allows the music to be played. Then, the `AudioClip` need to be set as the music file.

![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/move.gif)

[Back](entry-5.md) | [Next](entry-7.md) <br><br>
[Table of Contents](../README.md)
