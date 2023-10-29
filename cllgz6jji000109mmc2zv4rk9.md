---
title: "Getting lost in the forest"
seoTitle: "Postmortem on Using AI Generative Tools to Create a Forest Maze Game"
seoDescription: "In depth exploration of the generative AI tools, process and pipeline used to make a game.  Includes specific tools like Scenario and Replit Ghostwriter."
datePublished: Fri Aug 18 2023 19:20:25 GMT+0000 (Coordinated Universal Time)
cuid: cllgz6jji000109mmc2zv4rk9
slug: getting-lost-in-the-forest
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690750514628/3275c8e0-4f4d-44eb-8c0c-8c598911ded9.png
tags: ai, game-development, postmortem, ai-tools, generative-ai

---

"Lost" is a simple exploration game where the journey of development was just as interesting as the final play experience. My main goal in making this game was to let AI guide me on everything from code to content. I want to share the process and how it turned out.

## The game

You are lost and must find your way home. Explore the foreboding forest while managing your stats and remembering where you've been. Collect navigation items along the way to help. Enjoy the scenery, but don't get lost!

![Running into a bear while exploring the forest](https://cdn.hashnode.com/res/hashnode/image/upload/v1690752575717/1da105bd-727d-4c23-a932-39ddb6b40ad8.png align="center")

You can play it at [https://enegames.itch.io/lost](https://enegames.itch.io/lost).

This game was intended as an exploration of the theme of a physical solo card game I am working on. I wanted to create a strong abience and try out some ideas that didn't work in the physical version. Unlike the card game, a core mechanic of this game is plotting your way through a mental maze. If you make the wrong step, you might run out of courage.

### Initial design

I wanted to keep this game very simple. At first, I considered doing it in [PICO-8](https://www.lexaloffle.com/pico-8.php), but I wanted to learn [pygame](https://www.pygame.org/docs/) and try out [replit](http://replit.com/). However, I intended to keep the same 8-bit aesthetic of PICO-8 games.

I imagined a series of top-down screens that the player's character would move through, switching from one screen to the next when reaching an edge. This was very much inspired by an impressive PICO-8 game called [Ascent](https://www.lexaloffle.com/bbs/?pid=116846#p).

![Beautiful PICO8 graphics on Ascent](https://img.itch.zone/aW1hZ2UvMTY1ODczOS85Nzc2ODczLmdpZg==/347x500/q4TxiK.gif align="center")

For gameplay, I imagined each scene would have a central encounter that would impact your stats and you would have a choice about how to respond or use resources that you collected to help.

I really liked the idea of a Fog Of War effect to limit what you could see until you were right on top of it, and I particularly liked the idea of linking the size of it to your courage stat. Similarly, I wanted your vigor stat to impact how quickly you could move through each scene.

With all of that in mind, I turned to my AI tools, which immediately changed the aesthetic I had pictured.

## The process

### Assets

I used [Scenario](https://www.scenario.com/) with the intention of training my own model to get consistent custom backgrounds for each screen. I didn't have any graphics to start training with, so I got started by playing around with single-image generation. The prompt I used was:

> pixel art, retro, gloomy, minimalist, dark lighting, dramatic lighting, top-down, 8-bit, game asset, tiles, 4-way intersection of paths meeting in a dark forest

Now my prompt might not have been great, but the AI didn't get the top-down 8-bit style I wanted at all. I realized after a bit that it was because the sample pixel art model I had chosen was strongly trained for a specific look. I got a bunch of nice, but unuseful, images that looked like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691971698718/8d2b9ed1-651c-49c9-b8f7-1eac01837584.png align="center")

I experimented with some different models and prompts and started to see some very cool potential images with a dream-like quality that worked great. The problem was that my favorite ones had an isomorphic diorama style despite my best prompt attempts:

![asset image](https://cdn.cloud.scenario.com/assets/U3PCs8OoQbmiTzl91FHQhw?p=100&Policy=eyJTdGF0ZW1lbnQiOlt7IlJlc291cmNlIjoiaHR0cHM6Ly9jZG4uY2xvdWQuc2NlbmFyaW8uY29tL2Fzc2V0cy9VM1BDczhPb1FibWlUemw5MUZIUWh3P3A9MTAwKiIsIkNvbmRpdGlvbiI6eyJEYXRlTGVzc1RoYW4iOnsiQVdTOkVwb2NoVGltZSI6MTY5MjY2MjM5OX19fV19&Key-Pair-Id=K36FIAB9LE2OLR&Signature=Op1ei5cJ~7E7-BX1rfNh9vzO-ptoBuliNrwwlAdNw9yZvBiCcVivEcmbqzsLVYiy8tdlintlZs4UH-ccmv6sp3sSPMlOHa6Y-z~YujFR~zjXvvevY-LS9bNKr-a~cD7XcbmUrEr4czOi1CgzQnNOyud8GeQjou3~V3ibh4GhoHI1OV8k0MFfzXr1EWL8w7wbu1aL3FgNyZdR9e6DKMS8HAEdDH4wmSQ8EToPXx7lZkCO2PbcuvNEWbiS2I7dyUj174vnjPD6GiT25iLKSIdPw52nJbnIeX80ejgEQFd19puwi3icNmusDZWXihknoZjbdRnoxj0eh5w~SbsZn-QV5A__ align="center")

> 8-bit, pixel art, dark lighting, top down, game tile, dark forest, paths forming a cross, gloomy, mysterious, digital art

I decided to roll with it and changed not only the aesthetic but also the gameplay from a 3rd person avatar to a quasi 1st person POV. <mark>This became a theme: letting the AI guide the direction of the game.</mark> The AI had set a gloomy, glowy, muted yellows and green color pallet that I came to love.

After that, I made a ton more similar images and used them to train a model, and made a ton more from that, both unguided and with specific scenes in mind. Overall a lot of good images came out, but it was very hard to get the specific scenes that I asked for and I probably needed to do a better job with the training data. I experimented with different styles, some working better than others:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691972094747/5ec717b1-c915-4b05-a751-079200b4bd20.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691972124408/32016191-cda9-41b2-a81f-76b33a94728d.png align="center")

I also tried out [Leonardo.ai](https://leonardo.ai/) which gave me some initially better-looking images, albeit without the nice dreamy look from Scenario. I tried training a Scenario model with those images, but it still was too overfit. I also tried Leonardo's custom models which were also hard to control.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691972153832/44cf6a44-fd59-44bf-937a-08620c7c231e.png align="center")

I worried about the images where the isomorphic tile didn't fill the frame. I manually used Leanoardo's in-painting in these cases and was pleased with the results.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691964669626/0e982831-9bfd-438f-a7db-b7fe6b71ceba.png align="center")

In the end, I grabbed a handful of images from both platforms that would work in the game and started coding.

### Code

I hadn't used pygame before, so I relied on Replit's AI, called GhostWriter, to scaffold the main game loop for me. The first thing I wanted to see was how well the images would work with the new perspective, especially the movement. I asked the AI to load a few of my generated background images and move them around with the arrow keys.

Getting immediate feedback between code changes and Replit's browser-based output tab was very helpful. Overall, the effect was good, but I wanted it to be more immersive. I had an idea on how to cheaply fake out depth in the 2D image by zooming in when moving up and vice versa. Here are the results:

![](https://i.postimg.cc/VLRLVG52/pan-vs-zoom.gif align="center")

The image on the left is just panning, while the right image has the described effect. While subtle, I think it makes a huge difference. It also caused a lot of problems, not only in challenges with the code but also in limiting the images that it worked well for.

### Code wrangling

The experience of leaning on AI to write the code was mixed between moments of joy and moments of frustration. Certain things worked out very well while others didn't work at all. I think game dev is especially hard for AI since a lot of it is playing with equations to get the feel right or debugging performance issues. Many times I had to rely on my own knowledge of game dev patterns to get things working right.

For example, I spent a lot of time figuring out the unnecessarily complex AI-generated code for moving the backgrounds around to figure out how to know when reaching the edge of a screen. Even worse, the frame rate dropped to single digits when moving up and I had to rewrite the background moving and scaling code to find the culprit. I wish the AI could have caught it for me, but it would identify potential issues that weren't actually the problem.

On the positive side, the AI wrote some useful code on the first go for several parts. For example, I had the classic issue where moving diagonally moved faster than moving just up/down left/right (because of Pathgoreum's Theorem the speed is 1.4 times as fast). I told the AI to rewrite the movement code to use normalized vectors for consistent speed, which it did just fine.

Another example is even more interesting because not only did the AI design the code, but also the visible output. I explained to the AI that I wanted a grid for the map with dots to show where you have been. It wrote a bunch of code that looked right, but the fun part was running it to see how it looked. It looked great, and I left it exactly how the AI designed it. The same thing happened with the stat bars. I originally pictured them looking much different, but I let the AI code it and checked how it looked and liked it better than what I had in mind.

The last example highlights that theme again of treating the AI as a co-creator and not simply a tool as a means to an end.

### Content

I wanted each screen to have a little blurb and an effect on your stats. I designed a manifest file with the data for each scene that I had, 16 in all to fill the 4 by 4 map grid. I wrote out the declarative scene object as follows:

```json
{
  "filename": "bear.jpg",
  "description": "A massive bear stands tall, its powerful presence filling you with both awe and fear. You tread cautiously, knowing any sudden movement could provoke its fierce wrath. Best not to linger. \n(Courage -2)",
  "stat": "courage",
  "diff": -2
}
```

I then gave it a list of the 15 other background filenames and told it to follow the example and it did. Some of the wording was a bit flowery so I told it to adjust the tone. I also told it that I wanted to have a separate description and stat effect upon discovery and return, and it updated each scene accordingly, adding extra structure to each scene object. In the end, I had 280 lines describing what to say and do for every scene.

## Next steps

I spent a little time exploring AI-generated music. [SoundDraw](https://soundraw.io/) was an impressive tool and I got a soundtrack that felt perfect, but I clicked away and lost it, never to be heard again, which is both sad and beautiful. I think real-time generated music per scene would be more interesting, but I didn't explore that yet.

On that note, generating each scene for every playthrough at playtime would be the ultimate extension of this project. Every playthrough would be unique, no scene would ever be seen twice across games. While the map shuffles each playthrough currently, an entirely new generated map would be much more interesting and more fun. <mark>An infinite maze to explore and survive.</mark>

Technically, I think this is very doable. I can use a finetuned LLM to spit out new scene manifest data on demand, then use the description from those to generate a background from the custom-trained image model with Scenario's API.

For me, exploring all of the generated images, most of which didn't get used, was my favorite part of making this game. I want to have that experience as part of the gameplay. That might very well be my next project.