---
layout: post
title: "LMStudio: Running LLMs on my local network"
categories:
  - GenerativeAI
tags:
  - AI
  - LMStudio
  - LLM
---

While I have been happy using ChatGPT for generative AI tasks, especially as a
co-pilot for coding and IT knowledge support, this all happens through the web
UIs provided by the LLM provider (OpenAI, Anthropic, etc.).

Some project that I have wanted to work on require access to APIs, which charge
for access. While the prices aren't high, especially for relatively low usage,
it seemed unnecessary to pay anything when open-source models are available that
can run on relatively modest hardware (NVidia RTX GPUs).

So I started looking into options for serving large language models (LLMs) on my
local network, specifically, on a Windows 11 PC with an 8GB RTX 2080 GPU. As it
happens, the first app I tried seemed to meet my needs so I didn't look further!

## LMStudio

* [LM Studio](https://lmstudio.ai/)

LM Studio, on version 0.3.6 at the time of writing, is described on its own
website as "a desktop app for developing and experimenting with LLMs on your
computer". There are installers for Windows, MacOS and Linux. Once installed you
can:

* [Browse for models](https://lmstudio.ai/docs/basics/download-model) on HuggingFace.
* Run models locally and [interact with them](https://lmstudio.ai/docs/basics/chat) via a ChatBot interface.
* Serve models on the local network, providing an [OpenAI compatible API](https://lmstudio.ai/docs/api/openai-api).
* Run in [headless mode](https://lmstudio.ai/docs/advanced/headless)
* And more, such as a CLI and tool use (currently in Beta).

### Models

It doesn't seem to matter what architecture you choose for the models you want
to run (e.g. LLama, Phi, etc.). Perhaps obviously, you can only download
open-source models; you can't run versions of ChatGPT or Claude.

You need to choose models that will fit in the available VRAM (8GB in my case).
There are options to offload some inference to the CPU and main RAM but I chose
not to experiment with that.

## Ollama

It is worth mentioning that the other LLM server that I have most frequent come
across is [Ollama](https://ollama.com/). I may experiment with this in the
future but for now, LM Studio is working fine.
