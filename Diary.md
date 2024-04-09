# Learning Unreal

This is a dairy of what I did to learn Unreal. Mainly for my own future reference, but may be more generally useful.

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

Lesson 2 shows how to install and start Unreal Editor
Lesson 3 teaches about the views, navigation and modifying _Actors_ (Unity `GameObjects`)
Lesson 4 shows how to move stuff from project to project, and add stuff from the store.

I'm not quite sure about the difference between `Level`, `Map` and `World`....

## 08-Apr-2024

I'm not sure anything useful can be done with a 2019 i5 MacBook... But it seems to get better after the initial load took forever, we'll see.

I found <https://medium.com/xrpractices/unreal-engine-on-mac-56048e92be4f> which is handy for Mac users.

## 09-Apr-2024

Continued with lesson 5, built my first level from scratch.

Then lesson 6. The lighting model of Unreal is unparalleled. But that shoulnd't interest me:-) Except for the bit near `08:00` where it is explained how to do baked lighting (which is simply flipping a switch for a certain light). Select light, Mobility -> Static.

Lesson 7. Blueprint can sometimes mean "visual scripting language", but sometimes it means something akin to Unity `Prefab`. It actually seems to be a bit of both.

Around `02:00` things get very interesting as we dive into a material. It is itself made up with a blueprint (or something blueprint-like?), which processes all of the parameters to create the material properties. There's some color coding in the view.

> This may be part of how we do point cloud rendering...





 