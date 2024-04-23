# ITF files

## Index

* ITF_artifact
* ITF_audio
* ITF_audio_emitter
* ITF_audio_global
* ITF_avatar
* ITF_bone_chain
* ITF_button
* ITF_canvas
* ITF_constraint
* ITF_control_menu
* ITF_eye_position
* ITF_facial_rig
* ITF_humanoid
* ITF_itf_javascript
* ITF_itf_typescript
* ITF_js_class
* ITF_lighting
* ITF_mirror
* ITF_physics
* ITF_pickup
* ITF_post_process
* ITF_rigid_body
* ITF_rules
* ITF_seat
* ITF_shader
* ITF_shader_material
* ITF_skybox
* ITF_soft_body
* ITF_state_machine
* ITF_static_body
* ITF_tracker_link
* ITF_trigger
* ITF_ts_class
* ITF_video
* ITF_video_player
* ITF_voice_position
* ITF_world

## Scene usage

glTF 2.0 files can contain different scenes. ITF contemplates that feature and integrates it so one of these files can have multiple scenes, each scene being one different resource. The goal is to give content creators the ability to make libraries which hold different content and content types within. This can also help create variants of one asset types, allowing for better optimization as less resources can be stored at a time, practice that is very common to do for avatars.

## File extension

Any Isle Tree Format needs to be identified by a different extension, depending on what glTF 2.0 file format uses. The default format to use is `.glb` (binary), which will use the extension `.itf`, though, it's also possible to use the ASCII format, `.gltf`, in which case, the extension of the file will be `jitf` (Json Isle Tree Format).

For best practice, the `.jitf` format should only be used for raw UI integration, as the required resources can be asynchronously called, making ITF based pages load much faster, similar to how webpages work. The rest of the assets should be stored as `.itf` files.
