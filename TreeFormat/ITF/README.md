# ITF files

## Index

* [ITF_artifact](./Extensions/ITF_artifact.md)
* [ITF_audio_emitter](./Extensions/ITF_audio_emitter.md)
* [ITF_audio_streams](./Extensions/ITF_audio_streams.md)
* [ITF_avatar](./Extensions/ITF_avatar.md)
* [ITF_button](./Extensions/ITF_button.md)
* [ITF_canvas](./Extensions/ITF_canvas.md)
* [ITF_class](./Extensions/ITF_class.md)
* [ITF_constraint](./Extensions/ITF_constraint.md)
* [ITF_control_menu](./Extensions/ITF_control_menu.md)
* [ITF_light_source](./Extensions/ITF_light_source.md)
* [ITF_mirror](./Extensions/ITF_mirror.md)
* [ITF_physics_bone](./Extensions/ITF_physics_bone.md)
* [ITF_pickup](./Extensions/ITF_pickup.md)
* [ITF_rigid_body](./Extensions/ITF_rigid_body.md)
* [ITF_scripts](./Extensions/ITF_scripts.md)
* [ITF_seat](./Extensions/ITF_seat.md)
* [ITF_shader](./Extensions/ITF_shader.md)
* [ITF_shader_material](./Extensions/ITF_shader_material.md)
* [ITF_soft_body](./Extensions/ITF_soft_body.md)
* [ITF_state_machine](./Extensions/ITF_state_machine.md)
* [ITF_static_body](./Extensions/ITF_static_body.md)
* [ITF_trigger](./Extensions/ITF_trigger.md)
* [ITF_video_player](./Extensions/ITF_video_player.md)
* [ITF_video_streams](./Extensions/ITF_video_streams.md)
* [ITF_world](./Extensions/ITF_world.md)

## Scene usage

glTF 2.0 files can contain different scenes. ITF contemplates that feature and integrates it so one of these files can have multiple scenes, each scene being one different resource. The goal is to give content creators the ability to make libraries which hold different content and content types within. This can also help create variants of one asset types, allowing for better optimization as less resources can be stored at a time, practice that is very common to do for avatars.

## File extension

Any Isle Tree Format needs to be identified by a different extension, depending on what glTF 2.0 file format uses. The default format to use is `.glb` (binary), which will use the extension `.itf`, though, it's also possible to use the ASCII format, `.gltf`, in which case, the extension of the file will be `jitf` (Json Isle Tree Format).
