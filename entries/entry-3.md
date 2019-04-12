Entry 3: Creating Movements

# Recap

# Moving character
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
