# ITF_audio_streams

## Description

Root extension that defines an audio file, for ITF_audio_emitters to use.

## Usage

This extension consists of a list of audios, which, similar to glTF 2.0 textures, can be defined using an uri, or a part of the buffer, accompanied with the type they mime.

```json
{
    "extensions": {
        "ITF_audio_streams": [
            {
                "uri": "SqueakyBird.mp3"
            },
            {
                "bufferView": 13,
                "mimeType": "audio/ogg"
            }
        ]
    }
}
```

* uri: The uri of the audio file relative to this itf file.
* bufferView: The buffer view that points at the data stored within a binary.
* mimeType: The format of the audio that is going to be played, which can be `audio/mp3`, `audio/ogg`, or `audio/wav`.
