# ITF_artifact

## Description

Scene extension that defines an artifact and its basic attributes.

## Usage

This extension defines the name, the author, and the version of an artifact, and it's incompatible with ITF_world and ITF_avatar extensions.

```json
"scene": {
    "nodes": [0],
    "name": "Water gun scene",
    "extensions": {
        "ITF_artifact": {
            "name": "Water gun",
            "author": "BlueHarrier",
            "version": "1.0",
            "tags": [
                "Water",
                "Gun",
                "Pistol",
                "Cartoon"
            ]
        }
    }
}
```

* name: A string that defines the name of the artifact.
* author: The name of the author or authors of the artifact.
* version: The version of the artifact as a string.
* tags: A list of keywords that describe the artifact.