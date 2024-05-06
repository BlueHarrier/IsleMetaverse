# ITF_static_body

## Description

Node extension that defines a body that cannot move, or has scripted movement, but can be collided with in the world.

## Usage

This node extension specifies a body that's not supposed to move in the world, hence, it's static.

```json
{
    "name": "Floor",
    "position": [0.0, -0.5, 0.0],
    "extensions": {
        "ITF_static_body": {
            "colliders": [
                {
                    "shape": "BOX",
                    "size": [20.0, 1.0, 20.0]
                }
            ]
        }
    }
}
```

* colliders: List of all collider objects used in the static body, determined by the shape and attributes of each one of them.
