---
title: "Tip for controlling AI generated art"
datePublished: Fri Dec 01 2023 16:18:03 GMT+0000 (Coordinated Universal Time)
cuid: clpmtwgmh00020akz2gqu9nt3
slug: tip-for-controlling-ai-generated-art
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701374914903/1071dbb2-856a-4249-bb03-95c50595da39.jpeg
tags: ai, generative-ai, ai-art

---

I am making a prototype of a game that I designed that has close to 90 unique cards. Generative AI is great for this task, but sometimes I just can't get the right image. I learned a trick that gives me very tight control over the generated image and I want to share it.

I use [Leonardo](https://leonardo.ai/) for the image generation which offers some nice power tools. After playing around with different models and prompts to discover a general look that I like, I focus on the part of the prompt that is specific to the card I am working on. One particular card featured an "Angry skunk." This is the prompt that I used:

> Design for a Tarot card: Angry Skunk, forest theme, muted colors

The first and last parts are for the overall theme and look, and the middle part is for the subject. This is what it made:

![An angry skunk](https://cdn.hashnode.com/res/hashnode/image/upload/v1701376052682/73d8c3d2-d310-40fe-931c-7a53f01929d2.jpeg align="center")

The prompt is very short and simple. I usually start there, then add to it to flesh out the details or composition. In this case, the skunk is way too cutesy and cartoony and also too large in the frame.

I tried to adjust it by changing the prompt to say "behind a bush," "in the distance" or "long shot." I also added "cartoon" as a negative prompt. But for whatever reason, the model really thinks that skunks ought to look cutesy, cartoony, and in your face. So I had to get more advanced.

The model was great at making general forest scenes, so I made a fallen tree trunk, then opened that image in Leonardo's Canvas Editor and started drawing where I thought the skunk belonged. Now I'm not great at illustration, especially on my laptop's trackpad, and skunks are very confusing to draw from memory. But I figured a few black and white blobs would give the model the general idea. The purple bars show the masked area for the inpainting model to focus on:

![This is what I think skunks look like in broad terms](https://cdn.hashnode.com/res/hashnode/image/upload/v1701376470451/85052433-84d3-4144-b925-92528c02b8fe.png align="center")

You can see from the header image of this post how the model progressed through a couple of iterations of making my blobs actually look like a skunk. By changing the inpainting parameters and approach I was able to go from "sketch2image" and then "image2image" to get the final version. It has the right look and feel and most importantly, it is positioned properly in the frame. Here is the final card:

![An angry skunk in a card game](https://cdn.hashnode.com/res/hashnode/image/upload/v1701376834886/75c574d8-2cc6-4225-a5a3-ed0f35bad93b.jpeg align="center")

Raccoons were another small rodent that the model had trouble with. Like the skunk, it wanted very cute in-your-face raccoons despite my best efforts. I tried to get creative by changing the concept to "raccoons with glowing eyes hiding in the trees," but it just didn't work out right. So I did a similar process and was very happy with the results:

![Some very loosely sketched raccoons amonst the trees](https://cdn.hashnode.com/res/hashnode/image/upload/v1701377097822/fd6a2082-4eaf-4dbb-9789-79cf4e584d77.png align="center")

![some nicely rendered raccoons amonst the trees](https://cdn.hashnode.com/res/hashnode/image/upload/v1701377137520/3fbd18ea-f5aa-4e56-853e-a10795641d89.png align="center")

This technique works great any time you want to control or modify a specific element in an image. It elevates the AI image generation experience from a prompt to a paintbrush and makes me feel more involved in the process and more enabled to express what is in my mind. I've also used it for practical tasks like cutting out a frame or constraining an ink drawing to a specific area.

This type of interaction will only get better. I saw a demo just the other day of a new AI technology called real-time image generation with low latency models. You can paint a canvas on the left, and an AI-generated rendition of your sketch renders in real time on the right. Try it yourself on [fal.ai](https://www.fal.ai/dynamic).

AI art is not perfect, but for prototypes like this where volume and expediency are key, this technique can be very helpful.