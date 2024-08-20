# World

## Overview

The `World` API is a high-level API that is used to obtain information on the working environment, and to create new worlds under the current artifact. It is used to manage the world's rules and servers.

### Servers

Interfaces that are used to manage different aspects of the environment, such as rendering, physics, audio, interaction, and the logic loop. A default one is provided, but they can also be replaced with a world own implementation. The servers are:

- **`AudioServer`**: A server that is responsible for managing all the audio interactions in the world.
- **`InteractionServer`**: A server that is responsible for defining how the avatars are controlled by the user, and how artifacts are interacted with.
- **`LoopServer`**: A server that is responsible for managing the logic loop and the timing of the world.
- **`PhysicsServer`**: A server that is responsible for managing the physics interactions and constraints in the world.
- **`RenderingServer`**: A server that is responsible for managing the render engine, shaders, and render pipeline of the world.

| Property | Type |
|----------|------|
| `audio` | `AudioServer` |
| `interaction` | `InteractionServer` |
| `loop` | `LoopServer` |
| `physics` | `PhysicsServer` |
| `rendering` | `RenderingServer` |

| Constants | Type | Value |
|-----------|------|-------|
| `RULE_FLAG_AVATAR` | `Number` | 1 |
| `RULE_FLAG_WORLD` | `Number` | 2 |
| `RULE_FLAG_INTERACTION` | `Number` | 4 |
| `RULE_FLAG_INPUT` | `Number` | 8 |
| `RULE_FLAG_AUDIO` | `Number` | 16 |
| `RULE_FLAG_MESH` | `Number` | 32 |
| `RULE_FLAG_SKINNED_MESH` | `Number` | 64 |
| `RULE_FLAG_PARTICLE` | `Number` | 128 |
| `RULE_FLAG_LIGHT` | `Number` | 256 |
| `RULE_FLAG_SHADERS` | `Number` | 512 |
| `RULE_FLAG_CAMERA` | `Number` | 1024 |
| `RULE_FLAG_TRIGGER` | `Number` | 2048 |
| `RULE_FLAG_RIGID_BODY` | `Number` | 4096 |
| `RULE_FLAG_STATIC_BODY` | `Number` | 8192 |
| `RULE_FLAG_CONSTRAINT` | `Number` | 16384 |
| `RULE_FLAG_WASM` | `Number` | 32768 |
| `RULE_FLAG_PUBLIC` | `Number` | 65536 |
| `RULE_FLAG_PRIVATE` | `Number` | 131072 |
| `RULE_FLAG_COMMERCIAL` | `Number` | 262144 |
| `RULE_FLAG_LICENSE` | `Number` | 524288 |
| `RULE_FLAG_OVERRIDE_AUDIO` | `Number` | 1048576 |
| `RULE_FLAG_OVERRIDE_INTERACTION` | `Number` | 2097152 |
| `RULE_FLAG_OVERRIDE_LOOP` | `Number` | 4194304 |
| `RULE_FLAG_OVERRIDE_PHYSICS` | `Number` | 8388608 |
| `RULE_FLAG_OVERRIDE_RENDERING` | `Number` | 16777216 |

> [!WARNING]
> The list of flag is subject to change as the project evolves. When version 1.0 of the reference is released, the list will be considered stable and the current flags will not change positions or values, but new flags may be added.
| Method | Returns |
|--------|---------|
| `audioServerIsDefault()` | `Boolean` |
| `audioServerIsPassthrough()` | `Boolean` |
| `createWorld(Object rules, Object serverBinaries)` | `Number` |
| `getArtifactRules()` | `Object` |
| `getGlobalRules()` | `Object` |
| `getWorldInstances()` | `Array` |
| `interactionServerIsDefault()` | `Boolean` |
| `interactionServerIsPassthrough()` | `Boolean` |
| `loopServerIsDefault()` | `Boolean` |
| `loopServerIsPassthrough()` | `Boolean` |
| `physicsServerIsDefault()` | `Boolean` |
| `physicsServerIsPassthrough()` | `Boolean` |
| `releaseWorld(Number worldId)` | `Boolean` |
| `renderingServerIsDefault()` | `Boolean` |
| `renderingServerIsPassthrough()` | `Boolean` |

## Property descriptions

### `AudioServer` audio

The audio server of the world, that can be the default, or a custom one.

### `InteractionServer` interaction

The interaction server of the world, that can be the default, or a custom one.

### `LoopServer` loop

The loop server of the world, that can be the default, or a custom one.

### `PhysicsServer` physics

The physics server of the world, that can be the default, or a custom one.

### `RenderingServer` rendering

The rendering server of the world, that can be the default, or a custom one.

## Constant descriptions

All constants of the class are flags that are used to define the characteristics of the artifacts. Use bitwise operations to combine and compare them.

### `RULE_FLAG_AVATAR`

Defines whether the artifact is an avatar.

### `RULE_FLAG_WORLD`

