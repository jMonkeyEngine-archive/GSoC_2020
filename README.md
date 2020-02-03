# jMonkey Engine - Google Summer of Code 2020 Ideas list

Welcome to the jMonkeyEngine Google Summer of Code [GSoC 2020](https://summerofcode.withgoogle.com/) wiki. This will hold a list of ideas for students.

Everybody planning to participate should read the following,

- [Google FAQ](https://developers.google.com/open-source/gsoc/faq) so you know how GSOC works,
- Join us at [jMonkeyEngine Forum](https://hub.jmonkeyengine.org/)
- You could also join our Discord channel at ** //todo **

## Proposed Projects 

| Proposal      | Status        | Mentor |
| ------------- | ------------- | ------ |
| [Minie Simple Game](#minie-simple-game) | Needs student |  sgold            |
| [Asset Pipeline Workflow for Blender](#asset-pipeline-workflow-for-blender) | Needs student |  The_Leo            |
| [Video Playback](#video-playback) | Needs student |  DarkChaos            |
| [Improve Shader Node](#improve-shader-node) | Needs student |  DarkChaos            |
| [Integrate with Google Play game services](#integrate-with-google-play-game-services) | Needs student |  DarkChaos            |
| [Mobile Demos](#mobile-demos) | Needs student |              |
| [Bring your own idea](#bring-your-own-idea) | |

Students can propose their own idea. Please post you idea in the forum. You can also look at [past project list](GSoC_2014.md) for inspiration. 

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
//todo

#### Possible mentor
@The_Leo (GitHub: TehLeo); can maintain the project if required

#### Difficulty of the project
Medium

#### Further Reading (links to code, docs and conversations)

//todo

## Video Playback

#### Project Description
I still didn’t get around to do a full write up on libwebm/libvpx, so I am doing this here in quick bullet points and write it more detailed when/if the idea makes it through:

Story: We all know playing media/videos in Videogames is painful because of codecs, law, etc.
The webm container format using the libvpx (VP8, 9, 10) codecs is what drives the web “HTML 5 VIdeo”, what Youtube uses, etc. It’s open source and developed by google. It’s also available free of charge (I think there is confusion with X264 vs. H.264 there).

As opposed to other solutions I got suggested (using VLC or JavaFX), this one would be tightly integrated and potential (flex goal) also work on Android.

One upside of this feature is it guides the student through all phases:

#### Expected outcome

Research around libvpx, JNI (they even provide bindings already), jME/openGL, Color Spaces etc.
Design a Video API to maybe make it into core. There I’ll need paul’s help and we have to see if we can get away with a quad [or anything generic] and just a control.
Still we need to design multiple things: a) Lockstep [fetch a new frame every frame] b) fps invariant movies [don’t speed down when frames drop, run decoding in own thread and just push textures locked]
Implement libwebM Parser and vpx decoder according to the interface in 2
Test, Cleanups, Integrate like jme3-bullet-native (automatic compliation and packaging the native files in a jar)
From here on stretch goals:
Android. HW Accel? Conversion YUV2 -> RGB(A) as ShaderLib/dedicated material.
Example Shader with some “old TV” style distortion to show of how the shader lib can be used, to prevent re-writing the YUV2->RGB conversion.
Audio and synchronization!

#### Skills required/preferred (outline of skills required)
//todo
#### Tests (Students will do one or more of the following tests before contacting the mentors)
//todo
#### Possible mentor
DarkChaos
#### Difficulty of the project
Medium-Hard
#### Further Reading (links to code, docs and conversations)
//todo

## Improve Shader Node

#### Project Description
Replicate PBRLighting/Lighting with Shader Nodes as a starting point for others

From older GSoC idea:
The Shader Nodes system in JME3 is not used a lot. It comes with an editor in the SDK but unfortunately, it’s kind of unstable and needs a lot more work.
Here are the fixes/enhancements that it needs :
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

## Integrate with Google Play game services

#### Project Description
Especially for mobile/web games there are a lot of common social features like tracking scores on a leaderboard, comparing achievements, inviting friends to play a game and starting a multiplayer game through match-making. Google Play game services provides all of these features, and it is cross-platform (Android, iOS and Web), so it would be a good place to start.

Primary goal: Create a demo for fully functional achievements working across Android and iOS.

#### Expected outcome
#### Skills required/preferred (outline of skills required)
#### Tests (Students will do one or more of the following tests before contacting the mentors)
#### Possible mentor
#### Difficulty of the project
#### Further Reading (links to code, docs and conversations)
 - https://developers.google.com/games/services/

## Mobile Demos
#### Project Description
We have a demo app for Android, but its test scenes are outdated and we’ve now added iOS to our supported platforms.

There should be a common “Mobile Demos” app with:
- Tests optimized for mobile.
- Apps made for both Android and iOS
#### Expected outcome
#### Skills required/preferred (outline of skills required)
#### Tests (Students will do one or more of the following tests before contacting the mentors)
#### Possible mentor
#### Difficulty of the project
#### Further Reading (links to code, docs and conversations)
https://play.google.com/store/apps/details?id=com.jme3.androiddemo

## Bring your own idea
Students can propose their own ideas. Please make sure you have the following contents.

#### Project Description
#### Expected outcome
#### Skills required/preferred (outline of skills required)
#### Tests (Students will do one or more of the following tests before contacting the mentors)
#### Possible mentor
#### Difficulty of the project
#### Further Reading (links to code, docs and conversations)
