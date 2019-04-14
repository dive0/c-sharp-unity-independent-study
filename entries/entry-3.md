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
