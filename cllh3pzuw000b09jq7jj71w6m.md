---
title: "Adding Inworld AI Characters to an Existing Game, Part 1: Planning and Design"
datePublished: Mon Feb 27 2023 13:20:16 GMT+0000 (Coordinated Universal Time)
cuid: cllh3pzuw000b09jq7jj71w6m
slug: adding-inworld-ai-characters-to-an-existing-game-part-1-planning-and-design-57e6a86ffaf0
canonical: https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-1-planning-and-design-57e6a86ffaf0
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692393619993/5f683c54-288a-4fb2-a8df-ca5504f10f20.png
tags: ai, game-development, narrativegames, ai-tools, inworld

---

*(Originally published at* [*https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-1-planning-and-design-57e6a86ffaf0*](https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-1-planning-and-design-57e6a86ffaf0)*)*

As a game developer and narrative designer, I’m always looking for ways to make my games more engaging and immersive. Recently, I had an idea to take one of my old narrative games and add AI NPC characters to it using Inworld. In this developer diary, I’ll walk through my planning and design process for this experiment.

This is the start of a series of articles that follow my journey. You can see all articles in the series at [https://jschomay.hashnode.dev/series/inworld-npc-explorations](https://jschomay.hashnode.dev/series/inworld-npc-explorations).

### What is Inworld?

[Inworld](https://www.inworld.ai/) is a platform that lets creators easily build AI-backed characters by providing a personality, goals, and a knowledge base. They offer integrations with game frameworks to add these characters to your game.

### What is “Deadline?”

Two of my favorite movies are “[Subway](https://www.imdb.com/title/tt0090095/)” and “[Kontrol](https://www.imdb.com/title/tt0373981).” A while  
back, my friend told me that I should make a video game like those films.  
[“Deadline” is that game](https://enegames.itch.io/deadline).

<iframe src="https://www.youtube.com/embed/RYBcEXNLH7g?feature=oembed" width="700" height="393"></iframe>

Welcome to the subway

“Deadline” is a narrative-heavy game with minimal visuals, map-based navigation, a central story to explore with a few side plots, and many oddball denizens of the subterranean labyrinth. In that way, it is a little bit like “Kentucky Route Zero.”

> The goal of this experiment is to make those oddball denizens into AI-controlled oddball denizens… without losing control over the plot!

### Challenges of Adding AI into an Existing Game

Making a non-linear narrative game is already difficult enough, but adding AI to it has a number of additional complications to consider.

#### Generated vs. Scripted Content

In “Deadline” the player can see a list of NPC characters and items in each scene, and can select one to interact with, such as the “Coffee cart” in the opening scene.

Items and NPCs in the first station in “Deadline” for the player to interact with

This brings up a context-aware dialog box that usually includes a description of what happens and some dialog, both for the player’s character and the NPC.

![Example of a dialog box in “Deadline”](https://cdn.hashnode.com/res/hashnode/image/upload/v1692393617557/d88097c1-faae-4ea8-912b-7560ca9748b3.png align="left")

Interacting with the “Coffee Cart” brings up this dialog box

With the power of generative AI, it would be nice to create AI characters that have enough information to allow the player ask the right questions to move forward in the game. This could make for a very unique and interesting experience, and puts the player more in the driver’s seat, by making them think harder about what to ask, similar to old-school command line text adventure games.

On the other hand, I have lots of fun scripted content that I’d like players to come across. Also, pure generated content makes it technically much harder to trigger narrative rules that change the world state or unlock more content.

I could imagine a hybrid approach where narrative-significant interactions are scripted, while innocuous interactions use generated content so players can ask their own questions. But giving the player free rein some of the time, but not all of the time might actually make the game feel more railroaded. Plus some of my favorite scripted dialog moments happen in the minor interactions.

Another idea is on every interaction to let the player choose between advancing the story via the scripted content, or having an unscripted side conversation with an NPC. But this approach may also break the flow of the game by essentially having two ways to play it.

Furthermore, with a hybrid approach I’d have to carefully make the AI generated content match the voice and tone of the scripted content, which might not always be easy.

#### UI

The UI will need to change to accommodate the approach taken above. I can imagine a few approaches:

* Placing an input field at the end of each dialog box’s content for the player to type in prompts if they want to dig deeper.
    
* Offering a choice between one (or more) truncated scripted options and an input field for the player to supply their own prompt, and changing what displays next based on which option they chose.
    
* Adding a “chat” icon next to each NPC listed in the scene to activate free-form chat, and also keeping the original UI of clicking on the NPC name to trigger the scripted content.
    

Of these, I like the first option best because it feels the least intrusive, doesn’t preclude scripted content, and allows the player to interact further in a more free-form manner at a moment when they have the most new information.

#### Consistency

If one NPC is AI-backed, do all NPCs need that functionality? Does it break the fourth wall too much if players wonder why they can interact with one NPC but not another?

Adding AI to every character gets expensive and hard to manage. It also seems undesirable in many cases. For example, in the first scene, the player can say a quick hello to another character waiting for the same train to arrive. If the character tries to interact with that character again, the player’s character says “I think one hello is enough when talking to complete strangers.” This sets some bounds to the game, but more importantly conveys information about the player character’s personality. Allowing the player to then enter free-form chat mode with this character would break the constructs of the story.

I am hoping that selectively applying AI will feel natural without causing AI vs non-AI characters stick out like sore thumbs. I expect the choice of UI could help smooth this inconsistency and the narrative design could also make the presence or absence of free-form chat intuitive.

#### Staying “on Script”

One of the challenges of adding AI characters, is making sure they stick to talking about what they should know. Ideally they will be able to drive the plot forward and add texture and even foreshadowing. But if they go off the rails (sorry, couldn’t pass up on the pun), it could cause a lot of confusion for the player. Also, the player might ask things that don’t make sense, either on purpose or by accident, so I need a good strategy for dealing with those cases.

> Ultimately, the goal with adding AI characters is to make the world feel more alive, but also more interesting and deep, and to add tension to the story.

Inworld should be pretty good at keeping NPCs on script, but I have a few questions. For example, is there a way to change a character’s knowledge base over time? And if so, does each character “instance” across games have its own knowledge base? I need to explore this further, but I think each character might be a single entity that has a single source of knowledge, regardless of how many people are interacting with it. If that is the case, I might need to get clever with adding prompt prefixes to what the player writes to “direct” the character, though I’m not sure how well that would work. I think this is one of the big challenges game developers face when introducing AI that can be unpredictable.

### Conclusions and Next Steps

This experiment presents a unique set of challenges and unknowns, but I’m excited to dive in and see what happens. I’ll do some more research and pick a small spot to start with, perhaps Carl the coffee cart guy in the first scene. In the next part, I’ll cover some of the more technical aspects of integrating Inworld AI characters into my existing game framework.

Disclaimer: ChatGPT helped turn my rough outline into prose, which I then edited further into this final form.