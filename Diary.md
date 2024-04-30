# Learning Unreal

This is a dairy of what I did to learn Unreal. Mainly for my own future reference, but may be more generally useful.

The primary goal is not to become a full-blown Unreal developer, but to find out what I need to know to port `cwipc` to Unreal. First and foremost the reception/decode/render part of the pipeline, which is going to be needed for the Transmixr performance use case, but I will also keep an eye on the capture/encode/transmission part of the pipeline.

## 07-Apr-2024

Registered an epic account. Pick a memorable password, you'll have to type it in many times and Keychain or so won't help you.

Downloaded the Epic Games Launcher (on both a Mac and Win11 machine). It's big. Downloaded and installed the latest Unreal Engine (5.3), which is gigantic. This turned out to be a mistake, see below.

Started with the course "Your First Hour in Unreal Engine 5.2". This has a lot of videos with _very_ high information density. Watch it on a second computer.
Downloaded the "Course Material" and tried to open it in Unreal Engine. Second mistake.

Just start following the course videos, you will be told what to download when, and from where. Then you'll download (as of this writing) Unreal Engine 5.2 (not 5.3), and moreover you'll be shown a few options on how to make the download significantly smaller.

### Learned so far

- The Viewport (editor main view) is similar to the Unity Scene View
- The Outliner is similar to the Unity Hierarchy View.
- The Details is similar to the Unity Inspector
- The Content Drawer is similar to the Project view, but it also allows import/export and many more things.
- Here's a terminology list from the documentation: <https://dev.epicgames.com/documentation/en-us/unreal-engine/unreal-engine-terminology>

Lesson 2 shows how to install and start Unreal Editor
Lesson 3 teaches about the views, navigation and modifying _Actors_ (Unity `GameObjects`)
Lesson 4 shows how to move stuff from project to project, and add stuff from the store.

I'm not quite sure about the difference between `Level`, `Map` and `World`.... **Update:** I am now (after reading the terminology doc). A world is a container of levels, and level and map are synonyms.

## 08-Apr-2024

I'm not sure anything useful can be done with a 2019 i5 MacBook... But it seems to get better after the initial load took forever, we'll see.

I found <https://medium.com/xrpractices/unreal-engine-on-mac-56048e92be4f> which is handy for Mac users.

## 09-Apr-2024

Continued with lesson 5, built my first level from scratch.

Then lesson 6. The lighting model of Unreal is unparalleled. But that shoulnd't interest me:-) Except for the bit near `08:00` where it is explained how to do baked lighting (which is simply flipping a switch for a certain light). Select light, Mobility -> Static.

Lesson 7. Blueprint can sometimes mean "visual scripting language", but sometimes it means something akin to Unity `Prefab`. It actually seems to be a bit of both.

Around `02:00` things get very interesting as we dive into a material. It is itself made up with a blueprint (or something blueprint-like?), which processes all of the parameters to create the material properties. There's some color coding in the view.

> This may be part of how we do point cloud rendering...

> Also, in the uc-performance call it was mentioned that Unreal materials and (maybe?) shader survive round-tripping via USD, which may be interesting to the point cloud implementation.

Happened to come across <https://github.com/ibbles/LearningUnrealEngine> which fits my brain.

Also found <https://github.com/MOZGIII/ue5-gitignore> which may come in handy when moving Unreal projects to git. But maybe this isn't the best: it seems to be really geared towards a repo with a single Unreal project. And it ignores everything it doesn't know about (such as this Diary, or the toplevel readme). For now I'll start with a `.gitattributes` based on the info there and my Unity one. 

Here's the links at the end of the course, for continued learning:

<https://dev.epicgames.com/community/unreal-engine/learning?types=course>

<https://dev.epicgames.com/documentation/en-us/unreal-engine/understanding-the-basics-of-unreal-engine>

### Learned so far

- A laptop screen is really too small. You can see the scene, the outliner and the details at the same time, but with very little space on the latter two.
- If you open a view on a blueprint (for example) the Viewport disappears. My ADHD immedeately makes me forget what I was doing in the first place:-)
- Packaging (called building in Unity) takes an inordinate amount of time (almost half an hour on `beelzebub`). But the next time packaging to the same output location is pretty quick (1-2 minutes).

