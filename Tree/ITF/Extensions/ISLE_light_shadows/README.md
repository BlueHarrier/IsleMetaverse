# ISLE_light_shadows

## Contributors

* Daniel Píriz, [BlueHarrier](https://github.com/blueharrier/)

## Status

Isle Ecosystem red 🔴

## Dependencies

Written against the glTF 2.0 spec.

Depends on `KHR_lights_punctual` to be implemented.

## Overview

This extension allows for shadows to be configured in all types of lights.

While in the 3D filming industry shadows are not really a concern, as they're assumed to exist through techniques like raytracing, though, for video game development, or other applications that require real-time rendering, shadows require other settings that may not offer the best quality, or might even be omitted completely.

This extension works along `KHR_lights_punctual` to offer the possibility of using shadows in real-time applications, including settings like range, softness, reverse cull, bias, normal bias, and many others.

Another characteristic of this extension is the possibility to add shadow receiving and casting settings to meshes, such as if casting is enabled, the mode of it, and whether it should receive shadows or not.

### Example

In the following example, the directional light presented is now implemented with shadows. Directional lights have some extras, like how many cascades it has, how they blend, and how far apart are they between each other.

```json
"extensions": {
     "KHR_lights_punctual" : {
        "lights": [
            {
                "color": [
                    1.0,
                    1.0,
                    1.0
                ],
                "type": "directional",
                "extensions": {
                    "ISLE_light_shadows": {
                        "bias": 0.1,
                        "normalBias": 2,
                        "reverseCull": false,
                        "strength": 1.0,
                        "blur": 0.5,
                        "renderDistance": 100,
                        "fadeStart": 0.9,
                        "cascades": 4,
                        "blendCascades": true,
                        "cascadeSplits": [0.125, 0.25, 0.5]
                    }
                }
            }
        ]
    }
}
```

In the other hand meshes can implement this extension to cast or not shadows, and how.

```json
"meshes": [
    {
        "primitives": {/* ... */},
        "extensions": {
            "ISLE_light_shadows": {
                "castShadows": "ON",
                "receiveShadows": true
            }
        }
    }
]
```

### Light Types

The required extension provides three different light types, and the shadows need to have different settings for them. Though, most of the settings are common.

#### Common Settings

All shadows have common settings that apply to how they're rendered and post-processed before being used in the scene.

| Property      | Description                                                                              | Required             |
|---------------|------------------------------------------------------------------------------------------|----------------------|
| `bias`        | Displacement that is applied to the shadow to prevent a phenomenon called "shadow acne". | No, Default: `0.1`   |
| `normalBias`  | Similar to `bias`, but applied along the normal of the mesh.                             | No, Default: `2`     |
| `reverseCull` | Whether to reverse the face culling of the shadow geometry.                              | No, Default: `false` |
| `strength`    | Between `0.0` and `1.0`, how opaque the shadow is.                                       | No, Default: `1.0`   |
| `blur`        | Ranges from `0.0` to `1.0`, and defines how much a shadow is soften.                     | No, Default: `1.0`   |


#### Directional Light

Directional lights are rendered using an orthogonal projection, and usually have the longest range of them all. For this reason, a bigger texture is used to store its information alongside different cascades, progressively increasing the render distance until the maximum. Each cascade is blurrier, but has a wider range.

| Property         | Description                                                                                                | Required                                       |
|------------------|------------------------------------------------------------------------------------------------------------|------------------------------------------------|
| `renderDistance` | The maximum distance that the directional shadow can reach. The higher, the blurrier.                      | No, Default: `100`                             |
| `fadeStart`      | The normalized distance (from `0.0` to `1.0`) until `renderDistance` at which the shadow begins to soften. | No, Default: `0.9`                             |
| `cascades`       | The number of cascades for the shadow. It can only be `1`, `2` or `4`.                                     | No, Default: `4`                               |
| `blendCascades`  | Whether the cascades should blend between each other, depending on `cascadeSplit`, or if they should change abruptly.                                                                                                                     | No, Default: `true`. Omit when using 1 cascade |
| `cascadeSplits`  | An array of numbers between `0.0` and `1.0`, matching the number of `cascades - 1`, indicating at what normalized distance should the cascades change.                                                                                                                       | No, Default: `[0.5]` using 2 cascades, `[0.125, 0.25, 0.5]` when using 4. Omit when using 1 cascade. |

#### Point Light

The only relevant setting for the point lights is whether the author wants them to be precise, fast, or if it's irrelevant (automatic). This is because point lights have different ways of being implemented, usually depending on how many render calls it requires, if one, or multiple.

| Property   | Description                                                                                                                                   | Required              |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|
| `renderMode` | Can be `"FAST"`, `"PRECISE"`, or `"AUTO"`, as point lights have different ways to be rendered, letting the application decide how to do them. | No, Default: `"AUTO"` |

#### Spotlights

Spotlights are automatically generated by the application, as the shape of their cones already define the most relevant shadow properties.

### For Meshes

Sometimes, meshes will require not to cast or receive shadows, in which case, it can be specified.

| Property      | Description                                                                              | Required             |
|---------------|------------------------------------------------------------------------------------------|----------------------|
| `castShadows` | Indicates whether the mesh casts shadows or not, and the way it should cast them. It can be `"OFF"`, `"ON"`, `"DOUBLE_SIDED"`, which makes the shadow caster draw the mesh without backface culling, or `"SHADOWS_ONLY"`, which will only render the shadow, ignoring the material. | No, Default: `"ON"` |
| `receiveShadows` | Indicates if the object can receive shadows or not. | No, Default: true |
