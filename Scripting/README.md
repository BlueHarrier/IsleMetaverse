# Scripting

## Introduction

The Isle Metaverse ecosystem's JavaScript environment corresponds to the set of functions and helper objects that developers can use to create artifacts. The standard library included in the environment contains said functions and objects, and is designed to be as simple and easy to use as possible, while providing a wide range of functionalities.

## Standard library objects

### Core

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

### APIs

Environment singletons that are used to interact directly with the system. They are:

- **`Console`**: An API that provides access to the console, allowing artifacts to log messages to the terminal.
- **`Input`**: An API that provides access to the input system, allowing artifacts to handle user input.
- **`Network`**: An API that provides high-level access to the network, allowing artifacts to synchronize their data between clients, and perform HTTP calls.
- **`System`**: An API that provides data related to the system, such as the client version. It also provides pointer access to link and load WebAssembly modules, and allows access to files inside the artifact, and the artifact's local storage (saving and loading data).
- **`World`**: An API that allows artifacts to instantiate new worlds, other artifacts, and to obtain information about their current world, such as the rules and server implementations.
