---
layout: post
title: "VSCode: Using LMStudio for code completion"
categories:
  - VSCode
  - GenerativeAI
tags:
  - AI
  - LMStudio
  - LLM
  - VSCode
---

Now that I am able to [run LLMs on my local network](.\2025-01-06 local-llms.md),
I wanted to use LMStudio (in server mode) for code completion in VSCode, similar
to how GitHub Copilot works.

VSCode supports additional functionality via extensions that can be added to the
IDE via **.vsix** files downloaded from the [VSCode Marketplace](https://marketplace.visualstudio.com/VSCode).
The one I chose to experiment with first is:

## continue.dev

* [continue.dev docs](https://docs.continue.dev/)

### Installation

* If you have other extensions, such as GitHub Copilot, ensure they are disabled.
* Download and install the extension direct from the
[VSCode Marketplace](https://marketplace.visualstudio.com/items?itemName=Continue.continue).

#### Interface layout

Once installed (and VSCode reloads its extensions) there will be a new icon in
the Activity Bar. Clicking on this opens the Continue extension in the Primary
Side Bar. The recommendation is to move this to the Secondary Side Bar panel on
the right hand side.

If it is not already visible, open the Secondary Side Bar panel with `Ctrl+Alt+B`.
You can then drag the Continue icon from the Activity Bar over to the Secondary
Side Bar.

You should now see a prompt box with the text "Ask anything. '@' to add context"
and a few other icons.

### Features

Continue.dev is a VSCode (and JetBrains) extension that provides the following
functionality, similar to GitHub Copilot:

* [ChatBot interface](https://docs.continue.dev/chat/how-to-use-it), using workspace files as context.
* [Code completion](https://docs.continue.dev/autocomplete/how-to-use-it) as you type.
* [Editing](https://docs.continue.dev/edit/how-to-use-it) selected text.

### Getting started

#### Models

Out of the box, the extension is configured to use Anthropic's Claude 3.5
Sonnet, for which you'll need an API key and spending money. You can select
(add) other models via a drop-down at the bottom of the prompt box and then
choosing the **+ Add Chat Model** option. A new panel will open, proving a list
of LLM providers to choose from. If you have an OpenAI API key, you could enter
that here and use GPT-4o, for example.

#### LM Studio

In my case I want to use a LLM running on my local network, at least to test how
well this worked compared to GitHub Copilot. I already have LM Studio running as
a server, so I chose **LM Studio** from the list of providers. I left the other
options as default ("Install provider" was the LM Studio website and "Model" was
set to auto-detect) and clicked **Connect**.

Doing this adds the following configuration for Continue in its **config.json**
file:

``` json
    {
      "apiBase": "http://localhost:1234/v1/",
      "model": "AUTODETECT",
      "title": "Autodetect (1)",
      "provider": "lmstudio"
    }
```

If you're not running LM Studio on the local machine, change `localhost` to be
the IP address or hostname of the machine LM Studio is running on. Once you have
done this you should now see a list of "auto-detected" models in the drop-down
list as an alternative to Claude 3.5 Sonnet. The list is provided by LM Studio
so if you want different models you need to download them there.

#### Chat

Once you have a model selected, you can use the prompt box to interrogate the
LLM. You can use data provided by VSCode for context; just type `@` and a list
of options appears. For example, you can specify the currently active file and
ask questions about the contents.

If you want to include a chunk of highlighted code in your message to the LLM,
press `CTRL+L` to copy the highlighted code across.

* See [the documentation](https://docs.continue.dev/chat/context-selectionv) for
more information about context selection.

#### Code completion

You may not want everything you are working on to be sent to the LLM for code
completion suggestions. Click on **Continue** in the status bar (right-hand end)
and you can enable/disable code completion.

Code completion options are set in the **config.json** file. In order to set up
completion suggestions you need to add/update the following JSON in the config:

``` json
  "tabAutocompleteModel": {
    "apiBase": "http://localhost:1234/v1/",
    "title": "lmstudio",
    "provider": "lmstudio",
    "model": "stable-code-instruct-3b"
  },
```

Again, replace `localhost` with the server name or IP address of the machine
running LM Studio if it isn't running locally. You may see some errors in the
chat bot panel if the extension attempts to retrieve completion suggestions from
the LLM but isn't able to connect.

Note also that the model name needs to be hard-coded in this chunk of JSON. The
documentation suggests entering the full "path" of the model in LM Studio, but
based on the 404 error message from the server it's only necessary to use the
short name for the model in LM Studio.

#### In-place editing

Editing code in-place in the active file tab works as described (see link above)
but the quality of the suggestions will obviously depend on the model used.

## Alternative IDEs

While looking for suitable tools, I came across a number of different IDEs that
supported AI integration. There's not much point listing them here as a web
search for "IDE with AI integration" provides what is needed.
