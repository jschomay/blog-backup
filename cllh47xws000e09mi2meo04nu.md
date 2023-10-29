---
title: "Adding Inworld AI Characters to an Existing Game, Part 3: Integration and Analysis"
datePublished: Sat Apr 01 2023 20:57:29 GMT+0000 (Coordinated Universal Time)
cuid: cllh47xws000e09mi2meo04nu
slug: adding-inworld-ai-characters-to-an-existing-game-part-3-integration-and-analysis-826172445e10
canonical: https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-3-integration-and-analysis-826172445e10
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692393626323/be878064-85ae-4fdf-a0e0-73f12bb43737.png
tags: ai, game-development, npc, inworld

---

### AI is in my game now, but is it better?

*(Originally published at* [https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-3-integration-and-analysis-826172445e10](https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-3-integration-and-analysis-826172445e10)*)*

My game now has live AI characters in it. Interacting with these characters directly in the game is novel, fun, and even surprising.

But I can’t help feeling like something is lacking. Do the AI characters add to the game, or detract from it? Or are they simply inconsequential?

In this part of the series on adding AI to an existing game, I share the experience of integrating Inworld characters into my tech stack, and I consider if the result was a success or not, and if it could be better.

Getting trolled by own characters (“Snarky coffee girl” in this case).

### Getting it all connected

I have already created a few [Inworld characters for my game](https://jschomay.hashnode.dev/adding-inworld-ai-characters-to-an-existing-game-part-2-first-words-baf250e0307f). And I have the existing [game code](https://github.com/jschomay/subway-game). In this case, the game is a browser-based game, so all of the code is in JavaScript.

#### Using the Inworld SDK

I followed the [Inworld docs](https://docs.inworld.ai/docs/tutorial-integrations/web/api) for the web SDK. These required setting up an additional node.js server to securely create session tokens. Other than that, the basic process involved:

* Connecting to the Inworld server
    
* Activating the correct scene or character
    
* Sending out messages
    
* Receiving the responses
    

I had a little confusion figuring out how to correctly use scenes, and how they effect switching between characters, but it wasn’t too hard, and the [Inworld Discord](https://discord.com/invite/2jGPwV8g3b) support channel is very active and helpful.

Although the SDK includes audio chat and character emotion states, I did not use those advanced features since this game is mostly text based and I wanted to keep that interface.

#### Integrating with the game engine

As for integrating with my custom engine, I was easily able to add the Inworld character IDs into my engine’s stateful “manifest” of game entities. Not only did this make it simple to “opt-in” to adding AI interactions to some NPCs and not others, it also made it possible to enable or disable this feature on a per character basis at different points in the story.

It also made it simple to swap out IDs during game play as well, which would be helpful for connecting to different “versions” of the same character with different configurations. Or, in my case, the same game entity, “Coffee cart,” has different baristas at different times, so I could swap IDs for these different characters without needing a unique coffee cart entity for each barista.

Inworld has a concept of character goal triggers, and scene triggers. I used these in an attempt to make the characters change how they related to me as the story progressed. I got a less dramatic result than I desired, but I think it could be improved by tweaking my character prompts in Inworld’s studio.

#### Extending the UI

I was able to reuse the existing game views for the additional AI interactions, which not only made integration simpler, but also kept a holistic feeling to the interactions, which was one of my original goals. Both the chat interface and AI responses appear in the same UI as all other narrative content, helping the chat feel like part of the main story.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692393624350/21de65b3-2198-4d4e-a86b-d0892600985b.png align="left")

I had initially considered a [few approaches](https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-1-planning-and-design-57e6a86ffaf0) on where to add AI interaction. I went with the option of adding a “Talk more…” button after the scripted content finished, which enters a free-form chat-like interface with AI generated responses.

This option is only available on certain characters and at certain times that fit with the story. For example, the protagonist mentions that he doesn’t like to talk to the other morning commuters, so interacting with one of them doesn’t offer the “Talk more” option.

### But is it better?

One of my main goals in this experiment was to have the addition of AI make the game and story a better experience without detracting from the original curated content.

> Ultimately, the goal is to make the world feel more alive, but also more interesting and deep, and to add tension to the story.

The characters did indeed feel more “alive.” I must admit that I felt excitement from the unexpected responses in some of my conversations, like when the “snarky coffee girl” trolled me, no matter how hard I tried to get into her good graces.

I definitely felt compelled to forget about the rest of the game for a while, and just keep talking with snarky coffee girl. But I wonder if the novelty would wear off. And worse, I worry that talking with AI characters can become a meta-game that distracts from the actual game experience.

Or perhaps, stopping to have a chat *is* part of the game play. I think this depends greatly on the type of game, and might not work well in my existing game that already has a strong narrative.

This is why I am left with a nagging feeling that I haven’t reached the desired experience. I don’t think this is a shortcoming of Inworld at all. But I think that in this case, I’ll have to get more clever with how I use their tooling to support that narrative that already exists in my game.

> I need to craft my AI characters better, to make their responses prompt the player to feel the emotions and motivations that push the game and story forward.

When done well, I think AI characters can do this more successfully than scripted characters since they are, by design, reactive to a player’s personal experience.

#### Play-testing

Part of the challenge is that I do not really know what players will say to my characters. When I played, I role-played the protagonist character very rigidly, and measured the character responses against the story as I know it is supposed to unfold.

But other players will interact very differently. I need to play-test to see what conversations happen, and design around that. It may be possible that I’ve included AI in the wrong places, or maybe free-chat is the wrong mechanic. For example, it might be better to send background prompts based on the player’s actions and world state and then surfacing the character responses within the scripted narrative some how.

I invite you try out the demo. At this time, only a few characters in the intro have AI.

> [Play-test “Deadline” with the initial AI characters](https://deadline-ai-server.fly.dev/)

If you have feedback, you can use this post’s comments or [tweet me](https://twitter.com/jschomay). Let me know what you think of the AI interactions, and if you’d like to see more of them, or see them work differently. Just a note, I’ll be able to see the content of your chats, but no identifying information.

### What’s next?

In the next post I will dig deeper into exploring ways that AI can enhance game-play beyond just chat bots, and how I might apply that to this game.