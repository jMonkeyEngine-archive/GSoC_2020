# jMonkeyEngine - Google Summer of Code 2020 Ideas list

Welcome to the jMonkeyEngine Google Summer of Code [GSoC 2020](https://summerofcode.withgoogle.com/) wiki. This will hold a list of ideas for students.

Everybody planning to participate should read the following,

- [Google FAQ](https://developers.google.com/open-source/gsoc/faq) so you know how GSOC works,
- Join us at [jMonkeyEngine Forum](https://hub.jmonkeyengine.org/)
- You could also join our Discord channel at ** //todo **
- [Here](https://hub.jmonkeyengine.org/g) you can find more about our team.

## Proposed Projects

| Proposal      | Status        | Mentor (Forum Nick / Github Nick) |
| ------------- | ------------- | ------ |
| [Minie Simple Game](#minie-simple-game) | Needs student | [sgold](https://hub.jmonkeyengine.org/u/sgold/summary) / [stephengold](https://github.com/stephengold) |
| [Asset Pipeline Workflow for Blender](#asset-pipeline-workflow-for-blender) | Needs student | [The_Leo](https://hub.jmonkeyengine.org/u/the_leo/summary) / [TehLeo](https://github.com/TehLeo) |
| [Video Playback](#video-playback) | Needs student | [Darkchaos](https://hub.jmonkeyengine.org/u/darkchaos/summary) / [MeFisto94](https://github.com/MeFisto94)  |
| [Improve Shader Node](#improve-shader-node) | Needs student | [Darkchaos](https://hub.jmonkeyengine.org/u/darkchaos/summary) / [MeFisto94](https://github.com/MeFisto94)  |
| [Integrate with Google Play Game Services](#integrate-with-google-play-game-services) | Needs student |  [Darkchaos](https://hub.jmonkeyengine.org/u/darkchaos/summary) / [MeFisto94](https://github.com/MeFisto94) |
| [Mobile Demos](#mobile-demos) | Needs student | [Darkchaos](https://hub.jmonkeyengine.org/u/darkchaos/summary) / [MeFisto94](https://github.com/MeFisto94) |
| [Bring your own idea](#bring-your-own-idea) | |

Students can propose their own idea. Please post you idea in the forum. You can also look at [past project list](GSoC_2014.md) for inspiration. Please note that we are prioritizing ideas that would be maintained even after GSoC.

### General Requirement
Unless otherwise specified, all projects require some hands-on experience and general familiarity with jME3 as well as intermediate to high level of Java knowledge.

## Minie Simple Game

#### Project Description
Minie is the new physics add-on for JMonkeyEngine: https://github.com/stephengold/Minie

Minie includes a few tutorials and a set of simple test/demo apps, but so far no sample games. JMonkeyEngine likewise includes tutorials, tests, and demos, but the closest thing it has to a physics-based game is RollingTheMonkey, which is very simple, less than 500 lines of code: https://github.com/jMonkeyEngine/jmonkeyengine/blob/master/jme3-examples/src/main/java/jme3test/games/RollingTheMonkey.java

#### Expected outcome
A few more elaborate (open-source) sample games (or non-games) written in Java, might help game developers understand how to use Minie effectively and/or inspire them to learn.

A medium-scale game-development effort might also expose shortcomings in Minie or JMonkeyEngine or their documentation, shortcomings we could then remedy. Sample games could also be used to test future releases of Minie and JMonkeyEngine for regressions.

Sample games should follow best practices, including modularity, portability, encapsulation, re-use of existing code, extensibility, view/state separation, user-friendliness, build automation, version control, and thorough testing/documentation.

Students may propose their own game concept(s). Suggestions:
 - Asteroids! In 3-D (https://en.wikipedia.org/wiki/Asteroids_(video_game))
 - battling tops simulation (https://en.wikipedia.org/wiki/Battling_Tops)
 - bowling simulation (https://en.wikipedia.org/wiki/Bowling)
 - claw crane simulation (https://en.wikipedia.org/wiki/Claw_crane)
 - cue sports simulation (https://en.wikipedia.org/wiki/Cue_sports)
 - workbench for designing and simulating a domino show (https://en.wikipedia.org/wiki/Domino_show)
 - miniature golf simulation (https://en.wikipedia.org/wiki/Miniature_golf)
 - piñata simulation (https://en.wikipedia.org/wiki/Pi%C3%B1ata)
 - pinball simulation, either the modern (electric) kind or the old-fashioned (corkboard) kind (https://en.wikipedia.org/wiki/Pinball)
 - workbench for designing and simulating Rube Goldberg machines (https://en.wikipedia.org/wiki/Rube_Goldberg_machine)
 - vehicle racing simulation

#### Skills required/preferred (outline of skills required)

Java programming, Blender 3D, user-interface design, English, analytic geometry, classical mechanics, game design

#### Tests (Students will do one or more of the following tests before contacting the mentors)

// todo

#### Possible mentor

Stephen Gold (sgold@sonic.net, Forum/Hub: @sgold, GitHub: stephengold) also willing to maintain the resulting project(s) if necessary

#### Difficulty of the project

medium

#### Further Reading (links to code, docs and conversations)

//todo

## Asset Pipeline Workflow for Blender

#### Project Description

Blender is an open source 3D software. The goal of this project is for Blender to become our Level Editor. This project focuses on creating an Asset Pipeline between Blender and jME. In simple words, a user creates models and scenes in Blender and with a click of a button they will get converted into j3o files. Ideally, the user's game can also include a refresh button so that immediate feedback is achieved.

Why Blender as Level Editor?
I think plenty of people already understand -> generic level editor -> huge undertaking -> goes nowhere. Now compare that to the amount of effort that is required to make Blender a convenient Level Editor. All that is needed is Asset Pipeline Workflow.

#### Expected outcome

How would it work?
The job of the Asset Pipeline is to effortlessly convert a Blender file into a set of j3o files. To accomplish this the system has to receive as an input: the location of blender file to convert, as well as which Blender objects to convert to j3o's. This information can be presented in a text format, from now on, referred to as 'import script'. Import script defines file locations, which blender objects to convert to j3o objects, which jME materials to use, etc. Alternatively, information with regards to the import process could also be defined in Blender file as User Properties; or a mix of approaches could be used.

Afterwards, Blender Python API can be used to generate temporary glTF files. At this stage, objects that should be shared/use AssetLinkNodes can be handled/noted down.

Finally, the last step is trivial as jME already supports importing glTF files. However, some post import tasks such as applying jME materials and so on can take place.

The overall import process would go through these stages: 
import script → Blender Python API → glTF file/s → .j3o file/s

What has been already done?
Personally, I am already creating a game with the above workflow, I am using a modified version of https://github.com/TehLeo/JmeAssetImporter
and I use class reloading to achieve immediate feedback. However, the above is like a quickly meshed up prototype, also instead of .blender -> glTF -> j3o, it depends on jME BlenderImporter and thus is limited to a specific blender version.

#### Skills required/preferred (outline of skills required)
Java Programming, System Design;
Preferred skills: Capability or willingness to learn basic Blender 3D Python Scripting API

#### Tests (Students will do one or more of the following tests before contacting the mentors)
- Use Blender to generate a simple .gltf file (eg. single cube). Write a console application (without gui/jME canvas) that uses jME AssetManager to load this .gltf file. Now, set the material of the loaded model to Unshaded with Green color. Finally write it back on disk with .j3o file format. 
- To display it, write a jME application that shows the converted green model.

#### Possible mentor
@The_Leo (GitHub: TehLeo); can maintain the project if required

#### Difficulty of the project
Medium

#### Further Reading (links to code, docs and conversations)
https://wiki.jmonkeyengine.org/jme3/beginner/hello_asset.html

## Video Playback

#### Project Description

Playing media/videos in video games is an integral part but hard to use because of the availability of codecs their patents and the required toolset to work with them.
The .webm container format using libvpx (VP8, 9, 10) codecs is what drives the web "HTML 5 Video" and is what Youtube uses.
It's open source and developed by Google. It's also available free of charge (H.264 aka "mp4" is NOT).

As opposed to other solutions I got suggested (using VLC or Java FX), this one would be tightly integrated and (potential flex goal) also work on Android or other embedded platforms where Java FX or VLC Support might be tricky.
One upside of this feature is it guides the student through all phases (see expected outcome)

#### Expected outcome

- Research around libvpx, JNI (libvpx even provides jni bindings already), jME/openGL, Color Spaces etc.
- Design a Video API to generify video playback in jMonkeyEngine, irrelevant of the used codec or display implementation.
- Specifically design:
  - Lockstep (fetch a new video frame every game frame, playback fps depend on game fps)
  - FPS invariant movies (don’t speed down when frames drop, run decoding in own thread and just push textures at a fixed rate)
- Implement the libwebM container parser and vpx decoder according to the interface outlined above
- Unit Testing, Cleanups, Integration similar to jme3-bullet-native (automatic compliation and packaging the native files in a jar)
- From here on stretch goals:
  - Support for Android (Potentially just compile flags)
  - Hardware Acceleration: Conversion from YUV2 -> RGB(A) as ShaderLib/dedicated material (Color Space Conversion on the GPU vs. CPU)
  - Example Shader with some "old TV" style distortion to show how the shaderlib can be used, to prevent re-writing the YUV2->RGB conversion for every shader wanting to display a video
  - Audio Synchronization

#### Skills required/preferred (outline of skills required)

- Knowledge of JNI or C(++), specifically about heap memory management using pointers required
- Knowledge about Multi-Threading mechanisms (e.g. Locks, Thread Safe Queues) required
- Knowledge about Rendering, preferrably OpenGL or jMonkeyEngine preferred
- Knowledge of GLSL, the OpenGL Shading Language, preferred

#### Tests (Students will do one or more of the following tests before contacting the mentors)

- Write a jMonkeyEngine Shader (j3md) and a small contained sample which loads a texture in "YUV888" Format (a "hardcoded" texture is also okay, no need to write a .yuv loader) and converts it to RGB, so the rendered quad looks identical to the imageviewer.

#### Possible mentor

[Darkchaos](https://hub.jmonkeyengine.org/u/darkchaos/summary) / [MeFisto94](https://github.com/MeFisto94)

#### Difficulty of the project

Medium-Hard

#### Further Reading (links to code, docs and conversations)

https://chromium.googlesource.com/webm/bindings/+/refs/heads/master/JNI/  
https://chromium.googlesource.com/webm/libwebm/  
https://chromium.googlesource.com/webm/libvpx/  

## Improve Shader Node (Incubating)

#### Project Description
Replicate PBRLighting/Lighting with Shader Nodes as a starting point for others

From older GSoC idea:
The Shader Nodes system in JME3 is not used a lot. It comes with an editor in the SDK but unfortunately, it’s kind of unstable and needs a lot more work.
Here are the fixes/enhancements that it needs:

- removing a Mat param from a complex condition makes an invalid condition
- Condition custom editor or at least a check from the matparam
- Material property set : remove material parameters (clear button maybe?), display at least texture path in textureEditor (the image if possible) (inplace editor for flip, repeat and so on?)
- Big preview
- Add technique
- Add RenderState?
- Material property set additional render state
- remove output
- default diagram should have at least 1 output for vertex and fragment shader
- Handle MRT in the preview.
- Synchronize previews
- mat param should be explorer nodes and should be editable in the property set (for default value and fixed func binging)
- enable to collapse unmapped material parameters (and save state to metadata)
- possibility to see the shaderNode code
- possibility to edit a shader node code? (if it’s local to the project)
- shaderNodeDefinition wizard
- shaderNodeDefinition editor
- better handling of rendering errors
- test adding node with a sn def local to the project

#### Expected outcome
#### Skills required/preferred (outline of skills required)
#### Tests (Students will do one or more of the following tests before contacting the mentors)
#### Possible mentor
#### Difficulty of the project
#### Further Reading (links to code, docs and conversations)

## Integrate with Google Play Game Services

#### Project Description
Especially for mobile/web games there are a lot of common social features like tracking scores on a leaderboard, comparing achievements, inviting friends to play a game and starting a multiplayer game through match-making.  
Google Play game services provides all of these features, and it is cross-platform (Android, iOS and Web).

Some of those features would greatly benefit from a tight integration with jMonkeyEngine and apart from that having a demo application which shows other devs how to use them is also important.

#### Expected outcome

- Create a sample App which shows all of Play Game Service's features:
  - Create a wrapper around PGS' Save Game Data Features, so they can be used with jMonkeyEngine's [Savable](https://github.com/jMonkeyEngine/jmonkeyengine/blob/master/jme3-core/src/main/java/com/jme3/export/Savable.java) interface
  - Show how Player progress can be tracked and analysed
    - How can this be implemented in code?
    - How does the dashboard look like -> Why is it worth using this feature
  - Show how the player/account management with Leaderboards can be done
  - Anti Piracy by checking the License
  - Video Recording to allow players to share cool scenes with their friends.
  - Nearby Connections to discover nearby players
- Document your findings in our [wiki](https://wiki.jmonkeyengine.org/) as well as commenting your code properly, so that others can take it as an example to build their apps upon.
- Wrap your sample App in a small game, so that the testing process is more enjoyable and you can gather stats from a few more people that way

#### Skills required/preferred (outline of skills required)

- Knowledge of Android App Development (Having worked with Android Studio before) is required:
  - Building an UI
  - Lifecycle of Activities
  - Getting the Android Emulator to work
  - Having an Android Based Smartphone (can't do much without it, sorry)
  - Using ADB to Debug Problems
- Knowledge of Java is required
- Basics of Using Gradle
- Good English Skills to formulate an understandable documentation

#### Tests (Students will do one or more of the following tests before contacting the mentors)

- Build an Android App which shows our default [Blue Quad Example](https://wiki.jmonkeyengine.org/jme3/beginner/hello_simpleapplication.html#code-sample)

#### Possible mentor

[Darkchaos](https://hub.jmonkeyengine.org/u/darkchaos/summary) / [MeFisto94](https://github.com/MeFisto94)

#### Difficulty of the project

With existing Android Development Experience: Simple - Medium

#### Further Reading (links to code, docs and conversations)

 - https://developers.google.com/games/services/

## Mobile Demos

#### Project Description

In order to advance on the market of Android Gaming, jMonkeyEngine needs to have a dedicated app to test all of our common scenaries in a very handy way.
This ensures we can find device specific failures really quick and also show off the engines capabilities on Android.
Rough "Benchmarks" can also be done that way.

We already have a demo app (see below), but it is really simple and uses an outdated way of developing Android Apps (NB Android instead of Android Studio). In addition to that, it has a really simple UX, which could be improved.

#### Expected outcome

- An app ready to be released to the Android Store that fulfills the following requirements:
  - Being developed using Gradle and works with Android Studio after a simple git clone
  - Supports all existing "Tests"/"Examples" (i.e. using some drop-drown field, maybe also with an automatic way of launching each test sequentially and logging exceptions/failures)
  - Specific Android Showcase Scenarios (i.e. neat looking scenes with plenty of effects like fog, bloom, PBR, ...)
- Document/Improve Documentation of the current Workflow for Android:
  - Cross Platform Projects (Android Studio, Run Configurations: On Device, Emulator, Regular Desktop)
  - Problems along the way (Using Proguard, Native Libraries)
  - Integration with the Android Ecosystem (e.g Signing an APK, Profiling/Debugging)
  - Exploring rough limits of devices (e.g. X Verts, Y Draw Calls, Z Texture Memory) for common devices
- Working tightly with the core team to test and fix android related problems.

#### Skills required/preferred (outline of skills required)

- Knowledge of Android App Development (Having worked with Android Studio before) is required:
  - Building an UI
  - Lifecycle of Activities
  - Getting the Android Emulator to work
  - Having an Android Based Smartphone (can't do much without it, sorry)
  - Using ADB to Debug Problems
- Knowledge of Java is required
- Basics of Using Gradle
- Good English Skills to formulate an understandable documentation

#### Tests (Students will do one or more of the following tests before contacting the mentors)

- Build an Android App which shows our default [Blue Quad Example](https://wiki.jmonkeyengine.org/jme3/beginner/hello_simpleapplication.html#code-sample)

#### Possible mentor

[Darkchaos](https://hub.jmonkeyengine.org/u/darkchaos/summary) / [MeFisto94](https://github.com/MeFisto94)

#### Difficulty of the project

With existing Android Development Experience: Simple - Medium
The difficulty for this project is mostly coming from learning the jMonkeyEngine Eco-System and GLSL to fix potential Android/ES only problems.

#### Further Reading (links to code, docs and conversations)

https://github.com/jMonkeyEngine/JmeAndroidDemo  
https://play.google.com/store/apps/details?id=com.jme3.androiddemo (OFFLINE)  

## Bring your own idea
Students can propose their own ideas. Please make sure you have the following contents. You can also look at [past project list](GSoC_2014.md) for inspiration. Please note that we are prioritizing ideas that would be maintained even after GSoC.
