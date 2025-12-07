---
title: 'Closing Thoughts for 2025'
date: '2025-12-07'
tags:
  - ai
  - software engineering
---

As the year winds down, I thought I'd wrap up with some closing thoughts around AI/ML, engineering, and how it's going professionally.

## We're still trying to figure out how to responsibly use LLMs / GenAI

It's undeniable that LLMs are super useful. 

But use LLMs for everything and risk becoming a [meme](https://www.youtube.com/shorts/2zb7S2beKOE).

You'll stunt your growth if you make ChatGPT to do your homework. Karpathy [highlights](https://x.com/karpathy/status/1993010584175141038) "the goal is that the students are proficient in the use of AI, but can also exist without it, and imo the only way to get there is to flip classes around and move the majority of testing to in class settings."

Bryan Cantrill from Oxide Computing (and one of the most compelling speakers and writers in the field and throwback from when I first heard him [speak](https://www.youtube.com/watch?v=AdMqCUhvRz8) at Dockercon '15) published how they use [LLMs at Oxide](https://rfd.shared.oxide.computer/rfd/0576) and it comes down to responsibility.

AI generated videos - or AI slop - is becoming its own [category](https://podcasts.apple.com/us/podcast/how-to-lead-ben-horowitz-on-my-first-million/id842818711?i=1000739272418). I really think the AI cat videos are melting peoples brains. One Punch Man Season 3 animation is pretty bad and fans are accusing animators of using AI [poorly](https://www.youtube.com/shorts/m2wnSdmZi70).

Done right, you can get some really good advice for learning new concepts, studying for interviews, and planning a vacation. 

## The battle in the US is over. The competition is now with China.

ChatGPT came out in November 2022. That gave the AI labs and startups the chance to disrupt before Big Tech got their stuff together. Three years was all Google needed to focus their army of big brain computer scientists to [top LMArena in text, vision, video, image, and search](https://lmarena.ai/leaderboard). Mic-drop.

We have lots of great private LLM companies but not so many open-source alternative. Shoutout to [Olmo 3](https://allenai.org/blog/olmo3) from Ai2 leading efforts in the States. OpenAI also dropped gpt-oss which was generous of them. 

But you see the speed and pace of models coming out of China and you just wish for the same here. [DeepSeek-OCR](https://arxiv.org/abs/2510.18234) provided a new way to look at inputs. Images of text might be easier to encode meaning - very applicable to coding. Karpathy's take [here](https://x.com/karpathy/status/1980397031542989305). And remember, these models are still blackboxes. We KNOW they can be jailbroken. [Backdoors can be introduced by a small number of samples](https://www.anthropic.com/research/small-samples-poison). 

The White House annouced the [Genesis Mission](https://www.whitehouse.gov/presidential-actions/2025/11/launching-the-genesis-mission/) late November. Here's what Google AI Overview says: The mission aims to build an integrated national AI platform—called the "American Science and Security Platform"—that unifies federal datasets, high-performance computing resources (supercomputers), AI models, and robotic laboratories into a "closed-loop" discovery system. This system is designed to dramatically cut down R&D cycles from years to potentially days or hours.

Have you seen the [Xiaomi Electric cars](https://www.youtube.com/watch?v=Mb6H7trzMfI)?

## Lots of opportunities to learn, grow, and contribute

Don't let the AGI doom and gloom take over. You're here for the love of the game. Build cool things, contribute to project you use, go deep into the codebase with the help of [DeepWiki](https://deepwiki.org/).

All eyes are on AI but that leave lots of opportunity on other projects like [Rails](https://github.com/rails/rails/issues) and [OpenTelemetry](https://opentelemetry.io/community/). PyTorch has a [good first issues](https://github.com/pytorch/pytorch/issues?q=is%3Aissue%20state%3Aopen%20label%3A%22good%20first%20issue%22) tag. There are still people behind these projects, not AIs. And getting up to speed and helping is not trivial but a lot easier with the quick feedback you can get from asking uncle Claude. 

## Still bullish on Small Models and Structured Output

My most recent side project was figuring out whether people would like a fine-tuning platform for Apple Intelligence [Foundation Model Adapters](https://developer.apple.com/apple-intelligence/foundation-models-adapter/). I reached out to 20+ app developers using AFM, a few replied graciously, and only one used adapters. Learned a lot from using Rails 8 and Sagemaker but ultimately the market isn't there yet.

News broke that [Apple is going to use Google for Siri](https://www.bloomberg.com/news/articles/2025-11-05/apple-plans-to-use-1-2-trillion-parameter-google-gemini-model-to-power-new-siri). Hopefully the partnership goes beyond the Trillion parameter models and we get improvements with AFM too.

Structured output as a developer is still super exciting. All major LLMs now support structured outputs. Instead of begging the model to spit out a format and retrying if it didn't work, there's a structured supported way to ask. It's still not 100% but smoothing the edges to make development more reliable and not require re-engineering is great.

We saw a breakthrough with [TinyRecursiveModels](https://github.com/SamsungSAILMontreal/TinyRecursiveModels) achieve 45% on ARC-AGI-1 and 8% on ARC-AGI-2 using 7M parameters. Special purpose built for solving mazes but incredibly small and the concept can be applied elsewhere.

[Z-Image](https://github.com/Tongyi-MAI/Z-Image) just came out from Alibaba and is a 6B parameters text-to-image model that's really good and open-source. I haven't read the paper but it's also apparently very open about the model architecture and data it used.

## Fulfilling and meaningful work

I'm feeling grateful for the opportunity at [Nava](https://www.navapbc.com/) to lead an infrastructure team and go from zero to one. In a way, we're only now [approaching Day 1](https://minnesotareformer.com/2025/12/01/minnesota-paid-leave-launches-in-one-month-heres-what-you-need-to-know/). It just feels great to learn, grow, teach, support, and just try my best with a supportive team.

[Strata](https://www.navapbc.com/strata) is our push to make new software programs repeatedly successful through open source tooling. Happy to contribute to Strata a small bit.

## Closing Statement

It's been an incredible year of discovery and learning. In the year of AI full steam ahead, the steps are the same. 

As karpathy-sensei [put](https://x.com/karpathy/status/1325154823856033793?lang=en) it,
```
How to become expert at thing:
1 iteratively take on concrete projects and accomplish them depth wise, learning “on demand” (ie don’t learn bottom up breadth wise)
2 teach/summarize everything you learn in your own words
3 only compare yourself to younger you, never to others
```

So keep learning, but keep building.
