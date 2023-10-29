---
title: "Don’t think, just do: making AI work for me on a new game project"
datePublished: Sat May 20 2023 17:08:37 GMT+0000 (Coordinated Universal Time)
cuid: cllh4zvn8000009k73dxv9ukb
slug: disregarding-a-decade-of-programming-to-make-a-game-with-ai-eccfab31ad4
canonical: https://medium.com/@jschomay/disregarding-a-decade-of-programming-to-make-a-game-with-ai-eccfab31ad4
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692397449580/b2f587bb-ae65-462e-8659-9104dbb1d339.webp
tags: ai, game-development, coding

---

*(Originally published at* [https://medium.com/@jschomay/disregarding-a-decade-of-programming-to-make-a-game-with-ai-eccfab31ad4](https://medium.com/@jschomay/disregarding-a-decade-of-programming-to-make-a-game-with-ai-eccfab31ad4))

I’ve heard the stories of people with little to no programming experience making full games with the help of AI, and I wanted to try that out myself.

I am an experienced programmer and I have made many games in many different tech stacks. Now I want to make a new game in a new tech stack. Usually I would read some tutorials and do some small experiments to learn how to get started. But this time around I’m taking a completely different approach. This time I’m relying on AI… for everything!

I’m going to hold myself back in order give AI a fair chance, but honestly I am skeptical about how far I will get before returning to my usual approach. I hope I am wrong, and if I am, I’ll have to ask myself some difficult questions about my personal and professional workflow moving forward.

I’ll continue to share my experience as it unfolds. For now, I’ve got a plan on what tools to use.

#### The development environment

I love vim. I do all of my work in vim. For me, vim is an extension of my fingers which are an extension of my mind, letting me conjure ideas from thought, like some magical wizard hacker. But for this project, I’ll have to set vim aside.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*NFDcKdH3QtOCV_LaZZ8cng.png align="center")

Don’t get me wrong, I’ve got AI code completion (via [codeium](https://www.codeium.com/)) integrated with my vim setup, and I regularly use ChatGPT-4 as part of my workflow, and I’ve built bespoke AI generation tools to perform tasks I’d have to manually write complex code for in the past. So I’m not an AI-assisted coding newbie.

But this time around I want the full integrated experience, and the tool that often comes up is [Replit](https://replit.com/) with its collaborative AI coding tool called Ghostwriter. The features page looks amazing and I am looking forward to giving it a shot.

The part that I am most curious about is how much heavy lifting the AI “collaborator” will do for me. I plan on using [PyGame](https://www.pygame.org/news) which I have never used before. I am hoping that I can take off running with zero ramp up time. I’m even wondering if I’ll be able to make the whole game without actually learning any PyGame, which is such a foreign concept to me.

The part that I am skeptical about is if I’ll need to take over at some point to fix things, make changes, and organize the code, especially as it grows. I’m sure AI can help with the initial scaffolding, and adding localized functions, but will it be able to continually adjust a growing code base and iteratively add new features?

> I am hoping that I can take off running with zero ramp up time.

What if it works? This is the scary part. Does my workflow and approach to programing change after a decade of doing this by hand? If this goes well, should I ever go back to vim? Will I approach my day job differently? Will my job description change? Will my experience still be valuable?

#### The art assets

I am not an artist. I always struggle to find art for a game, especially since it often involves many iterative changes which can become expensive if I contract an artist.

In the past, I have been able to get pretty far with free or cheap assets on [itch.io](https://itch.io/game-assets). But for this project, I turn to the promise of AI.

I have used AI image generation tools in the past for some of my games, but they often have been limited. I want to reach for more robust tools. Luckily, this game has a limited set of art requirements. It involves 50 or so 2D backgrounds in a dark forest setting. Each background should look unique, and many should have distinguishing content features, but each one should have a cohesive style.

I’ve had my eye on [scenario.gg](http://scenario.gg) ever since it first popped up on Twitter. They have some very impressive demos for making game assets. The cool thing about this tool is that it lets you create your own image generators, which you can then use to make limitless assets that will share a cohesive style or content (I believe they use [DreamBooth](https://dreambooth.github.io/) tech underneath).

![A bunch of generated forest backgrounds that share a consistent style](https://cdn.hashnode.com/res/hashnode/image/upload/v1692393605374/74b7b88e-5aad-43bc-b8ce-d17056a96416.png align="left")

In my case, I don’t have a set of starting images to train a model on. That’s no problem, I have AI to make them for me! Of course, getting a good sample that has the right cohesion from a generalized model is a lot harder and I have had mixed results so far. But the process shows promise

#### Music?

I have even less music talent than art talent. Probably because of this, I tend to forget about music and sound design when starting a game. But I also know that high quality audio can make or break a game, even more so than good visuals.

In the past I’ve been lucky to work with some great sound artists to make custom music and sound effects for my game. I’ve also found good music on itch.io. However, the process can be very involved and time consuming.

I know that a number of AI music and sound generative tools have popped up, and I plan on exploring them, though I must admit that this is an area I haven’t given much thought to yet.

#### Narrative content

Unlike some of my previous games, this game has limited written content, though it does have a narrative ambience from setting and mechanics. Nonetheless, I have considered using AI to generate a sparse narrative as the player comes across each different scene. Because players can navigate through the scenes in any order, AI might be a good choice to make a satisfying narrative that is unique for a single play-though.

I’ve [written extensively](https://jschomay.hashnode.dev/series/inworld-npc-explorations) about my experience of applying AI narrative to a game using [Inworld](https://www.inworld.ai/) and I may use a similar technique, or I might explore other tools.

With that, the pieces are set, and it’s time to see how this experiment plays out. Stay tuned for the next post.