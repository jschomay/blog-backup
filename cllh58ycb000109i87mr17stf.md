---
title: "Observations on using Replit’s AI coding tool from an experienced coder"
datePublished: Sun Jun 04 2023 22:17:32 GMT+0000 (Coordinated Universal Time)
cuid: cllh58ycb000109i87mr17stf
slug: observations-on-using-replits-ai-coding-tool-from-an-experienced-coder-3dd7d0146401
canonical: https://medium.com/@jschomay/observations-on-using-replits-ai-coding-tool-from-an-experienced-coder-3dd7d0146401
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698591751443/e04e603b-fba8-499f-b0ab-0591ceeed869.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692397482827/ef087931-cd10-4ddc-a1d6-d1adfa3a73c3.webp
tags: ai, pair-programming, coding, replit, ai-tools

---

*(Originally posted on* [https://medium.com/@jschomay/observations-on-using-replits-ai-coding-tool-from-an-experienced-coder-3dd7d0146401](https://medium.com/@jschomay/observations-on-using-replits-ai-coding-tool-from-an-experienced-coder-3dd7d0146401))

I used [Replit](http://replit.com/) and their AI “pair programming” service called GhostWriter on a new game project recently. This is my experience.

I had three goals when leaning on the AI:

1. *Instantly go from zero to something interesting on the screen.*
    
2. *Add features without ever referencing any docs, tutorials or Stack Overflow.*
    
3. *Avoid making coding decisions based on my own experience with game dev patterns and general coding patterns.*
    

I should say that I am an experienced programmer, and have made games on multiple tech stacks before, however, this project was in a new stack for me, specifically Python and pygame. The game was relatively simple, involving 2D, top-down, fog-of-war style movement in a minimal design with heavy ambiance, with game play as a mix of stat and resource management and maze solving. (A write-up on the game will follow soon.)

I’ll only talk about the interactions with the AI and not the rest of what Replit offers, though I did enjoy the zero-setup and instant hosted feedback loop, which made iterating with the AI possible.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*MMnuN6Iosqi2qAkP_HhE9A.png align="center")

*Move over, I’ll drive*

At first, I wasn’t sure this process was better than my usual workflow. But after working with it more, I decided it was. Although not everything worked as well as I had hoped, I got to a functioning game without the lead time I usually need to put in learning new tools.

Plus it was just fun, simply asking for what I wanted to happen and having it appear. I would sum up the while experience by saying that it felt like the Top Gun quote:

> <mark>“Don’t think, just&nbsp;do.”</mark>

Replit offers 4 AI tools: “generate”, “transform”, “explain”, and “chat.” I found “chat” to work the best and used that 99% of the time. I liked how “generate” was more embedded in the editor, but it didn’t seem to have the context of the rest of the code and would spit out generic coding solutions completely unrelated to pygame. The same was true for “transform” and even “explain” which is a shame because “transform” seemed like a power tool. The best part about “chat” was how it knew about the different files and classes I had and could make cross-cutting suggestions, refactors and explanations.

That said, using “chat” all of the time meant a lot of copying and pasting. I wish there were a feature that would show a side-by-side diff of the proposed changes for you to review and accept. I believe Copilot X has this feature.

I found ways of making “chat” a little more useful, such as asking for only the parts of the code that changed, along with line numbers. I also got better results when prompting the AI to “act like an expert and use best practices.” For example, with that prompt, it corrected an earlier suggestion that used a deprecated pygame API.

I also found it useful to start with a basic request for what I wanted, then another iteration to refactor it, then another to enhance it closer to what I actually wanted or to fix what didn’t work. Perhaps some better prompting (like the “think in steps” trick) would have had better results, but I ended up doing the steps for it.

To that end, I think that if I did not already know a good amount of programming and game dev that this would have been much harder. Even just simple things like asking to “Extract this value out into a constant” or “Make a class for this part of it.” But I also had to draw on my game dev knowledge, like asking for alternate ways to do collisions or use sprite groups, and frequently, “Can you do that using vector addition instead?”

![Red, Green, Refactor](https://cdn.hashnode.com/res/hashnode/image/upload/v1692393611573/ceb13e90-832a-4ad9-8579-e7ea8b8aab67.png align="left")

*From* [*https://openclassrooms.com/en/courses/4554386-enhance-an-existing-app-using-test-driven-development/5095731-understand-the-red-green-refactor-methodology*](https://openclassrooms.com/en/courses/4554386-enhance-an-existing-app-using-test-driven-development/5095731-understand-the-red-green-refactor-methodology)

Basically, the AI was missing the “refactor” step in the Extreme Programming idiom, “red, green, refactor.” This was one area where working with an AI felt very different from working with a human pair. A human pair would be challenging the decisions I made, while the AI blissfully did whatever I asked for. Maybe this is an opportunity to improve the UX. For now, I just periodically ask the AI to do a pass over the code looking for improvements or potential issues, but it still feels like a one-way street. I would love the AI to say to me of its own volition, “Hey Jeff, the code down here looks like it should be changed…”

On a similar note, I wasn’t doing Test Drive Development for this project, at least not in the traditional sense. As a game, most of the “testing” was moving around in the game and seeing if things moved correctly, clipped at the right spot, had the right speed, weren’t jumpy, etc. Traditional TDD doesn’t help much with that. So after every code change, I’d have to manually see if it “felt” right and explain the problem to the AI if it didn’t. This was not a good feedback loop, as the AI would say that it “fixed” the problem, usually by putting more math around something, like ‘alpha = int(255 \* (1 — y / radius))’ and it wouldn’t get the desired effect. I think a more traditional and observable testing loop would have worked better, and I also think that a domain that didn’t involve math and “feel” would help the AI shine more. But we got there, often by me puzzling through the math-y bits to make it look and feel right.

So where does that leave me? I am pleased with the state of my game so far, but I am slightly worried that my code isn’t idiomatic, doesn’t follow best practices, or most distressing, isn’t performant. Where does code linting fit into the pipeline? How would it be if the project got huge? Large code bases are always difficult to keep in check, but would that be better or worse for the AI to deal with?

Then, the deep questions emerge. Do humans ultimately even need to see the code? What if the AI controlled the code entirely, invisibly updating it based on the conversation with the human? We aren’t there yet, but it seems like we could be soon. Is that desired? Or would that set us up for problems in the future? The movies always have a manual override that the protagonist needs to activate (usually in the most precarious spot). What if the code gets to a point we can’t access or understand if things go terribly wrong? GitHub’s Copilot guides emphasize that the human is the pilot, and the AI is the assistant. I think that is good advice, but with things advancing so quickly, I wonder how long it will hold.

> A human pair would be challenging the decisions I made, while the AI blissfully did whatever I asked for

I started with some goals. Did I meet them? Not completely. I certainly was able to quickly make things happen without having to know anything. I continued to feel empowered to blaze forward, adding features, though ultimately I lost most of the time I saved by tinkering with the math-y bugs.

I’m sad to admit that I did turn to the docs and even Stack Overflow, though often those instances verified what the AI had suggested but I had initially doubted. I did find it very helpful to be able to look up what I needed in the docs, but being able to go in with existing code gave me a much better context to understand and apply what I looked up, and I was able to improve what I asked the AI for.

The biggest difference in expectations was how much I drew on my own experience throughout the process. While I think that AI is fantastic for coders just starting out, it can be a very powerful tool for programmers with plenty of experience under their belts, and it becomes less of a magical code genie, and more of a magic wand to wield to shape your domain.

The final question is: will AI coding assistants change the way I work from now on?

The answer is absolutely yes. Since this experiment, I’ve been using AI in multiple effective ways professionally, and I plan to continue using it personally too in every new project going forward. If you haven’t tried an AI coding pair yet, I recommend giving it a shot, and if you have similar or different experiences, I’m curious to hear about them.