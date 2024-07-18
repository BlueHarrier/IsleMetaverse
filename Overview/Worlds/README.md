# Worlds

Worlds are the continent of the ecosystem. They give the environment in which objects can interact with, including the rules, the physics, and the behavior of the objects. Worlds can be anything, from a simple room, to a whole universe, and can be controlled by the user that created them. Worlds can also be shared, and even be used as templates for other worlds, or even avatars. Worlds can also be used to create pocket worlds, which are worlds inside other worlds, and can be used to create very complex applications.

## Spawn points

Spawn points are not required in a world, avatars would spawn at (0, 0, 0) coordinates, but they can be placed, and then managed by the world as it needs to. Also, by default avatars will spawn as children of the world node, but it can also be changed to spawn on any other node, as long as it's a child of the world node. This also includes spawning inside other pocket worlds within the main one.

## Griefing prevention

To prevent other users to force people into pocket worlds, the only means of traveling between them is either a script doing the job, which requires a higher hierarchy, or a portal, which can only be access by the user's interaction, knowing that they are going to be teleported to another world.

## Pocket worlds

Pocket worlds, or more commonly named "dimensions", is a way in which the ecosystem can run multiple worlds at once, in the same environment. This is done by adding the `World` module to another node inside the already existing tree. Avatars will only be able to see and interact with elements that are in the same world as them, and travel between them using portals (class `Portal`). Portals can be instantiated by the scripting API, exist already in the tree, or even be created by the ISLE server. This allows for more complex applications to be made, like games, or even social networks, where users can interact with each other in different worlds, but still be in the same environment.

> [!TIP]
> In order to instantiate a portal back to a superior world, as they might be running in another template, the one world higher in the hierarchy can communicate with the world and add the portal to the world's spawn point.

> [!CAUTION]
> It's important to note that users should be allowed to respawn back into the default world, as they might get stuck in a world that doesn't allow them to go back to a superior world. The protocol will include a special instruction to request a respawn back to the default world, that will occur if allowed by the server.
> In the case of the client being run locally, the user can always do this, without the need of any server's permission.

Worlds can be instantiated inside everything (as long as the working hierarchy allows it), creating very interesting concepts, such as avatars holding pocket worlds, or artifacts that can be used to create new worlds. This allows for a very flexible system, where the user can create virtually anything they want, and the ecosystem will adapt to it.

## Between-worlds interaction

Worlds running in the same hierarchy can communicate between each other, and so, many cool stuff can be made with this, such as using cameras to render another world, as I'm writing this, I'm thinking about a small artifact, a snow globe, that, when interacted with (portal) can put users inside of it, allowing them to see the world outside, and the users outside, to see the world inside. This is a very cool concept, and can be used to create very interesting applications, and can even be implemented in an avatar, so it can be a pocket dimension in a character's collar, or even a pocket watch!

## Null world

What happens if there's no world attached anywhere on top of the avatar? I already see people panicking, but don't worry. All modules in Isle have default parameters, and worlds do too, so, in case of no world being available above the avatar, the default world parameters will be taken to display at least something.
