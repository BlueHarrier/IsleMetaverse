# ISLE_canvas

## Contributors

* Daniel Píriz, [BlueHarrier](https://github.com/blueharrier/)

## Status

Isle Ecosystem red 🔴

## Dependencies

Written against the glTF 2.0 spec.

## Overview

This extensions allows images to store render target information for them to be used dynamically after.

In video game development, having multiple cameras is used to create diegetic elements, such as security cameras, mirrors, etc. In order for those cameras to be seen in the world, a canvas needs to be used. The purpose of this extension is that to create these canvases dynamically, based on the user camera, or specifying its properties, as well as giving the cameras the possibility to set the target and refresh rate.

### Example

Images that are defined as canvas don't require uri nor buffer view, as they will be dynamically render onto, so they just need to be allocated in the system's memory.

```json
"images": [
    {
        "extensions": {
            "ISLE_canvas": {
                "format": 23,
                "width": 512,
                "height": 512
            }
        }
    },
    {
        "extensions": {
            "ISLE_canvas": {
                "format": 23,
                "scale": 1.0
            }
        }
    }
]
```

In the previous example, there are two images that implement `ISLE_canvas`. Both have the same format, which is the Vulkan format FOR `VK_FORMAT_R8G8B8_UNORM`, a 8 bits per channel format with RGBA color as a float from `0.0` to `1.0`. The first example uses absolute resolution, while the second one uses relative resolution.

This extension allows cameras to draw on these canvases, giving extra information on what canvas target to use, and what the refresh rate should be.

```json
"cameras": [
    {
        "type": "perspective",
        "perspective": {
            "aspectRatio": 1.0,
            "yfov": 0.7,
            "zfar": 100,
            "znear": 0.01
        },
        "extensions": {
            "ISLE_canvas": {
                "target": 0,
                "refreshRate": 30
            }
        }
    }
]
```

### Formats

Though each render engine has their own formats, all of them have common formats, and so, the Vulkan formats have been chosen to be the standard for this extension. The full list of format can be found in the [Resource](#resource) section.

### Image canvases

| Property | Description                                                                                                               | Required                      |
|----------|---------------------------------------------------------------------------------------------------------------------------|-------------------------------|
| `format` | Corresponds to the Vulkan format index, an integer that represents the data format of the image, this is how the image information is encoded and interpreted. | No, Default: `23` (`VK_FORMAT_R8G8B8_UNORM`) |
| `width`  | Width of the image to allocate. Incompatible with `scale`.                                                                | Yes, if `scale` is not defined |
| `height` | Height of the image to allocate. Incompatible with `scale`.                                                               | Yes, if `scale` is not defined |
| `scale`  | Creates a canvas from a factor of the main application's frame buffer. It's incompatible with the `width`/`height` setup. | Yes, when `width` and `height` are not present. |

### Cameras

| Property      | Description                                                                                          | Required                                              |
|---------------|------------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| `target`      | Canvas target that the camera will draw onto.                                                        | Yes                                                   |
| `refreshRate` | When present, will define the exact framerate that the camera will render the world on the `target`. | No, Default: automatically defined by the application |

## Resource

* Vulkan formats: https://registry.khronos.org/vulkan/specs/1.3-extensions/man/html/VkFormat.html
