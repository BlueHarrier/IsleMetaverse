# ITF files

## Index

* ITF_static_body
* ITF_rigid_body
* ITF_soft_body
* ITF_bone_chain
* ITF_constraint
* ITF_trigger
* ITF_button
* ITF_pickup
* ITF_seat
* ITF_audio_emitter
* ITF_audio_global
* ITF_video_player
* ITF_shader_material
* ITF_mirror
* ITF_canvas
* ITF_state_machine
* ITF_js_class
* ITF_ts_class
* ITF_WORLD_head
* ITF_WORLD_skybox
* ITF_WORLD_post_process
* ITF_WORLD_physics
* ITF_WORLD_lighting
* ITF_WORLD_rules
* ITF_AVATAR_head
* ITF_AVATAR_humanoid
* ITF_AVATAR_tracker_link
* ITF_AVATAR_facial_rig
* ITF_AVATAR_eye_position
* ITF_AVATAR_voice_position
* ITF_AVATAR_control_menu
* ITF_ARTIFACT_head
* ITF_RESOURCE_javascript
* ITF_RESOURCE_typescript
* ITF_RESOURCE_shader
* ITF_RESOURCE_audio
* ITF_RESOURCE_video

## Design philosophy

Following the general naming convention from the Khronos Group, all ITF extensions start with `ITF_`, followed by the name of the common extension, or `WORLD_`, `AVATAR_`, `ARTIFACT_`, or `UI_`, in case of that extension being constrained to one of those types. Alongside those node types, there's also the prefix `RESOURCE_`, to identify new resource types embebed in the buffer, such as audio and video.

Asset typing is very important for ITF files, as all of them are incompatible with the others. These types will be defined in one of the root nodes of a scene, and contain metadata about the asset type. Their names are identified by the termination `head`.

## Scene usage

glTF 2.0 files can contain different scenes. ITF contemplates that feature and integrates it so one of these files can have multiple scenes, each scene being one different resource. The goal is to give content creators the ability to make libraries which hold different content and content types within. This can also help create variants of one asset types, allowing for better optimization as less resources can be stored at a time, practice that is very common to do for avatars.

## File extension

Any Isle Tree Format needs to be identified by a different extension, depending on what glTF 2.0 file format uses. The default format to use is `.glb` (binary), which will use the extension `.itf`, though, it's also possible to use the ASCII format, `.gltf`, in which case, the extension of the file will be `jitf` (Json Isle Tree Format).

For best practice, the `.jitf` format should only be used for raw UI integration, as the required resources can be asynchronously called, making ITF based pages load much faster, similar to how webpages work. The rest of the assets should be stored as `.itf` files.
