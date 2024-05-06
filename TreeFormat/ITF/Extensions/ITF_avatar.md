# ITF_avatar

## Description

Scene extension that defines the general attributes of an avatar.

## Usage

This extension is incompatible with `ITF_world` and `ITF_artifact`, and it's utilized to define the basic avatar attributes, such as the base scale, the features it has, and the metadata.

```json
"scene": {
    "nodes": [0],
    "name": "Blue",
    "extensions": {
        "ITF_avatar": {
            "name": "Blue birdy",
            "author": "BlueHarrier",
            "version": "1.1",
            "tags": [
                "Bird",
                "Male",
                "Avian",
                "Humanoid",
                "Furry"
            ],
            "height": 1.59,
            "rig": {
                "type": "HUMANOID",
                "head": 
            }
        }
    }
}
```

* name: The name of the avatar.
* author: The name of the author or authors of the avatar.
* version: The version of the avatar as a string.
* tags: A list of keywords that describe the avatar.
* height: The base height of the eye level of the avatar.
* features: A list containing the features that the avatar has, which can be:
    * HEAD: If this avatar has head tracking.
    * HANDS: If this avatar has hand tracking and potential arm tracking.
    * FINGERS: If this avatar has fingers that can be tracked.
    * FEET: When the avatar has trackable feet.
    * EYES: When the avatar has eye movement that can be tracked.
    * FACE: If the avatar has face expressions that can be used using facial hardware.
    * HAPTICS: If the avatar is configured for haptic feedback devices.
