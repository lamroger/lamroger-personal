---
title: 'Guardrails for LLM Chatbots (March 2024)'
date: '2024-03-11'
tags:
  - llm
  - guardrails
  - chatbots
---

LLMs are great at generating text. Trained on the corpus of the internet, fine-tuned to respond in a human-centric manner. LLMs from OpenAI, Google, Anthropic, and more are battling to convince people to use their models over others. Open source models from Meta and Mistral give an alternative to people that want to host their own models too.

The use case for chatbots is compelling. As the Turing Test and Westworld proposed, "If you can't tell, does it matter?". [Klarna said](https://www.fastcompany.com/91039401/klarna-ai-virtual-assistant-does-the-work-of-700-humans-after-layoffs) it handles 2/3rds of customer support tasks with chatbots with similar satisfaction ratings to human agents.

Throwing an LLM into your app also doesn't seem like the best approach. A [Chevy dealership](https://medium.com/@branden.mcintyre/chevy-chatbot-misfire-a-case-study-in-llm-guardrails-and-best-practices-7ae319088e94) got pwned to promote its competitor. [Air Canada](https://www.theguardian.com/world/2024/feb/16/air-canada-chatbot-lawsuit) was ordered to be responsible for hallucinated responses around it's bereavement policy.

Call it automation or 2023's word of the year, enshittification, companies are looking for ways to cut costs and increase efficiency. [Gartner](https://www.gartner.com/en/newsroom/press-releases/2022-07-27-gartner-predicts-chatbots-will-become-a-primary-customer-service-channel-within-five-years) predicts that chatbots will be the primary customer service channel for roughly a quarter of organizations by 2027.

Whether it's a chatbot, a recommendation system, or a content generator, the guardrails are the same. Left as an afterthought and you'll be in the news for the wrong reasons.

Below is a proposal I did for prototyping guardrails around LLM chatbots.

### Overview

Gartner predicts that chatbots will be the primary customer service channel for roughly a quarter of organizations by 2027[1].

While LLMs can produce higher quality conversational interactions, the inherent generative nature remains a risk.

Our goal is to create a reliable and robust LLM-powered chatbot with the latest safety and guardrail tools and methodologies. Additionally, we want to maintain a high level of transparency and modularity to monitor, debug, and improve the system over time.

### Core Components

#### Base model
We lean on foundation models with higher levels of safety and alignment[2]. Our implementation will also support multiple models for our own domain-specific benchmarking and the ability to fallback if there are external provider outages.

* OpenAI GPT 3.5 / 4
* Anthropic Claude
* Google Gemini
* Llama 2

#### Framework

Nvidia’s [NeMo-Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) is an open-source toolkit for adding programmable guardrails to LLM-based conversational systems. The built-in guardrails allow us to quickly get started with checks - with, for example, jailbreak detection and input/output moderation.
While NeMo relies on using LLM calls to steer dialog and perform most of the guardrail checks, it can also integrate other endpoints, APIs, and approaches.

##### External guardrails to add
* [LlamaGuard](https://ai.meta.com/research/publications/llama-guard-llm-based-input-output-safeguard-for-human-ai-conversations/) is a safeguard model developed by Meta for input and output classification. It acts as an example of external LLM feedback.
* [LLM Guard](https://llm-guard.com/) is another toolkit for input and output control. It has a combination of deterministic and probabilistic checks. It acts as an example of internal (deterministic) feedback.

##### Other considerations

* [Microsoft Copilot Studio](https://www.microsoft.com/en-us/microsoft-copilot/microsoft-copilot-studio) is a platform to build and run copilots in a low-code graphical environment. While it allows for quick prototypes, the low-code aspect prevents abstracting the environment to apply to other customers. It does have analytics out-of-the-box.
* [Guardrails AI](https://www.guardrail.ai/) is an open source library for structural and type validation and corrections. They recently released a platform with modules that need a bit more research to see if it fits our needs.
* [LMQL](https://github.com/eth-sri/lmq) is a programming language for LLMs. It combines templating in Python with templating in LLM calls and responses for structured output
* [Outlines](https://github.com/outlines-dev/outlines) also focuses on generating structured output
* [Guidance](https://github.com/guidance-ai/guidance) is another library for structured output but focuses on efficiency through constraining output
* [Instructor](https://github.com/jxnl/instructor) is yet another structured output library but leveraging Pydantic
* [Prompt Security](https://www.prompt.security) is SaaS for generative AI security
* [More](https://www.signalfire.com/blog/prompt-injection-security) SaaS providers on AI Security

### Evaluation

When building and deploying LLM-based chatbots, one aspect that shouldn’t be overlooked is evaluation. How do the different layers of guardrails impact the reliability of our chatbot? What can we test ahead of time? When we find a gap or vulnerability, how confident are we in fixing it and not breaking something else?

NeMo provides an [evaluation tool](https://github.com/NVIDIA/NeMo-Guardrails/blob/develop/nemoguardrails/eval/README.md) and [red-teaming interface](https://github.com/NVIDIA/NeMo-Guardrails/blob/develop/docs/security/red-teaming.md) to help streamline evaluation.

We also need to evaluate the chatbot based on [performance](https://deepchecks.com/best-practices-for-llm-evaluation-of-rag-applications/) - including accuracy, fluency, coherence and relevance. This will include automated and human evaluation. Creating the test set and scenarios, continuously evaluating, monitoring and improving is necessary to uphold the highest standards for customer satisfaction.

Every domain vertical will require its own test set. Each customer will require a further specialization. While it presents additional challenges, it’s also an opportunity to provide the most robust and reliable system to our customers.

### Monitoring

On the chat level, all conversations will be accessible through an admin panel. Future iterations can include customer service representatives joining the conversation as needed.

Internally, all LLM calls will be instrumented and monitored. We know some major LLM providers have inconsistent response times and chaining multiple guardrails can lead to long latency. This will be a trade-off we will continually monitor.

### Timeline

For the prototype, we’re aiming for a 6-8 week release, running in 2 week sprints.

Roughly, we want to spend 50% on building the chatbot and 50% on evaluation and monitoring.

* Week 1-2: Requirements gathering and planning. Building.
* Week 3-4: Building.
* Week 5-6: Evaluation.
* Week 7-8: Monitoring.

### Out of Scope

* RAG functionality. NeMo plays well with RAG implementations but will require more time to experiment and test out embeddings, infrastructure, and retrieval. This could be added but requires a bit more research.
* LangChain or LlamaIndex. LangChain and LlamaIndex are popular LLM frameworks. We don’t plan on using these since NeMo works well without an additional framework. NeMo does fit well into LangChain Chains if we decide to add LangChain.

### Links
* [1] [https://www.gartner.com/en/newsroom/press-releases/2022-07-27-gartner-predicts-chatbots-will-become-a-primary-customer-service-channel-within-five-years](https://www.gartner.com/en/newsroom/press-releases/2022-07-27-gartner-predicts-chatbots-will-become-a-primary-customer-service-channel-within-five-years)
* [2] [https://huggingface.co/blog/leaderboards-on-the-hub-decodingtrust](https://huggingface.co/blog/leaderboards-on-the-hub-decodingtrust)
* [LLM Patterns](https://eugeneyan.com/writing/llm-patterns/#guardrails-to-ensure-output-quality)
