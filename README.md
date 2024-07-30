# Isle Ecosystem

The following documentation contains a proposal for a standard implementation of a file structure, and synchronization protocol between a server and multiple clients, designed with the vision of a functional, extensible, and long-lasting XR metaverse.

## Context and purpose

In the current year (2024), the state of the so called "metaverse" is handled by very few platforms, from which, one ([VRChat](https://hello.vrchat.com/)) is clearly the most advantaged, and another one ([NeosVR](https://neos.com/) / [Resonite](https://resonite.com/)) the most advanced, being both of them private, and so, relying on their servers to work. This situation creates two negative consequences in their huge communities, the first one being that all of the knowledge and content uploaded to said platforms will, at some point, be lost for good due to the servers shutting down, and the other, the creation of a clear dependency by third party organizations on them to create XR events, campaigns, or other social activities. Another big problem created by the first platform mentioned is the hard dependency on the engine it uses, [Unity Engine](https://unity.com/), making it impossible to compatibilice with other software, and requiring the engine's private SDK to create and upload content.

The sole purpose of this proposal is to offer an open-source alternative that can be implemented as both, server and client, independent of the engine, device, and context that the software is running on, while at the same time being as easy to implement and integrate as possible with other already existing data transfer protocols, such as HTTP / HTTPS.

## Tree

In order to create a standard and non-limited way to transfer files between different systems, different approaches have been studied, such as glTF, maintained by the [Khronos Group](https://www.khronos.org/), but has ultimately been discarded, as their solution is too strict to allow for the flexibility required by this project, though, has been kept as a valid structure in the ecosystem. Game engines often use a component based system, where each object has different behaviors, depending on those components.

In order to universalize the tree structure, every element of this ecosystem utilizes the same format and structure, using modules (components) attached to each node (objects) to alter their behavior. This includes worlds, avatars, and other user summonable items.

> [!TIP]
> Isle Tree Format is a mixture of Unity and Godot's philosophy, having a single root node at the top of the tree, but each node being composed by modules.

### Isle structure

Isles are the representation of the session. There's only one at the top of the hierarchy, and contains one single node with the `Isle` module, which is an invalid module everywhere else, and optionally, a `World` module as well. This object grants access to the session information, synchronization, users, and worlds. It keeps track of all summoned assets by each user, and the overall structure of the world.

#### Worlds

Worlds are nodes that contain the `World` module. All subsequent nodes will live inside of it, and will no longer be able to interact with anything above it, unless another module on top allows for that purpose, such as `Portal`s.

#### Avatars

Any node that implements the `Avatar` module is a valid avatar. In case it's being loaded from an ISL file, the root node must implement it.

#### Ownership

Nodes have owners, which is not a reference to the parent, but to the summoning user, or, if there's none, the Isle. Each summoning entity has a privilege level, that may go from 0 (lowest) to 255 (highest), restricting what can they do with the other nodes.

## Protocol

In video game development, the ability to transfer data in order, quickly, safely, and reliably is essential. While TCP ensures some of these purposes, it lacks others, even in the modern days, so UDP subprotocols are used instead to create game sessions. Another way to look at it would be whether the system is better to be peer to peer (p2p), or client / server, both having advantages and disadvantages. For the purpose of safety, as Isle is designed to run on the internet publicly, client / server is the way to go. Glenn Fiedler wrote [an article](https://web.archive.org/web/20180823014904/https://gafferongames.com/categories/building-a-game-network-protocol) back in 2018 talking more in depth about this topic, from which Isle is departing.

This project, though, encounters some other difficulties that need to be considered. The first difficulty is the "voice chat". In order for the metaverse to be immersive, proximity voice chat has to exist. Which requires ways to compress and transmit audio between users. Another difficulty is the tree synchronization, as the tree may vary along time. The ideal thing would be for the Isle to send a copy of the tree as it is in the current state, as long as the elements are synchronized, the trees will be the same between users, though, the user should receive tree updates from the on to keep the sync.

## Scripting

During the analysis, high-level scripting languages like Python were brought to the table, but in the end, JavaScript has been selected instead, due to its obfuscability and popularity. This scripting languages is most commonly used for web development, and so, the standard library needs to change accordingly. This adaptation, though, is not the first time that has been done, as showcased by the [GodotJS](https://geequlim.github.io/ECMAScript/) project, which integrates JS into Godot Engine, and from which this project takes note.

## Coconuts

Even though scripts are usually fast enough to execute, they are not powerful enough to do more computational expensive operations, or simply allow for more nodes with custom modules in the tree at once. This is the same reason why other VR social platforms are moving to a virtual machine model instead of scripting as well. A virtual machine is capable of running assembled bytecode, which is much faster, and can also be translated to native binaries very effectively, making it even more efficient. This is also similar to how graphic cards (GPUs) run shaders, by compiling bytecode (or an intermediate language) such as [SPIR-V](https://registry.khronos.org/SPIR-V/) or [DXBC](https://learn.microsoft.com/en-us/windows/win32/direct3dhlsl/shader-model-5-assembly--directx-hlsl-) to their own native architecture. Bytecode also allows for virtually any programming language to be available for development, as the code needs to be compiled either way. WASM (WASM64, as it supports more memory and operations) has been selected as a viable option, for its ease of implementation and rich documentation.

Coconuts are encapsulated applications that run within the environment, offering not only the same features that JS has, but much more, such as the ability to replacing native singletons, such as the rendering service (running on Vulkan), or the physics engine. The way they can interface with each other is through the use of the environment itself, which needs to be designed, but it will likely be a GNU - Linux.
