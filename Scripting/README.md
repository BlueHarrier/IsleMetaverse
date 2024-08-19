# Scripting

## Introduction

The Isle Metaverse ecosystem's JavaScript environment corresponds to the set of functions and helper objects that developers can use to create artifacts. The standard library included in the environment contains said functions and objects, and is designed to be as simple and easy to use as possible, while providing a wide range of functionalities.

## Key concepts

### Core objects

A set of objects that are used to interact with the environment, as well as to offer a wide variety of arithmetical functionalities to the developers. Those objects are:

- **`Basis2`**: A basis object that is used to represent scale and rotation in 2D space.
- **`Basis3`**: A basis object that is used to represent scale and rotation in 3D space.
- **`BBox2`**: A bounding box object that is used to represent a 2D area.
- **`BBox3`**: A bounding box object that is used to represent a 3D area.
- **`Color`**: A color object that is used to represent a color in the RGBA format.
- **`Quaternion`**: A quaternion object that is used to represent rotation in 3D space.
- **`Transform2`**: A transform object that is used to represent position, scale, and rotation in 2D space.
- **`Transform3`**: A transform object that is used to represent position, scale, and rotation in 3D space.
- **`Vector2`**: A vector object that is used to represent a 2D point.
- **`Vector3`**: A vector object that is used to represent a 3D point.
- **`Vector4`**: A vector object that is used to represent a 4D point.

### Helpers

Static classes containing helper functions that are used to perform common tasks, such as:

- **`Array`**: A class containing array manipulation functions.
- **`Console`**: A class containing functions to log messages to the console.
- **`Date`**: A class containing date and time manipulation functions.
- **`Error`**: A class containing functions to throw errors.
- **`JSON`**: A class containing functions to parse and stringify JSON data.
- **`Math`**: A class containing mathematical functions.
- **`Number`**: A class containing number manipulation functions.
- **`Promise`**: A class containing functions to create and manage promises.
- **`Random`**: A class containing random number generation functions.
- **`RegExp`**: A class containing functions to work with regular expressions.
- **`String`**: A class containing string manipulation functions.

### Servers

Interfaces that are used to manage different aspects of the environment, such as rendering, physics, audio, interaction, and the logic loop. A default one is provided, but they can also be replaced with a world own implementation. The servers are:

- **`AudioServer`**: A server that is responsible for managing all the audio interactions in the world.
- **`InteractionServer`**: A server that is responsible for defining how the avatars are controlled by the user, and how artifacts are interacted with.
- **`LoopServer`**: A server that is responsible for managing the logic loop and the timing of the world.
- **`PhysicsServer`**: A server that is responsible for managing the physics interactions and constraints in the world.
- **`RenderingServer`**: A server that is responsible for managing the render engine, shaders, and render pipeline of the world.

### API

Environment singletons that are used to interact directly with the system. They are:

- **`FileAPI`**: An API that provides access to the file system, allowing restricted access to artifact-specific data that they can save and read back.
- **`InputAPI`**: An API that provides access to the input system, allowing artifacts to handle user input.
- **`NetworkAPI`**: An API that provides high-level access to the network, allowing artifacts to synchronize their data between clients, and perform HTTP calls.
- **`SystemAPI`**: An API that provides data related to the system, such as the client version. It also provides pointer access to link and load WebAssembly modules.
- **`WorldAPI`**: An API that allows artifacts to instantiate new worlds, other artifacts, and to obtain information about their current world, such as the rules and server implementations.
