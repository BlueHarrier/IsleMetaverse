# ITF_audio_emitter

## Description

Node extension that defines an audio emitter in the world, using the node's transformation to place it.

## Usage

This node only requires the stream ID to work, and the attenuation type if it is an emitter point in the world. If the audio is meant to be global, attenuation and radius should be omitted.

```json
"nodes": [
    {
        "name": "Audio emitter",
        "position": [15.0, 0.0, 15.0],
        "extensions": {
            "ITF_audio_emitter": {
                "stream": 2,
                "attenuation": "INVERSE",
                "radius": 10.0,
                "pitch": 1.0,
                "play": true,
                "volume": -5
            }
        }
    }
]
```

* stream: The ID of the stream buffer to use.
* attenuation: The attenuation model to use, which can be `INVERSE`, `INVERSE_SQUARE`, `LOGARITHMIC`, or `DISABLED`.
* radius: The distance in which the emitter can be heard.
* pitch: The scale of the pitch of the sound that's playing.
* play: Boolean that determines whether the emitter is playing the stream.
* volume: The volume of the stream in decibel difference, so 0 is the normal volume, positive is more, and negative is less.