## 19-Apr-2024
 
I'm bad at diaries, adding this entry after the fact.
 
Started on _Blueprint Communication_ lesson, <https://dev.epicgames.com/community/learning/courses/LWv/unreal-engine-blueprint-communication/ypKl/unreal-engine-blueprint-communication-overview>.
 
Quick deep-dive into Blueprint scripting. And how best to structure your scripts, with examples. 
 
### Learned so far
 
- BP has all the inheritance and stuff from normal programming languages. It looks a bit like control flow plus data flow ombined (but maybe its only control flow?).
- The interface is very busy, and sometimes it isn't obvious how to create something, for example a call to a base class method.
- Some stuff is in the `Class` tab, and it isn't always obvious what is where.
- Aside from calls there are also events, event handlers and event dispatchers. This was very unclear to me for a long time, until I realized that every BP "pipeline" (unsure what the correct term is) is really just a C++ method in disguise. That also explains why you have to create the events and event dispatchers and all that.

## 21-Apr-2024
 
Continued with BP communication. Thenwanted to know a bit about debugging and found the course _Blueprint Debugging_, <https://dev.epicgames.com/community/learning/courses/VdA/unreal-engine-blueprint-debugging/xnmJ/unreal-engine-blueprint-debugging-overview>.
 
## Learned so far
 
The debugger is nifty, at least if you can run your BP in isolation (unsure if it works otherwise). But you're debugging the _class_, and you have to select the _instance_ in the top-right menu before you see all the control flow visualization.
 
When your mouse is captured by the preview player you can get it back with `shift-F1`.
 
## 28-Apr-2024

Decided to start looking at point cloud support. Found the Lidar Point Cloud plugin (from Unreal themselves) and <https://github.com/ValentinKraft/UE4_GPUPointCloudRenderer>.

Both are UE4 only. The ValentinKraft one has comments that someone tried a port to UE5 and failed. But it does look more promising from the description that it seems to be able to handle dynamic point clouds.

But let's start with the Lidar one. Installed UE4, the Lidar plugin and the example.

UE4 looks quite different from UE5. Found the point cloud actor, which seems to be the thing rendering. Tried to find out how it is controlled, for example how the sliders that change point size in demo `3.1` work.

## Learned so far

- I don't know how to navigate by object. For example, I presume there's a BP somewhere that changes `BP_DemoDisplay8.PC_Demo.Appearance.PointSize` if the value of the slider is changed. I had expected to be able to select the object, and then do _Find References in Scene_ or something like that. Can't find it.
- Inspected the slider also (it's blueprints). I don't understand how it works together. There must be a blueprint somwhere that I can't find.

## 30-Apr-2024

Decided I should first learn about creating C++ plugins in general before looking at the PointCloudPlugin I found yesterday. Got started with _Unreal Engine C++ Tutorial: Plugins_, from <https://www.youtube.com/watch?v=mgFrFdzb7hg>.

Needed to install Visucla Studio 2017, omg...

Got the plugin to work, any components inside it will always face the player (by auto-rotating).

Also copied the plugin over to yesterdays Pointcloud tutorial code, and used it to have one of the pointclouds always face you.

Next step is trying to see if I can add my own methods and attributes, and if I can see these from BP.

### Learned so far

- The Visual Studio solution contains **all** the source code, so also for the Lidar Point Cloud plugin I installed yesterday.
- The tutorial goes _very_ fast. For example, the fact that I had to add my new class to the _plugin_ and not to the _project_ I overlooked the first time around.
- Got an error `Pointer to Incomplete class is not allowed`. Seems to be common. Solution is here: <https://forums.unrealengine.com/t/pointer-to-incomplete-class-type-is-not-allowed/399262/2>.
Generally, I think the issue is that you have to know which include file to use where the class is actually fully declared. `GameFramework` is a good place to start looking.
- The end of the tutorial explains how to copy plugins from one UE project to another. Very helpful!