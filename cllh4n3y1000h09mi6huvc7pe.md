---
title: "Adding Inworld AI Characters to an Existing Game, Part 4: Going Deeper"
datePublished: Thu Apr 20 2023 00:22:05 GMT+0000 (Coordinated Universal Time)
cuid: cllh4n3y1000h09mi6huvc7pe
slug: adding-inworld-ai-characters-to-an-existing-game-part-4-going-deeper-2c9f4f1084c3
canonical: https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-4-going-deeper-2c9f4f1084c3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692393629451/784e2dcd-e1bb-4b67-966c-9f3f8e257cd4.jpeg
tags: ai, game-development, narrativegames, inworld

---

### Getting the most out of AI chat bots

*(Originally posted at* [https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-4-going-deeper-2c9f4f1084c3](https://medium.com/@jschomay/adding-inworld-ai-characters-to-an-existing-game-part-4-going-deeper-2c9f4f1084c3))

Inworld lets you make really interesting AI characters. But interesting AI characters don’t automatically make good game NPCs [as I found out last time](https://jschomay.hashnode.dev/adding-inworld-ai-characters-to-an-existing-game-part-3-5-reflections-trust-and-pigeons-a4db887e1ea1). How can you use AI to enhance your game in a way that only AI can?

There is a whole [exploration of *agentic* AI NPCs](https://www.goodai.com/the-future-of-ai-in-games/) that can understand and manipulate their world and other NPCs around them, and grow and learn. As cool as that is, this article focuses on making *conversational* AI interactions as best as possible.

[Jon Radoff has a great article](https://metavert.substack.com/p/game-designs-for-generative-ai?sd=pf) where he explores his list of “42 elements of fun” in game design through the lens of generative AI.

I found this article very inspirational, and wanted to explore some of its concepts more thoroughly, and how I am using them with specific examples from my game (you can play the [demo here](https://deadline-ai-server.fly.dev/)).

#### Exploring a World

A big part of the fun of playing a game is exploring a new world that is different than your own. World building can be a huge undertaking, but the depth of lore is what makes a game world feel solid and alive. Generative AI promises unlimited content to explore at minimal expense. All the player has to do is ask. But this is not all good.

One common problem is hallucination, when characters make up things that aren’t true or don’t make sense. For example, Carl the coffee cart vendor once gave detailed instructions on how to get from one subway station to another. The problem was that the lines and stations he mentioned do not exist in my fictional subway map! There are measures you can take to avoid this, but it is always a challenge and offers no guarantees. But that is only one problem.

> “The subway system was built by a bunch of different companies and organizations over the years, but the most famous is probably the Interborough Rapid Transit Company, or IRT for short. They were responsible for building the first line, which opened in 1904.” — according to Carl, the coffee cart owner

The bigger problem is *ludo narrative dissonance.* This is what happens when what is going on in the story does not align with what is going on in the game. For example, my protagonist has no interest in the history of the subway, or the politics involved in its construction, or the technical aspects of its maintenance. He just wants to get his promotion at work. And yet, AI NPCs like Carl open the door for a player to literally talk for hours about those topics if they wish. While that type of content might be interesting to the player, it pulls them out of the primary game experience.

I have found that a good way to deal with this problem is to load up the characters with in-game knowledge and prompts like rumors about a suspicious person at a specific station, or potential train delays. This kind of content would make the player curious about what they are foreshadowing, and provoke the player to move in that direction. It adds tension to the game, and gently guides the non-linear narrative, while still allowing the AIs to riff.

I also found that putting interesting things in the game world for players to ask characters about is a good way to make room for lore for players to dig into at their own pace. For example, the broken vending machine has a backstory that foreshadows an important character that arrives later. But I tried to maintain the forward momentum by training Carl to warn the player that they will miss their train if a conversation goes on for too long.

#### Personalized content

The best thing about AI NPCs is that you can say anything you want to them, and they will say something meaningful back. This means every player’s experience will be unique, and they will have played a role in defining their own experience, which makes it personal.

A lot of this comes automatically from how Inworld works, especially how they handle long term memory and shared knowledge. But you could push it even further with custom game hooks that tie into Inworld’s scene triggers or character goals. I’m looking forward to trying their upcoming “intent” feature which should allow for less rigid content hooks.

Humans love sharing a good story, especially about something that only happened to them. I had something interesting happen in one of my recent plays, and I’m dying to share it:

> **Me (to Snarky Coffee Girl):**  
> I have to talk to someone. My boss is super mad at me.

> **Snarky Coffee Girl:**  
> Oh, I’m sure your boss is thrilled with your work ethic. Maybe you should buy them a cup of coffee to make up for it. Just kidding, sorry to hear that. Good luck!

> **Me**:  
> Actually, that’s a good idea, give me your fanciest drink.

> **Snarky Coffee Girl:**  
> Oh, my fanciest drink? That would be a cup of hot water with a tea bag on the side. Enjoy!

> **Me:**  
> Come on, I’m trying to make a good impression here.

> **Snarky Coffee Girl:**  
> Oh, I’m sorry, I didn’t realize your boss was a tea connoisseur. In that case, how about a vanilla latte with extra foam and a sprinkle of cinnamon? That’ll be $5.50.

> *Me:*  
> Yes, do it!

> **Snarky Coffee Girl:**  
> One vanilla latte with extra foam and a sprinkle of cinnamon, coming right up! That’ll be $5.50.

> **Me:**  
> Oh shoot, I gave my last change to the bum. All I have is 5 bucks.

> **Snarky Coffee Girl:**  
> Oh, well isn’t that wonderful. Looks like you’ll have to go beg the bum for some change now. Have a great day!

> **Me (to bum):**  
> I’m sorry man, um, this is awkward, but um, can I have some change? I need 50 cents to pay for my coffee to bring to my boss so he won’t be mad at me.

> **Bum:**  
> Oh, mmmmbbb sure, I can give you some change. I know the feeling of needing to please the boss. Here you go, man. Good luck with that coffee!

> **Me:**  
> Wow, that’s awesome of you! Thanks so much.

> **Bum:**  
> Sssbbble no prmmmmmlem, man. Jjjjjust be careful down here, the rats…they’re everywhere. And the tunnels, you gotta watch out for them. Mmmbbbbye now.

> **Me (to Snarky Coffee Girl):**  
> Guess what? I asked the bum for change, and he gave me fifty cents. Now I can pay for that coffee. What a great guy.

> **Snarky Coffee Girl:**  
> Wow, what a heartwarming story. I’m sure that 50 cents will make all the difference in your life. Here’s your vanilla latte with extra foam and sprinkle of cinnamon. Enjoy it while it lasts!

That scene may or not mean much to you, but I thought it was a great little vignette, and as the game designer, it was awesome to help create some of the story by *playing* the game instead of *making* it! (I’m also pleased with how the bum managed to mumble “no problem,” it was hard to train that.) I’ve mentioned before how AI characters are masters of improv, and this interaction definitely felt like I was a part of an improv skit. I mostly led first part, but the scene turns thanks to Snarky Coffee Girl’s brilliant insight of comedic reversal in asking a bum for change.

The only downside of this kind of interaction is that it happens in a separate layer from the rest of the game engine. For example, I don’t get 50 cents or a fancy coffee in my inventory to actually give to my boss. But I think that is alright. With some extra hard work, and taking some guesses at anticipating player’s actions, it might be possible to really push the envelope by using the Inworld intent system, their game trigger id system to feedback into my rules engine, and some extra generalized rules to make an in-game response to a chat-initiated action. While only a few players would likely experience the fruits of that labor, it would really knock their socks off!

#### “Hidden” content

Many games have achievements for finding hidden content, and mine is no exception. For example, there is a hidden way to get a soda from the broken vending machine. But it would be interesting to make a whole meta-game of hidden topics that only the AI NPCs know about, especially if they thematically support the game or tie in later. The player never knows if they will hit on a topic that goes deep. This was one of the best parts of classic parser interactive fiction games.

I have started doing this by giving characters knowledge of hidden tunnels, ghost stations, and a secret underground cult. All of these become game mechanics much later in the game, but make for interesting speculation from the first scene forward. You can see the bum above mentions it, but he also mentions a lot of other crazy conspiracies. But if you ask Carl about them, he will corroborate the rumors, though he doesn’t believe them.

#### Nurturing

One of the obvious applications of AI NPCs is dating sims. While my game doesn’t have a romantic side plot, it does have a few characters that the protagonist must successfully “court” in order to gain access to the next area. These are usually very static in my scripted content, so this would be a great place to let the AI be the gatekeeper.

For example, at one point the protagonist gets in trouble and has to talk his way out of custody. That conversation could be a good micro relationship arc and would be a great chance to use AI. Other characters show up at different parts of the story, giving the player an opportunity to build up a relationship over time. These relationships could be solely thematic, or they could influence certain game mechanics later. For example, the Girl in Yellow is a mysterious character that disappears when you try to interact with her, but later she becomes an important gatekeeper. It would be fantastic if the things you said each time you see her come up again when she finally confronts you.

Ghost station?

#### Commentary

I’ve always found it interesting how large of a role commentators play in sports. Since I first started thinking about adding AI to my game, I wanted to explore the idea of a commentator who sees what the player is doing and comments on how “well” the player is playing the game, or not. While this might have too much of a “Stanley Parable” vibe, this could manifest as the protagonist thinking to himself in between interactions about what has happened so far, and even what he thinks he ought to do next. I love the idea of making the Player Character also be an NPC!

#### All together now

As I am writing this article, I am realizing that many of these techniques overlap and work well together. As I begin to incorporate them into my game it feels like the process has shifted from world building and character design back to integrated game design, which feels right. I have a lot more to do, and a lot more to discover about getting the most out of my new AI cast, but this is a great start.

You can play the in-progress demo at [https://deadline-ai-server.fly.dev/](https://deadline-ai-server.fly.dev/).