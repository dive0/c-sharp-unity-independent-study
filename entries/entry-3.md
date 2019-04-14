# Entry 3: Creating Movements

## Recap
In the previous entry, I talked about the codes that I may need to use in order to control my character. This entry, I will talk about the codes I use to actually move my character and other movements that may be used in the game.

## Useful syntax
### transform.eulerAngles
Rotates as Euler Angles in degrees

### StartCoroutine
Completes a function before calling

### yield return
Returns each element one at a time

### WaitForSeconds
Suspends a coroutine for a certain amount of seconds in scaled time

## Moving character
This part is the code that I need to move my character, controlled by  gravity.
```
using UnityEngine;
using System.Collections;

public class Movement : MonoBehaviour
{

    public float speed;
    public GameObject player;

    private Rigidbody rb;

    void Start()
    {
        rb = GetComponent<Rigidbody>(); // control the position through physics simulations
    }

    void FixedUpdate()
    {
        float moveHorizontal = Input.GetAxis("Horizontal");
        float moveVertical = Input.GetAxis("Vertical");

        Vector3 movement = new Vector3(moveHorizontal, 0.0f, moveVertical); // moving the player

        rb.AddForce(movement * speed); // speed of the movement
        
    }
}
```
    
## Moving the camera
This part is the code that moves the camera. The camera will follow the character where ever it goes.
```
using UnityEngine;
using System.Collections;

public class CameraController : MonoBehaviour
{

    public GameObject player;

    private Vector3 offset;

    void Start()
    {
        offset = transform.position - player.transform.position; // distance between the camera and the player
    }

    void LateUpdate()
    {
        transform.position = player.transform.position + offset; // follow the player
    }
}
```

## NPC movement
This is the code to move the object random like NPCs in the game.
```
using UnityEngine;
using System.Collections;

[RequireComponent(typeof(CharacterController))]  // Creates wandering behaviour for a CharacterController.
public class RandomMovement : MonoBehaviour
{
    public float speed = 1;
    public float directionChangeInterval = 1;
    public float maxHeadingChange = 30;

    CharacterController controller;
    float heading;
    Vector3 targetRotation;

    void Awake()
    {
        controller = GetComponent<CharacterController>();

        // Set random initial rotation
        heading = Random.Range(0, 360);
        transform.eulerAngles = new Vector3(0, heading, 0);

        StartCoroutine(NewHeading()); // Model behavior over several frames
    }

    void Update()
    {   
        // Moving the object foward while rotating
        transform.eulerAngles = Vector3.Slerp(transform.eulerAngles, targetRotation, Time.deltaTime * directionChangeInterval);
        var forward = transform.TransformDirection(Vector3.forward);
        controller.SimpleMove(forward * speed);

    }

    // Repeatedly calculates a new direction to move towards.
    // Use this instead of MonoBehaviour.InvokeRepeating so that the interval can be changed at runtime.
    IEnumerator NewHeading()
    {
        while (true)
        {
            NewHeadingRoutine();
            yield return new WaitForSeconds(directionChangeInterval);
        }
    }

    // Calculates a new direction to move towards.
    void NewHeadingRoutine()
    {
        var floor = transform.eulerAngles.y - maxHeadingChange;
        var ceil = transform.eulerAngles.y + maxHeadingChange;
        heading = Random.Range(floor, ceil);
        targetRotation = new Vector3(0, heading, 0);
    }
}
```

## Takeaways
* **Create sample codes** I can be helpful to create a sample of what you are trying to create since you are about to have an idea of how you want to create your product. You can test with the sample and make different changes to make it similar to the actual product. Then, you can use the sample to be put in the product and make tweaks.
* **Comment your code** Commenting your code helps remind you of what that piece of code is about. You may understand the code at the moment, but when you want to go back and make changes, you may forget what the code is. Commenting can also help you better understand your code since you are explaining what the code does.

[Back](entry-2.md) | [Next](entry-4.md) <br><br>
[Table of Contents](../README.md)
