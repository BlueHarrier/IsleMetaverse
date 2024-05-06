# ITF_light_source

## Description

Node extension that defines a light source, defining its attributes and type.

## Usage

```json
{
    "name": "Light bulb",
    "position": [0.0, 10.0, 0.0],
    "mesh": 3,
    "extensions": {
        "ITF_light_source": {
            "type": "POINT",
            "radius": 5.0,
            "attenuation": 1.0,
            "color": [177, 154, 119],
            "intensity": 1.0,
            "shadow": "SMOOTH"
        }
    }
}
```

* type: Can be POINT, SPOTLIGHT or DIRECTIONAL, and it represents the type of light being showcased. Each one has their own parameters.
* color: Can be an array of three integers between 0 and 255, an array of three floats between 0.0 and 1.0, or a string with the hex value of the color in #RRGGBB.
* intensity: Light intensity multiplier.
* shadow: The type of shadows the light casts. Can be NONE, HARD, or SOFT.
