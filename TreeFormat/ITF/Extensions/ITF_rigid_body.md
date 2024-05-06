# ITF_rigid_body

## Description

Node extension that defines a body that will be affected by the physics rules of the world.

## Usage

This node extension specifies physical properties of the object, such as the mass and gravity scale. It can also have initial linear and angular velocities.

```json
{
    "name": "Ball",
    "position": [0.0, 2.0, 0.0],
    "extensions": {
        "ITF_rigid_body": {
            "mass": 1.0,
            "gravityScale": 1.0,
            "drag": 0.0,
            "linearVelocity": [0.0, 0.0, 0.0],
            "angularVelocity": [0.0, 0.0, 0.0],
            "colliders": [
                {
                    "shape": "SPHERE",
                    "radius": 1.0
                }
            ]
        }
    }
}
```

* mass: Mass of the object in Kg. Must be greater than zero.
* gravityScale: Scale in which the gravity will affect the object.
* drag: Friction of the object with the air, which slows down movement and rotation.
* linearVelocity: Initial velocity of the object in an [X, Y, Z] vector.
* angularVelocity: Initial rotation velocity of the object along the [X, Y, Z] axis.
* colliders: List of all collider objects used in the rigid body, determined by the shape and attributes of each one of them. There must not be any CONCAVE colliders.
