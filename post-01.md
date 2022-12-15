+++
draft = false
title = "Blog"
description = "Blog site description."
sort_by = "date"
paginate_by = 5
template = "blog.html"
page_template = "blog_page.html"
+++

# BYOGE, the tech I will use

![image](https://www.meme-arsenal.com/memes/39851438a88c2b66519fa39046dc746a.jpg)

This will be probably the easiest part. I did a lot of research on tech and usually don't follow trends much in that space.

- Rendering, Input, Audio: I will use Kinc, yes no SDL to be seen here. I won't touch Open GL or any of those. We want to support multiple engines so using one API would limit us to that API. Kinc supports all the API's. Who cares about the rendering API the engine uses ? Well us, we may want to be able to support any rendering API the user uses. How can we do this ? It is quite a feat, but what I resorted to using is a method similar to what Quake2 does, i.e. [polymorphism through dll's](https://fabiensanglard.net/quake2/quake2Polymorphism.php). This will enable us to support an easy way for game engines using BYOGE to load/unload and activate scenes.
- Shaders: We will use Kinc's supplied [runtime shader compiler](https://github.com/Kinc-Samples/RuntimeShaderCompilation-Kinc) and for debugging/developpement Shadered will need to be installed ideally. View it as the external shader editor of choice.
- Coding: We will enable specifying scripts on objects but external editors would be preferred at first. I think having an integrated editor could be doable and viable in the long run.
- External data: For loading models we will use assimp. It's the most fully feature model loader and we can just export simplified model data (vertex/indices/image filepaths). What about the animations you ask ? We can use ozz-animations for that and find a way to simplifie the end output. For audio, we will support wav's/ogg's and support exporting a simplified sequence mechanism using Audaspace.
- UI: I will use Dear Imgui. 
- Level editing tools: We will need to enable easy scene creation like Trenchbroom enables. The goal being to create models based on textures and CSG. Easy kitbashing abilities could also be used like [MAST](https://fertile-soil-productions.itch.io/mast). We also need a way for designers to be able to create instances, 3D Skybox's and terrain like in Source2 Editor.

Now, we need to identify which language and tooling we will use for programming the editor itself. There are a couple of solutions that I invision. The major issue in my case is that a few things are valued for the developpement environnement used. 

- Ease of use: Use tools that enable debugging, that have linting, easy code writing/analyses and have fast iteration times
- Freedom: We need to be able to develop cross-platform
- Speed: the editor needs to be fast for users.

## Solution 1: Haxe/hashlink

Haxe is a C# like programming language with a host of features. One such feature is one of it's VM's i.e. hashlink. Hashlink is a FOSS VM developped by the Haxe foundation and Shiro Games to be used for the indie games it produces. In theory, since speed is important for games the VM should be fast but it's not as fast as V8 or other javascript engines. This solution though has great debugging features included and cross-platform developpement comes out of the box. Iteration times are quite good in my experience. The jit bytecode of the VM can be converted to a C file and compiled natively for better performance. We can integrate C libraries with the VM with multiple exemples online on how to do it.  A couple of projects already exist that could be used to have support for Kinc and Dear Imgui. A gc'ed language would have the advantage of having a low barrier to entry for developpers wanting to participate on the project. 

## Solution 2: Haxe or Typescript/V8

Easily integrate C libraries with exemples. No debugging for now and in the near future. Developpement environnement is favorable and cross-platform. Anyone could participate as javascript/typescript is easy. Iteration times are the fastest a language can be.

## Solution 3: Beef / No VM
Beef is a C# clone but is geared towards game developpers so it's an AOT compiled language that is built to create fast code because games gotta go fast. The developpement environnement is great with a debugger integrated but is Windows only. In the future, I will have a Linux only machine so this is kind of a hindrince but this issue could be anulled by the fact that I can run a Windows VM in the linux machine while using GPU passthrough.  Integrating Kinc will demande an upfront cost of time.

## Solution 4: Luau
Luau is a lua based language that's developped by the Roblox team sheppered by [zeux](https://zeux.io). As such, it's geared towards speed. It's a AOTish in the sense that the luau code is compiled to a bytecode representation to simplify optimization's in the runtime. As it's built around Lua C API integration into a native project is well documented. As the Roblox community has been emancipating from Roblox Studio interesting tooling has emerged in other code editors, most notably vscode. The only thing missing, is debugging. That will take some time to implement but we can base our work on a Lua based debugger that already exists LRDB. For history and more context on Luau, zeux talks more about it's aims and such in his [blog](https://zeux.io/2020/08/02/eight-years-at-roblox/) for the year 2019

If we consider everthing I've said, I think that the conclusion is that I would be better off using Luau. Speed is a major factor and since luau is used for games in Roblox it should be fine for our usecase. Lua and by extension luau can freely share data between C and it's runtime, giving us control over our memory if need be. Having a language that's easy to use but hard to master makes the barrier to entry for participating developpers higher whislt still being somewhat manageable. Not witstanding the upfront initial cost of generating the API for all the libraries used by Luau for BYOGE, all in all I believe it would be a better long-term solution.

There is a lot to do and little time.
