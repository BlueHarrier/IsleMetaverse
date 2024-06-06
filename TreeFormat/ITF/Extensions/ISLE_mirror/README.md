# ISLE_mirror

## Contributors

* Daniel Píriz, [BlueHarrier](https://github.com/blueharrier/)

## Status

Isle Ecosystem red 🔴

## Dependencies

Written against the glTF 2.0 spec.

Can depend on `ISLE_canvas` to be implemented, but not for all cases.

## Overview

This extension allows for mirrors to be place in the world.

In the metaverse, is common to see different members of all sorts of communities obsessed with mirrors. For weird that it may sound, it makes sense, considering the metaverse allows anybody to be anything they ever want to be. Hence, this project considers mirrors to be a necessity.

Mirrors have two ways to be implemented, being the first one the in-node implementation, and the other one the canvas implementation, being the second option more advanced, and designed for special effects and tricks.

### Examples

In the following example, an in-node implementation is showcased. The extension uses the node to create a mirror of a certain size of 10x5 meters.

```json
"nodes": [
    {
        "scale": [10.0, 5.0, 1.0],
        "extensions": {
            "ISLE_mirror": {
                "quality": "HIGH",
                "scale": 1.0
            }
        }
    }
]
```

As a counterpart of the previous snippet, an implementation using a canvas is more flexible, as it allows the creator to put the texture of the mirror on any surface using canvases.

```json
"images": [
    {
        "extensions": {
            "ISLE_canvas": {
                "format": 23,
                "scale": 1.0
            }
        }
    }
],
"nodes": [
    {
        "extensions": {
            "ISLE_mirror": {
                "quality": "HIGH",
                "canvas": 0
            }
        }
    }
]
```

This will prevent the mirror from drawing on the spot, instead, it will draw the result on the canvas. It's important to consider that the mirror will extend up to infinity in this situation, so no scale is needed to define its size. Also, keep in mind that using a canvas in `width`/`height` setup can result in the image being distorted, among other projection artifacts.

### Plane

This extension takes the position of the node as the center of the mirror, the scale will be the size of it (on a default plane of 1x1), and the rotation considers that the plane is placed along the +z axis, having +y being up and +x being right.

| Property  | Description | Required |
|-----------|-------------|----------|
| `quality` | Can be `"HIGH"`, `"MEDIUM"`, or `"LOW"`, and represents the present for the elements that will be drawn by the application. | No, Default: `"HIGH"` |
| `scale`   | Similar to `ISLE_canvas`'s `scale` parameter, it represents a factor of the application's frame buffer size. | Yes, if `canvas` is not present |
| `canvas`  | Canvas image that the reflection will be rendered onto. This will disable the automatic drawing of the mirror, and it's the creator's responsibility to do it. | Yes, when `scale` is not present |
