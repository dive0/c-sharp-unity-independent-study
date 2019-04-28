# Entry 4: MVP

## Recap
In the previous entry, I talked about the codes I learned and used to make the characters (player and NPCs) move. In this entry, I will talk about the changes I made to the movements for the player and added controls using the mouse.

## Trial Code
### Trying to rotate the camera player using the mouse
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class CameraMouseMove : MonoBehaviour
{
    Vector2 mouseLook; //faces the mouse 
    Vector2 smoothV; //smooth the movement of mouse
    public float sensitivity = 3; //sensitivity of mouse
    public float smoothing = 2.0f; //speed of the smoothing speed

    public GameObject player; //get player
 
    void Update()
    {

        var md = new Vector2(Input.GetAxisRaw("Mouse X")*4.0f, Input.GetAxisRaw("Mouse Y")); //control the camera using mouse

        //turning the mouse with certain speed
        md = Vector2.Scale(md, new Vector2(sensitivity * smoothing, sensitivity * smoothing));
        smoothV.x = Mathf.Lerp(smoothV.x, md.x, 1f / smoothing);
        smoothV.y = Mathf.Lerp(smoothV.y, md.y, 1f / smoothing);
        mouseLook += smoothV;

        //moving the player and camera
        transform.localRotation = Quaternion.AngleAxis(-mouseLook.y, Vector3.right);
        transform.localRotation = Quaternion.AngleAxis(mouseLook.x, Vector3.up);
        player.transform.localRotation = Quaternion.AngleAxis(mouseLook.x, player.transform.up);

    }
}
```

### Camera follows the player
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class CameraView : MonoBehaviour
{
    public GameObject player; //get player

    private Vector3 offset; //set distance from player

    void Start()
    {
        offset = transform.position - player.transform.position; //distance
    }

    void LateUpdate()
    {
        transform.position = player.transform.position + offset;  //stay at a certain distance from the player
    }
}
```

## Useful Syntax
### Cursor.lockState and CursorLockMode
These are used to lock and unlock the cursor in the center of the screen/game

### Cursor.visible
Shows/hides the cursor

### AddForce and ForceMode.Impulse
These are used to add force to the direction of the vector and rigid body

### Input.GetAxis
This will return the virtual axis of my mouse

### Quaternion.AngleAxis
Rotates a certain degree around the axis

## Player Movements
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

[RequireComponent(typeof(Rigidbody))] //allow the use of physics
public class CharacterControl : MonoBehaviour
{
    public int ShowCursor = 0; //set showing cursor to false
    public float speed = 1;
    public Vector3 jump;
    public float jumpForce = 2.0f; //height of jump
    public bool isGrounded; //check if player is on the ground
    private Rigidbody rb; //use physics
    void Start()
    {
        Cursor.lockState = CursorLockMode.Locked; // start without showing cursor and lock the cursor in the center of the screen
        rb = GetComponent<Rigidbody>(); //use physics
        jump = new Vector3(0.0f, 2.0f, 0.0f); //how high to jump
    }

    void OnCollisionStay()
    {
        isGrounded = true; //when touching the ground, the player is on the ground
    }

    void Update()
    {
        //move the player
        float moveInY = Input.GetAxis("Vertical") * 5;
        float moveInX = Input.GetAxis("Horizontal") * 5;
        moveInY *= Time.deltaTime;
        moveInX *= Time.deltaTime;

        transform.Translate(moveInX, 0, moveInY);

        //make player jump by pressing space
        if (Input.GetKeyDown(KeyCode.Space) && isGrounded)
        {
            rb.AddForce(jump * jumpForce, ForceMode.Impulse);
            isGrounded = false;
        }

        //make the cursor disappear and appear. However, when making the cursor disappear again, have to click on the mouse to make it disappear
        if (Input.GetKeyDown(KeyCode.Escape))
        {
            if (ShowCursor == 0)
            {
                Cursor.visible = true;
                Cursor.lockState = CursorLockMode.None;
                ShowCursor++;
            }
            else
            {
                Cursor.visible = false;
                Cursor.lockState = CursorLockMode.Locked;
                ShowCursor = 0;
            }
        }
    }
}
```

## Camera Movements
```
using UnityEngine;
using System.Collections;

public class TransformFollower : MonoBehaviour
{

    public float turnSpeed = 4.0f;
    public Transform player; //allow to move the player

    //distance from the player
    public float height = 1f;
    public float distance = -4f;

    private Vector3 offsetX;
    private Vector3 offsetY;

    void Start()
    {
        //set distance
        offsetX = new Vector3(0, height, distance);
        offsetY = new Vector3(0, 0, distance);
    }

    void LateUpdate()
    {
        player.Rotate(0, Input.GetAxis("Mouse X") * turnSpeed, 0); //rotating the player with mouse

        //rotating around the player using the mouse
        offsetX = Quaternion.AngleAxis(Input.GetAxis("Mouse X") * turnSpeed, Vector3.up) * offsetX;
        offsetY = Quaternion.AngleAxis(Input.GetAxis("Mouse Y") * turnSpeed, Vector3.right) * offsetY;
        transform.position = player.position + offsetX;
        transform.LookAt(player.position);
    }
}
```

## Takeaways
* **Don't just copy tutorials and/or codes other people provide online.** There are many solutions for your problem(s) on the internet. You may be tempted to copy the solutions, but that won't help you learn. You can use it as a reference and learn from it. Also, the solution may not be exactly how you want your project to work. It's better to know how to solve instead of copy.

[Back](entry-3.md) | [Next](entry-5.md) <br><br>
[Table of Contents](../README.md)
