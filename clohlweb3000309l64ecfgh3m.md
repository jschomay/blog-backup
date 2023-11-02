---
title: "Lost in an Infinite Maze: Building  a Real Time Generative AI Game Assets Pipeline"
seoTitle: "Real-time generative AI game assets pipeline"
seoDescription: "Postmortem on building a Generative AI game asset pipeline with details on fine-tuning a LLM on OpenAI and a custom image model to generate game content."
datePublished: Thu Nov 02 2023 19:55:30 GMT+0000 (Coordinated Universal Time)
cuid: clohlweb3000309l64ecfgh3m
slug: lost-in-an-infinite-maze-building-a-real-time-generative-ai-game-assets-pipeline
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698951101962/584af72b-3101-468a-89a1-c798082b207e.png
tags: ai, game-development, games, llm, generative-ai

---

I recently made a game with 100% AI-generated content. But I wanted more. I wanted to generate the content on the fly so that each scene would be completely new and unique in every play - a game of <mark>infinite exploration</mark>!

I gave a talk at the "[AI Engineer Summit 2023](https://www.ai.engineer/summit)" on how I accomplished this. You can watch it here or read the generated "transcript" below.

%[https://www.youtube.com/watch?v=q1LyrO3lWiA] 

<div data-node-type="callout">
<div data-node-type="callout-emoji">🎮</div>
<div data-node-type="callout-text">You can play the game yourself at <a target="_blank" rel="noopener noreferrer nofollow" href="https://enegames.itch.io/lost" style="pointer-events: none">https://enegames.itch.io/lost</a>.</div>
</div>

Also, the code is available on Github if you want to fork it to make your own game:

* Server/AI pipeline: [https://github.com/jschomay/lost-game-ai-asset-server](https://github.com/jschomay/lost-game-ai-asset-server)
    
* Client/game: [https://github.com/jschomay/Lost](https://github.com/jschomay/Lost)
    

---

## The Concept: Getting Lost in the Forest

The premise of the game is simple yet intriguing. As a player, you find yourself lost in a vast forest. Each scene presents encounters that impact your vigor and courage. The goal is to find your way back home before your courage runs out. A maze without walls. The only drawback was that I only made 16 scenes in a 4x4 grid, so after playing for a while they would repeat.

My favorite part of creating this game was generating each scene using AI and seeing what it came up with. I wanted to share this experience with the players and give them a unique scene every time they moved to a new location. By leveraging the power of AI, I was able to create a game of infinite exploration!

## AI-Generated Scenes: A New and Unique Experience Every Time

To create the scenes, I used a JSON object that describes the initial state of the scene and its subsequent variations. Initially, I employed OpenAI's Completion Endpoint and prompt engineering techniques to generate new scenes via their GPT3.5 Turbo LLM. The prompt I used was highly detailed and specific, ensuring that the AI-generated scenes maintained the required JSON format and contained fitting, varied, and interesting content.

*Initial prompt:*

```json
I'm making scenes for a game.  The setting is being lost in the forest.  Each scene has a unique feature that can be frightening, inspiring, relaxing, etc.  The scene can feature an encounter that is either animal, natural, human, or supernatural.
The player has two stats: vigor and courage.  Vigor is impacted by events that give or take energy and effort.  Courage is impacted by events that add or reduce fear and uncertainty.
A scene has title and 1-2 sentence initial description of what you see and how it effects you (in second person).  
It also has stat change of one, both, or neither of the player stats.  Changes should be an integer between -4 and 4.
A scene also has returning description that highlights any potential changes and how they impact you and a corresponding returning stat change.

Output format is a single JSON map:

{
  "title": "Intimidating Bear",
  "on_discover": {
    "description": "A massive bear stands tall, its powerful presence filling you with both awe and fear. You tread cautiously, knowing any sudden movement could provoke its fierce wrath. Best not to linger.",
    "stats": [
      {
        "stat": "courage",
        "diff": -2
      }
    ]
  },
  "on_return": {
    "description": "The bear is still here, or has it been following you?",
    "stats": [
      {
        "stat": "courage",
        "diff": -4
      }
    ]
  }
}
```

After obtaining satisfactory results, I fine-tuned the model using OpenAI's Fine Tuning Endpoint. I gave it 50 hand-selected generated examples. I also gave it a simplified prompt without explicitly mentioning the JSON structure.

*Simplified prompt:*

```json
Help the user make up scenes for a game. The setting is being lost in a forest. Scenes have different feelings and involve various encounters.
The output must follow a specific JSON map.  The only valid stats are `vigor` and `courage`.
```

The simplified prompt would reduce cost and latency. I was impressed to see that I still got consistent and valid results. The fine-tuned model produced scene descriptions that aligned perfectly with my requirements.

## AI-Generated Images: Creating Stylistically Consistent Art

In addition to generating textual descriptions for each scene, I also wanted to create stylistically consistent images to enhance the game's visual experience. To accomplish this, I utilized a tool called [Leonardo.Ai](https://leonardo.ai/), which not only allows image generation but also lets you create custom image models.

When training an image model, selecting training images that strike the right balance between consistency and variation is essential. It ensures that certain elements, such as perspective and scale, remain consistent across scenes while allowing for unique and diverse elements. I trained multiple models with different datasets before achieving the desired results.

*Training data (generated from the standard model):*

![Image training data](https://cdn.hashnode.com/res/hashnode/image/upload/v1698953491466/ca676c02-415b-4a35-8cbb-2a0bfb0ceded.png align="center")

*Generated samples from my custom model:*

![Game scene images generated from a custom AI image model](https://cdn.hashnode.com/res/hashnode/image/upload/v1697822563919/2b647dcb-94a9-46df-9fef-803dda9ca09e.png align="center")

I built a [preview server](https://lost-game-ai-assets-server.fly.dev/scenes) to visually inspect the generated images for quality and compare them to the scene descriptions. They all displayed the desired similarities while still being unique, ensuring a cohesive yet varied experience for the players.

![AI-generated game scenes](https://cdn.hashnode.com/res/hashnode/image/upload/v1698953380849/76adb4eb-2c39-43c2-948e-bded1db3a27d.png align="center")

## Assembling the Game: Bringing AI-Generated Content Together

With the AI-generated scene descriptions and images in hand, I updated the game to fetch images dynamically. I built an asset server with a simple AI pipeline to fetch and serve scenes on demand. First, a request for a new scene definition was made to OpenAI's Endpoint using my fine-tuned model. The resulting scene description was then validated to ensure the presence of all necessary keys.

Once validated, the scene description was sent to Leonardo to generate an image using the custom image model. After receiving the generated image, I combined it with the scene description and sent it to the game.

The whole pipeline would take up to 20-30 seconds to run, which was too much latency when requesting a new scene, so I built a simple cache that maintained a baseline number of generated scenes to draw from. The cache would be filled up automatically in the background when reaching a minimum threshold. In this way, I was able to achieve an instant, endless and scalable supply of unique generated content.

## The Result: A Unique Gaming Experience

The final product of this project offers players a unique and immersive experience that would not be possible without the use of AI. This innovative approach to game development satisfactorily demonstrates what is possible with AI technology. Yet this just scratches the surface.

## Opportunities for Expansion

While the game I created provides a compelling experience, there are several opportunities for expansion and further improvement. For instance, the generated images are currently low resolution (512 pixels). By incorporating an AI upscaler into the pipeline, higher-resolution images could be achieved, albeit at the cost of additional time and expense.

To further enhance the gaming experience, incorporating more user customization could be considered. For example, allowing players to select themes to guide the type of scenes they encounter. Or even generating scenes based on the user's time, location or current weather conditions for a truly immersive experience.

Furthermore, the process and techniques used in this project can be applied to other projects, opening up a world of possibilities for AI-generated content in various disciplines.