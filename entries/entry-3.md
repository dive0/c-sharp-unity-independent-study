Entry 3: Creating Movements

# Recap
In the previous entry, I talked about the codes that I may need to use in order to control my character. This entry, I will talk about the codes I use to actually move my character and other movements that may be used in the game.

# Moving character
This part is the code that I need to move my character, controlled by  gravity.
```
using System.Collections;
using UnityEngine;

public class Movement : MonoBehaviour
{
    public float speed;

    private Rigidbody rb;

    void Start()
    {
        rb = GetComponent<Rigidbody>();
    }

    void FixedUpdate()
    {
        float horizontalMovement = Input.GetAxis("Horizontal");
        float verticalMovement = Input.GetAxis("Vertical");

        Vector3 movement = new Vector3(horizontalMovement, 0.0f, verticalMovement);

        rb.AddForce(movement * speed);
    }
}
```

# Moving the camera
This part is the code that moves the camera. The camera will follow the character where ever it goes.
```
```

# Takwaways
* **Create sample codes** I can be helpful to create a sample of what you are trying to create since you are about to have an idea of how you want to create your product. You can test with the sample and make different changes to make it similar to the actual product. Then, you can use the sample to be put in the product and make tweaks.
* **Comment your code** Commenting your code helps remind you of what that piece of code is about. You may understand the code at the moment, but when you want to go back and make changes, you may forget what the code is. Commenting can also help you better understand your code since you are explaining what the code does.

[Back](entry-2.md) | [Next](entry-4.md) <br><br>
[Table of Contents](../README.md)
