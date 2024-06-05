# ITF_world

## Description

Scene extension that defines the attributes, rules, and characteristics of a world.

## Usage

Worlds are an essential and complex part of the system, and this extension is used to define all of the basic rules of it, as well as its metadata. It also establishes the general appearance of the world by defining the lighting.

```json
"scene": {
    "nodes": [0],
    "name": "Isle World Example",
    "extensions": {
        "ITF_world": {
            "name": "Isle Water Park",
            "author": "BlueHarrier",
            "version": "1.0",
            "tags": [
                "Water",
                "Park",
                "Attraction",
                "Fun"
            ],
            "rules": {
                "userGravity": [0.0, -9.8, 0.0],
                "userAcceleration": 5.0,
                "userDeceleration": 10.0,
                "userMaxVelocity": 10.0,
                "userJumpSpeed": 25.0,
                "userMaxFallSpeed": 50.0,
                "userAllowVelocityScaling": true,
                "userRespawnFallDistance": 30,
                "userSpawnPolicy": "RANDOM",
                "userSpawners": [
                    1,
                    2,
                    3
                ]
            },
            "physics": {
                "gravity": [0.0, -9.8, 0.0],
                "airThickness": 1.0,
                "windForce": [0.0, 0.0, 0.0]
            },
            "environment": {
                "cameraZNear": 0.1,
                "cameraZFar": 200,
                "fogEnabled": true,
                "fogStartDistance": 100,
                "fogEndDistance": 200,
                "fogColor": [0.5, 0.5, 0.5],
                "ambientLightSource": "SKYBOX",
                "skyboxType": "TEXTURE",
                "skyboxTexture": 0
            }
        }
    }
}
```

* name: A string that defines the name of the world.
* author: The name of the author or authors of the world.
* version: The version of the world as a string.
* tags: A list of keywords that describe the world.
* rules: An object containing the set of rules that define the world:
    * userGravity: Vector `[x, y, z]` that defines the direction and acceleration of the gravity that affects users in m/s^2.
    * userAcceleration: Maximum acceleration that users can have in m/s^2.
    * userDeceleration: Rate at which user decelerate in m/s^2.
    * userMaxVelocity: Maximum velocity at which a user can move in m/s.
    * userJumpSpeed: Maximum velocity at which users can jump in m/s.
    * userMaxFallSpeed: Maximum velocity at which a user can fall in m/s.
    * userAllowVelocityScaling: Whether the velocity should scale with the height of the avatar or not, considering the base height is 1 meter.
    * userRespawnFallDistance: Distance from the origin of the world along the normalized gravity vector in which users and artifacts will respawn at their original position.
    * userSpawnPolicy: Indicates how the system will automatically choose what point to spawn at. The different options are "RANDOM", if the spawn point is chosen randomly, or "ORDERED", if users should spawn in order along the user spawners list.
    * userSpawners: A list with node IDs that represent the spawners, from which, position and direction will be transferred to the user.
* physics: An object containing the set of physic rules that define the world:
    * gravity: Vector `[x, y, z]` that defines the direction and acceleration of the gravity that affects physic bodies, soft bodies, and particles in m/s^2.
    * airThickness: Physics body drag multiplier.
    * windForce: Force constantly being applied to all physics bodies in order to simulate wind.
* environment: An object with all world environment settings.
* postProcessing: An object with all enabled post processing with their settings.