Defines whether the artifact has at least one world.

### `RULE_FLAG_INTERACTION`

Defines whether the artifact uses the interaction server.

### `RULE_FLAG_INPUT`

Defines whether the artifact uses the input server.

### `RULE_FLAG_AUDIO`

Defines whether the artifact plays audio.

### `RULE_FLAG_MESH`

Defines whether the artifact uses meshes.

### `RULE_FLAG_SKINNED_MESH`

Defines whether the artifact uses skinned meshes.

### `RULE_FLAG_PARTICLE`

Defines whether the artifact uses particles.

### `RULE_FLAG_LIGHT`

Defines whether the artifact uses lights.

### `RULE_FLAG_SHADERS`

Defines whether the artifact uses shaders.

### `RULE_FLAG_CAMERA`

Defines whether the artifact uses cameras.

### `RULE_FLAG_TRIGGER`

Defines whether the artifact uses triggers.

### `RULE_FLAG_RIGID_BODY`

Defines whether the artifact uses rigid bodies.

### `RULE_FLAG_STATIC_BODY`

Defines whether the artifact uses static bodies.

### `RULE_FLAG_CONSTRAINT`

Defines whether the artifact uses constraints.

### `RULE_FLAG_WASM`

Defines whether the artifact uses WebAssembly libraries.

### `RULE_FLAG_PUBLIC`

Defines whether the artifact is public.

### `RULE_FLAG_PRIVATE`

Defines whether the artifact is private.

### `RULE_FLAG_COMMERCIAL`

Defines whether the artifact is commercial or sponsors a commercial brand.

### `RULE_FLAG_LICENSE`

Defines whether the artifact has a `LICENSE` file in its root directory.

### `RULE_FLAG_OVERRIDE_AUDIO`

Defines whether the artifact overrides the audio server in any of its worlds.

### `RULE_FLAG_OVERRIDE_INTERACTION`

Defines whether the artifact overrides the interaction server in any of its worlds.

### `RULE_FLAG_OVERRIDE_LOOP`

Defines whether the artifact overrides the loop server in any of its worlds.

### `RULE_FLAG_OVERRIDE_PHYSICS`

Defines whether the artifact overrides the physics server in any of its worlds.

### `RULE_FLAG_OVERRIDE_RENDERING`

Defines whether the artifact overrides the rendering server in any of its worlds.

## Method descriptions

### `Boolean` audioServerIsDefault()

Returns whether the audio server is the default one.

### `Boolean` audioServerIsPassthrough()

Returns whether the audio server is a passthrough of the previous world's.

### `Number` createWorld(`Object` rules, `Object` serverBinaries)

Returns the ID of the new world that has been created.

The object that represents the rules is the set of maximums of each instantiable element that the world can have, which will automatically allow or disallow the instantiation of artifacts.

The object that represents the server binaries is the set of WebAssembly binaries that will be used to replace the default servers. Though, they can be one of three types:

* `DEFAULT`: will force the use of the default server.
* `PASSTHROUGH`: will use the server of the previous world (default strategy).
* `CUSTOM:{path/to/.wasm}`: will use the provided custom server, contained in a binary file. The path will be defined from `/bin`, like all other binary files.

> [!IMPORTANT]
> Servers are delicate pieces of software, and always require very low level to perform properly. Hence, they're always compiled to WebAssembly, and are not allowed to be written in JavaScript.

### `Object` getArtifactRules()

Returns the rules that are applied to the current artifact. These are a combination of the artifact's requested requirements and the current world's global rules. If an artifact's maximums are over the world's, they will be capped to the world's maximums, and if the minimums aren't met, it will not be allowed to instantiate.

### `Object` getGlobalRules()

Returns the world's global rules, which are the maximums of each instantiable element that any artifact can have. These rules are strict, and it's not recommended to leave any in infinite, as it can lead to performance issues.

### `Array` getWorldInstances()

Get the emitter artifact's instantiated world IDs.

### `Boolean` interactionServerIsDefault()

Returns whether the interaction server is the default one.

### `Boolean` interactionServerIsPassthrough()

Returns whether the interaction server is a passthrough of the previous world's.

### `Boolean` loopServerIsDefault()

Returns whether the loop server is the default one.

### `Boolean` loopServerIsPassthrough()

Returns whether the loop server is a passthrough of the previous world's.

### `Boolean` physicsServerIsDefault()

Returns whether the physics server is the default one.

### `Boolean` physicsServerIsPassthrough()

Returns whether the physics server is a passthrough of the previous world's.

### `Boolean` releaseWorld(`Number` worldId)

Releases the world with the given ID. This will free all resources that the world was using, including inner artifacts. Bound avatar's artifacts will be popped to the previous world instead.

### `Boolean` renderingServerIsDefault()

Returns whether the rendering server is the default one.

### `Boolean` renderingServerIsPassthrough()

Returns whether the rendering server is a passthrough of the previous world's.
