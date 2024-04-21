# Isle Ecosystem

The following documentation contains a proposal for a standard implementation of a file structure, and synchronization protocol between a server and multiple clients, designed with the vision of a functional, extensible, and long-lasting XR metaverse.

## Context and purpose

In the current year (2024), the state of the so called "metaverse" is handled by very few platforms, from which, one ([VRChat](https://hello.vrchat.com/)) is clearly the most advantaged, and another one ([NeosVR](https://neos.com/) / [Resonite](https://resonite.com/)) the most advanced, being both of them private, and so, relying on their servers to work. This situation creates two negative consequences in their huge communities, the first one being that all of the knowledge and content uploaded to said platforms will, at some point, be lost for good due to the servers shutting down, and the other, the creation of a clear dependency by third party organizations on them to create XR events, campaigns, or other social activities. Another big problem created by the first platform mentioned is the hard dependency on the engine it uses, [Unity Engine](https://unity.com/), making it impossible to compatibilice with other software, and requiring the engine's private SDK to create and upload content.

The sole purpose of this proposal is to offer an open-source alternative that can be implemented as both, server and client, independent of the engine, device, and context that the software is running on, while at the same time being as easy to implement and integrate as possible with other already existing data transfer protocols, such as HTTP / HTTPS.

## Tree

In order to create a standard and non-limited way to transfer files between different systems, glTF offers the best solution. This format, maintained by the [Khronos Group](https://www.khronos.org/), consists of a structural part (Json), which stores information about the scene and the properties of the 3D elements it contains, and a binary part, that contains models and textures to be deployed. Though, the design to store only 3D scenes is incomplete for our purpose, as a metaverse also requires XR specific nodes, audio, and scripts, amongst others. This is where glTF's extensibility comes in, allowing for more properties to be include within the Json structure, as well as other types of binary data. One example of an integration for avatars is the VRM file format, by the [VRM Consortium](https://vrm-consortium.org/en/).

Most modern game engines, such as the previously mentioned Unity, [Godot](https://godotengine.org/), or [Unreal](https://www.unrealengine.com/en-US), have a programming workflow based on objects (object oriented), with classes that allow for the creation of a hierarchy structure, where objects can be parents of other objects, inheriting other aspects, like 3D transformation. While some engines prefer to make these objects out of componentes (classes), glTF considers each object as the class itself. This is the same workflow Godot Engine uses.

As it's been established, the Isle tree uses a glTF-like structure, but it has more requirements, such as the need to separate the elements properly, so not all of them are in the same category. There are three categories: *Worlds*, that must be only one per Isle, and is the base scenario to put the rest of the content in; *Avatars*, which are the representation of the clients, who must have only one selected at a time; and *Artifacts*, which are other interactable instances that the clients can summon.

## Protocol

In video game development, the ability to transfer data in order, quickly, safely, and reliably is essential. While TCP ensures some of these purposes, it lacks others, even in the modern day, so UDP subprotocols are used instead to create game sessions. Another way to look at it would be whether the system is better to be peer to peer (p2p), or client / server, both having advantages and disadvantages. For the purpose of safety, as Isle is designed to run on the internet publicly, client / server is the way to go. Glenn Fiedler wrote [an article](https://web.archive.org/web/20180823014904/https://gafferongames.com/categories/building-a-game-network-protocol) back in 2018 talking more in depth about this topic, from which Isle is departing.

This project, though, encounters some other difficulties that need to be considered.

The first one is the interaction that tree elements can have with each other. To put it simple: an avatar should not be able to rule over the world, and artifacts should not be able to rule over avatars, even though everything is running on the same tree. To prevent this from happening, it's important that the information that it's being transmitted has a *scope*, depending on the entity that is sending it. These scopes are *Isle*, *World*, *Avatar*, and *Artifact*, where the first has the highest priority, and the last one, the lowest.

Though, not all the synchronized events happen inside the tree, hence, the second difficulty shows up, the *context*. There are three possible contexts: *Server*, *Client*, and *Tree*, each one having different ways of communication.

It all sums up to the following characteristics:
* Packages must use UDP to have enough transfer speed.
* Packages must only be sent and received in order.
* Packages must be tagged in order to keep the reliability and ensure they've been received.
* Packages are made out of messages, which don't necessarily have the same length.
* Messages group up in three different contexts, which have may have same philosophy, but different purpose and structure.
* Server context is used to define parameters of the connection.
* Client context is used to transfer common client data, such as inputs, voice, or chat.
* Tree context is used by the nodes to communicate and sync the tree between clients.
* Within tree context, a four level hierarchy is required to ensure nodes from lower scopes cannot interfere with the operation of higher scopes.
* Isle scope is used to define the general rules of the working tree, as well as override parameters of the world if needed.
* World scope is used to synchronize global elements, as well as to define basic spatial and visual rules, such as gravity or post-processes.
* Avatar scope is used to synchronize avatar states, avatar shifts, and avatar to avatar interactions.
* Artifact scope is used to synchronize artifact states, summon and destruction of artifacts, and artifact to artifact interaction.

## Scripting

During the analysis, high-level scripting languages like Python were brought to the table, but in the end, JavaScript and the more recent TypeScript have been selected instead, due to their obfuscability, popularity, and compatibility between each other. These two scripting languages are most commonly used for web development, and so, the standard library needs to change accordingly. This adaptation, though, is not the first time that has been done, as showcased by the [GodotJS](https://geequlim.github.io/ECMAScript/) project, which integrates JS and TS into the Godot Engine, and from which this project takes note from.

## Virtual Machine

Even though scripts are usually fast enough to execute, they are not powerful enough to do more computational expensive operations, or simply allow for more objects with custom behaviors in the tree at once. This is the same reason why other VR social platforms are moving to a virtual machine model instead of scripting as well. A virtual machine is capable of running compiled bytecode, which is much faster, and it can also be translated to native binaries very effectively, making it even more efficient. This is also similar to how graphic cards (GPUs) run shaders, by compiling bytecode (or an intermediate language) such as [SPIR-V](https://registry.khronos.org/SPIR-V/) or [DXBC](https://learn.microsoft.com/en-us/windows/win32/direct3dhlsl/shader-model-5-assembly--directx-hlsl-) to their own native architecture. Bytecode also allows for virtually any programming language to be available for development, as the code needs to be compiled either way.
