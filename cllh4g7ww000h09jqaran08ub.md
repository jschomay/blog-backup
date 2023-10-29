---
title: "Adding Inworld AI Characters to an Existing Game, Part 3.5: Reflections, Trust, and Pigeons"
datePublished: Sat Apr 08 2023 23:32:31 GMT+0000 (Coordinated Universal Time)
cuid: cllh4g7ww000h09jqaran08ub
slug: adding-inworld-ai-characters-to-an-existing-game-part-3-5-reflections-trust-and-pigeons-a4db887e1ea1
canonical: https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-3-5-reflections-trust-and-pigeons-a4db887e1ea1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692393635249/92494b04-c10d-4b2a-9abd-9bce73757ab1.png
tags: ai, game-development, narrativegames, inworld

---

*(originally posted at* [https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-3-5-reflections-trust-and-pigeons-a4db887e1ea1](https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-3-5-reflections-trust-and-pigeons-a4db887e1ea1))

## What I learned from my players and my characters

> “Giving infinite dialog agency to the player in a controlled story is a frightening thing!”

Last week I released a [demo](https://deadline-ai-server.fly.dev/) of the new AI characters in my narrative game. One of my favorite things to do now is reading the (anonymized) transcripts from players interacting with these AI characters.

In my [previous article](https://jschomay.hashnode.dev/adding-inworld-ai-characters-to-an-existing-game-part-3-integration-and-analysis-826172445e10), I had left feeling lukewarm about this experiment. Specifically, I was concerned with the free-form AI chat detracting from the tightly scripted main narrative and game experience. However, I’ve had a chance to reflect and get feedback, and now I’m feeling more enthusiastic. In this bonus developer diary I want to share what I learned and how my view changed.

In one interaction, the player asked Carl (the friendly subway station coffee vendor) if he had seen anything strange going on. Carl said he hadn’t lately, but one time he saw a pigeon fly into the subway and cause a bunch of chaos! What a lovely little anecdote for the player.

More importantly, it is one I never would have written myself. And Carl probably won’t share it with any other players again. It was unique for that particular player, and even better, that player collaborated in telling the story, making it more personal and meaningful. That kind of interaction is an elusive holy grail in content-driven game design. And that is the true promise and power that generative AI offers.

In another case, a more devious player was having fun trying to “break” Carl. Despite his protests, they eventually managed to coerce him into serving them 100 cups of coffee! Then, they faked a heart attack and poor Carl had to improvise in the subway setting to seek emergency assistance (which he did rather well). It was quite tense for a bit, and the player and Carl managed to laugh about afterwards.

Only one player was directly inappropriate. I was so proud of Carl, who, instead of the default AI safety-control response (usually like, “I’m uncomfortable talking about that, let’s talk about something else”), managed to stay in-character to defuse and redirect the conversation, even across multiple uncomfortable interactions.

I never tire of watching Snarky Coffee Girl relentlessly troll players, no matter how hard they try to outdo her. Once, she slipped up in some kind of AI safety over-correction bug that made her announce that she was a “virtual assistant.” When the player asked if she really just admitted to being a virtual assistant, she just rolled with it, saying “No, I’m a figment of your imagination. Of course, I’m a virtual assistant. Do try to keep up, will ya?” I was laughing out loud, and I imagine the player was too.

I had such a good time reading the transcripts, that I was reassured the players must have been enjoying the experience just as much. These example interactions, and many others, showed me that **AI characters are masters of improv.** Watching my characters, out in the wild, managing on their own, taught me an important lesson.

#### Trust

Although my characters sometimes faltered, or said the wrong things, or spoke nonsense, for the most part they did just fine, and frequently pleasantly surprised me. As a game designer in this new world of generative AI, my job is to design the characters as well as possible, and then trust that they will help carry the game.

It’s almost impossible not to anthropomorphize my characters. I know that they are nothing more then LLMs and prompt engineering, and each interaction is running binary data through a model to complete a string of text word by word. But none of that really matters. Functionally, I need to trust them, in the very same way I would trust trained improv actors that I hire to entertain an audience.

I also learned to trust the players. At first I didn’t know what players would say to my characters. Now I do. Most played the part of the protagonist character, conversing about what they have seen and experienced so far. Many simply asked, “How’s it going?” A few were more interested in peering behind the curtain and exploring the mechanical workings and limits.

In the end, I realized that it didn’t matter what players said. The players that role-played likely had a great time. The players that probed the dark corners, trying to break things, probably had a good time too. Ultimately, with or without AI, the game happens, not on the screen, and not in the script, but in the player’s mind, and they will enjoy it however they want.

#### Prompting… the player

While I am pleased that players are enjoying their experience, I still want to use the AI characters as optimally as possible. I have some directions to pursue to achieve that.

This whole time I’ve been concerned with trying to make better AI character prompts. And while that is important, it is equally, or even more important to prompt the player. Everything in a game is a cue, a little nudge, to spark the player’s curiosity, to go check it out, and to progress in the direction you want them to go. So how do you prompt the player?

One way is with rich content. In a primarily text based game like mine, the static content creates a framework of context for the player to reference. In my case, this includes all written text, but also, everything available to discover in a location, like my broken vending machine. I was somewhat surprised to find quite a few players asking Carl about it. Even though I didn’t design Carl to know that the vending machine was there, the context of the conversation was sufficient for him to reply along the lines of how the subway maintenance has been falling behind. This is perfect, because it foreshadows everything that is about to happen to the player. (The broken vending machine is a metaphor? Wow! Thanks, Carl!) Which gets to the next point.

The second important place to prompt the player is directly in the conversations they have with the AI characters. Their responses should make the player even more curious, and even more eager to press forward. But, how do you do that when you don’t directly control what the characters will say. How do you trust your characters?

#### Giving the tools to thrive

It is a very strange thing to trust an algorithm. I trust Google Maps, and to some extent, self driving cars, but this is different. This is a facsimile of a living, thinking, intelligent entity. You have no way of knowing how it might react to a given situation, yet its response is so important. How do you trust something that is, by design, nondeterministic?

![The intersection of 1) interesting characters, 2) good character design, and 3) shared knowledge](https://cdn.hashnode.com/res/hashnode/image/upload/v1692393632865/3a0fb31f-26ba-43dd-a0f6-2f1d1171a66e.png align="left")

How to trust your characters

I found that the best AI characters came from the most interesting characters to begin with. Snarky Coffee Girl has minimal design behind her, but she plays her role superbly. I tried to make another commuter in the station. She is pretty bland, and serves more to show the player that the protagonist prefers to keep to himself. When I tried to add AI for her, she was really generic and even annoying. So it goes to show how even minor characters should be interesting. This is true in game design as well as in TV and film. As [beloved screenwriting guru Blake Snyder](https://savethecat.com/products/books/save-the-cat-the-last-book-on-screenwriting-youll-ever-need) advises, “give every character a limp and an eye patch.”

Once you have an interesting character, Inworld offers a whole suite of tools to direct how they respond. I’m still figuring out how to best use it all. Beyond turning all of the dials and knobs to get the right personality and tone of voice, I’m starting to learn that orienting each character’s place in the game is critical. For each character, ask why they are in the game and what they bring to it. You can probably tell that I already had a good answer to these questions when I initially designed the scripted interactions and narrative. Now, I’m learning to pull that into the Inworld system too. For example, I tweaked Carl to warn lingering players not to miss their train, and to encourage them to stand up for themselves if they mentioned their boss. As more events start to unfold, other characters should have opportunities to worry about (and therefore talk about) very in-game concerns. In some cases, this might require carving back some of the scripted narrative to leave some unanswered questions for the player to ask about.

Of course, your characters can’t talk about in-game things if they don’t know about them. I mentioned the broken vending machine earlier, and how Carl didn’t know about it. I plan to go back and add everything observable in the scene to the characters’ knowledge. It reminds me of how you would have to add [all of the nouns in old school interactive fiction](https://intfiction.org/t/craft-parser-if-and-nouns/57451/2) games to the world model to avoid embarrassing errors when the player asks about something they read about, but the author forgot to define it. Luckily, generative AI will just spout out what ever comes naturally. It’s still surprising to me to never see a character say, “Uh, I don’t know about that.” This trait is pretty sweet, but you lose control of that opportunity to prompt the player if the character doesn’t have the appropriate context. Luckily, Inworld offers a number of ways to make your characters aware of things.

For each character, you can define common knowledge, private knowledge, and scene events. I’m still working out what combination of these work best, but the idea is that character conversations will be more rooted in the game world. For example, I look forward to seeing conversations with Carl where he brings up fun anecdotes about the broken vending machine in the corner. If the player hasn’t checked it out yet, they likely will after Carl mentions it. Better yet, maybe I hint to Carl that it broke because the Skater Dude was trying to steal from it. The protagonist character mentions earlier how much he hates rule-breakers like Skater Dude (who plays a big role later in the game), so this would be great contextual fodder for Carl to draw from.

And the rest is trust.

#### Next

In the next article, I’ll get back to the scheduled plan of more deeply exploring ways to successfully integrate AI characters into games. And in the meantime, I’ll be improving and adding characters to my game!