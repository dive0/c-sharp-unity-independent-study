# Entry 8: Adding UI And Texturing The Mountain

## Recap
In the previous entry, I talked about the animation I created for the model my partner created and the demo of the game. In this entry, I will talk about the UI my partner made adding in the texture that I wasn't able to before.

## Adding UI
My partner created 2 scenes that contains the UI for the start menu and the pause menu. 

### Start Menu
I would make the game start when the Start button is clicked.

![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/Start_Menu.gif)

### Pause Menu
The game will pause when the escape key is pressed. The player and the NPCs will not be able to move. The Resume button will continue the game and the Quit button will return to the start menu.

![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/Pause_Menu.gif)

### Changing Scene
#### Script for changing scene:
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ChangeScene : MonoBehaviour
{
    //Load the scene specified
    public void change(string scenename)
    {
        Application.LoadLevel(scenename);
    }
}
```

#### Specify Which Scene To Load
##### For Resume Button:
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class PanelToggle : MonoBehaviour
{
    public GameObject Panel;
    public int shown = 0;

    public void Start()
    {
        Panel.gameObject.SetActive(false);
        Time.timeScale = 1;
        Cursor.lockState = CursorLockMode.Locked;
    }
    public void Update()
    {
        if (Input.GetKeyDown(KeyCode.Escape))
        {
            if (shown == 0)
            {
                Panel.gameObject.SetActive(true);
                shown = 1;
            }
            else if (shown == 1)
            {
                Panel.gameObject.SetActive(false);
                shown = 0;
            }
        }
    }
}
```

`Start()` will run when Resume is pressed. <br><br>
![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/Resume_Button.png)

##### For Start Button
Load the Gameplay scene <br><br>
![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/Start_Button.png)

##### For Quit Button
Load the Main scene (Start Menu) <br><br>
![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/Quit_Button.png)

## Adding Texture
At first I wasn't able to find out how to add in the texture for the mountain becuase there are multiple texture on it. This week, I found out that I can have the texture as a UV map, which has all the texture in one image file. I told my partner to get me the UV map using Blender and I imported the UV map onto the model.
 
To put the UV map on the model, the material's shader have to be in diffuse.

![text](https://github.com/dive0/c-sharp-unity-independent-study/blob/master/images/Material.png)

I have to make sure that the material with the UV map is a component of the mountain in order for the texture to appear. Even though the texture did appear, the resolution is just really low. I tried increasing the resolution and the image size, nothing changes. I decide to just leave it.

## Takeaways
* **There's always a way to fix a problem** At first, I though there's no way to put the texures on the mountain since only one material works on the model. However, by doing more research, I found out about UV map and was able to put the texture on the mountain. Fixing a problem can be hard, but by trying to research more on the problem, a solution may appear. As long as there's a problem, there's a solution.

[Back](entry-7.md) | [Next](entry-9.md) <br><br>
[Table of Contents](../README.md)
