# Isle Metaverse

## Introduction

### Overview

The following documentation contains a proposal for a standard implementation of a functional, extensible, and long-lasting XR metaverse, based on a runtime environment, a data transfer protocol, and a set of standards for the creation and distribution of content.

### Context and purpose

In the current year (2024), the state of the so called "metaverse" is handled by very few platforms, from which, one ([VRChat](https://hello.vrchat.com/)) is clearly the most advantaged, and another one ([NeosVR](https://neos.com/) / [Resonite](https://resonite.com/)) the most advanced, being both of them private, and so, relying on their servers to work. This situation creates two negative consequences in their huge communities, the first one being that all of the knowledge and content uploaded to said platforms will, at some point, be lost for good due to the servers shutting down, and the other, the creation of a clear dependency by third party organizations on them to create XR events, campaigns, or other social activities. Another big problem created by the first platform mentioned is the hard dependency on the engine it uses, [Unity Engine](https://unity.com/), making it impossible to compatibilice with other software, and requiring the engine's private SDK to create and upload content.

The sole purpose of this proposal is to offer an open-source alternative that can be implemented as both, server and client, independent of the engine, device, and context that the software is running on. While it was at first thought with ease of implementation in mind, this task was too hard to accomplish without constraining developers into a specific set of tools and workflows, and so, the proposal was redesigned to have a bigger focus on the runtime environment, being more complex, but allowing for more flexibility and freedom to the developers.

## Key concepts

### Definitions

This project is based on the following definitions:

- **Metaverse**: An online, cross-platform environment made out of encapsulated XR applications that can interact with each other in such a way that the user can navigate through and interact with them seamlessly, while accompanied by other users.
- **Implementor**: A person or organization that creates and maintains a runtime environment with this specification.
- **Developer**: A person or organization that creates content for the metaverse.
- **User**: A person that interacts with the metaverse.
- **Ecosystem**: The combinations of elements that work together to conform an environment.

### Ecosystem

The ecosystem consists of a runtime environment based on JavaScript and WebAssembly 64, designed with the purpose of containing in a safely manner all the encapsulated applications that will run within it. It's not thought as a whole self-sustained system, but as a subsystem of a bigger one instead.

### Artifacts

Artifacts are the unit of content in the metaverse. They are encapsulated applications that can be interacted with by the user, and can represent a variety of things, ranging from a simple 3D object to a complex game. Artifacts interact with the runtime environment using servers and the API.

### Worlds

Worlds are the different environments where artifacts can be summoned. Though, they must not be seen as independent entities from artifacts, but as a part of them, as they are responsible of instancing worlds and managing their rules and servers.

### Servers

Servers are singleton interfaces that exist in a world. They are responsible for a variety of tasks, depending on their type. Though a default implementation is provided, developers can create their own server overrides to implement custom logic.

There are a total of five interfaces:

1. **Render server**: Responsible for managing the render engine (OpenGL or Vulkan), shaders, and render pipeline of the world.
2. **Physics server**: Responsible for managing the physic interactions and constraints in the world.
3. **Audio server**: Manages all the audio interactions in the world.
4. **Loop server**: Manages the logic loop and the timing of the world.
5. **Interaction server**: Defines how the avatars are controlled by the user, and how artifacts are interacted with.

### API

Similar to servers, the API consists of a set of singletons, but unlike them, they are not a part of the world, but of the runtime environment, and so, they cannot be overridden by developers. The API is responsible of managing more sensitive tasks, like the user's data, the network, and the artifact's lifecycle. They also provide the servers with access to lower level hardware access.

The global APIs that can be accessed by artifacts and servers are:

1. **System API**: Provides data related to the system, such as the client version.
2. **File API**: Provides access to the file system, allowing restricted access to artifact specific data that they can save and read back.
3. **Network API**: Provides high level access to the network, allowing artifacts to synchronize their data between clients, and perform HTTP calls.

### Coconuts

Coconuts are the templates that instantiate artifacts. Packages that contain all the files, binaries, and scripts to execute them. They can be directly executed by the runtime environment. Internally, they are a zip files with a specific structure and the `.nut` extension.

The file structure of a coconut is as follows:

```plaintext
|-- manifest.json
|
|-| src
| |-- main.js
| |-- ...
|
|-| bin
| |--...
|
|-- ...
```

All coconuts contain a manifest file, which contains metadata about the artifact and the world requirements (rules) to run it. The `src` folder contains all the JavaScript code that will be executed by the artifact, and the `bin` folder all the WASM64 binaries. `main.js` is the entry point script of the artifact, and it will be responsible of initializing the artifact and linking all the binaries if needed. The rest of the file structure is free to be used by the developer however they want, usually to store models, sound files, textures, etc.

### Protocol

> ![WARNING]
> The protocol doesn't even have a proper name yet, and so, it's just called "protocol" for now.
> Though, the purpose of it is to synchronize the artifacts between the clients, allow users to communicate through chat and voice, and to provide a way to download and upload artifacts without using a dedicated server to store them (HTTP).
