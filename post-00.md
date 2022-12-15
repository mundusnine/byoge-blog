# Why Bring your own Game Engine ?

### TLDR:
I searched for the best game engine, I almost found it, but instead found out that I need to build BYOGE, which isn't a game engine. What will be needed [is](#conclusion--what-are-we-left-with)

## The big search
In my search for the best game engine, I have come to the conclusion that their is no such thing. Why ? Well it's quite simple, trying to use a swiss knife as your only tool to accomplish your basic surviving will work fine in most case's, but if your in antartica, the cold might hinder what your doing and a wooden tool would suffice.

Even though you probably don't know it, your probably using a game engine thats actually hindering your workflow, not simplifing it. Another way of saying it is, your not learning the actual concepts to make games with Unity/Unreal/Godot but actually the minutia of how someone thought it would be good to generalize the way of making games. Do you see the difference ? 

In my research though, I did come into contact with some great contenders. There's this little engine called Source engine and another was the Doom/Quake engines. Why those ? Well in both those case's, there was a great separtion of labor. There was the actual game runtime and the game editor. They only talked to each other with this little concept invented by the Unix OS devs called text files. `"Then why are you whinning on the interweebs ?" ` Because reasons...

## Why not Source 2 ?

Here be reasons, they are my own, do what you will with them. But in short, Source2 as been announced as a futur open source engine... back in 2016. Thanks Gaben for being an engine tease. At this point, and considering how well Source 1 as been maintained by Valve when it was open sourced, I wouldn't hold my breath. You could have access to the engine now, through Chaos Interactive's deal with Valve. But, the issue there is that you have to sign a contract with Valve and that would be fine but it's not futur proof.

So no Source2 source code, can we just use their editor and use their text files in our own engines ? We could, but the file format is closed source and "compiled" by the Editor. Shout out to Source2-viewer, he pretty much implemented a way to do it and showed me that, while doable, it's convoluted in itself. In the end, the editor scene compiler is closed source and will produce files specific to Source2 which is fine but couldn't be used to support a variety of engine's. `"Woooh, we want to support multiple engines now ?"` Apparently.

These facts outlined, I would prefer doing something thats open from the start. That way, it's futur proof, it will be accessible to all and easily integrable for engine makers. By the way, nothing against Valve, they have been really great with their mod support of their games and their work to support FOSS OS's. They are actually one of the game company/store front that I respect the most.

## No Source ? What next ? Quake of Doom maybe ?

In my search's, I stumbled upon other engine's that were greatly moddable. One of those was the early games from Id Tech. Those initial engine's source are available, modders are still making maps and creating new content for these engines. New engines are being built to support the data formats of those games and make raytraced Doom's or Quake's. Why ? Well some fully featured open source level editors and tooling have been developped for these games, which is really interesting in itself. The best tools developped that I had a look at was Trenchbroom. The format of the Quake and Doom game files are well documented and some FOSS libraries are available to parse/load these files. `"We found it, the holy grail !"` Sadly, no.

Those tools are really great. The file formats are good but they don't reflect the needs of the games of today and tommorrow. They are a true testament though that if you design the format well, have good stable tooling and give creators good level design tools, they'll create until there's no tommorrow.

## Conclusion / What are we left with ? 

Ourselves, and one of use needs to make that thing that seems so perfect we can't touch. By the way, it will be a mess.

In short, here's what I found out in my search for the best game engine:

- We need to have a visual tool that enables game designers and visual artists to create worlds easily
- We need an easy file format for programmers to use, or even sidestep easily to make a specified format
- In the end, the only thing we need in the files is filepath's to images/sounds, shader files, vertex/indices data for models and instance id's for models being instanced.

In the next post, I will start to outline what Tech we shall use.