---
lab:
    title: TechLab: TechLab: Terminal to Party: Live-Coding with Copilot CLI and Hydra
    description:
    level: 200
    duration: 120 minutes
    islab: true
    primarytopics:
---

# LAB500: Terminal to Party - Live-Coding with GitHub Copilot CLI and Hydra

Welcome to the GitHub Copilot Dance Party! Over the next \~75 minutes you'll turn a blank app into a browser-based AV playground - part code editor, part synth rig, part dance floor - with GitHub Copilot CLI riding shotgun the entire set.

> [!WARNING]
> **Photosensitive seizure warning**
> 
> The visuals you build with Hydra can include rapidly flashing lights, high-contrast patterns, and strobe-like effects. A small percentage of people may experience seizures when exposed to such images - even people with no prior history of epilepsy. If you experience dizziness, altered vision, eye or muscle twitching, disorientation, or convulsions while building or watching demos, stop immediately and consult a medical professional. If you or anyone in your family has a history of seizures or epilepsy, talk to a doctor before participating.
> 
> To help with this, make sure your app has an easy-to-hit stop button. You can add that as a requirement when talking with Copilot!

## 🚦 Before you begin

You'll be working from a provided lab environment: a **codespace with everything you need**, running from the local machine you're using rather than the lab environment. GitHub Copilot CLI is already installed, and you've been provided a starter project you can use to help you quickly create your masterpiece.

> [!NOTE]
> This is intentionally **not** a step-by-step exercise sheet. You are the architect and the DJ. Copilot CLI is your technical co-producer. Discover, prompt, remix, iterate, and ship something loud enough to demo.

## Lab sections

The content of this lab is designed to help set you up for success. It walks through the starter environment you have access to, talks through best practices when working with GitHub Copilot (and really any AI tool), and defines the requirements of the cool tool you're building. These include:

0. **Backstage** \- soundcheck the rig: log into the codespace\, sign into GitHub\, and get to a Copilot CLI prompt inside your project.

1. **Hello, world** \- explore the starter app you'll be building from and confirm everything's wired up.
2. **The vibe** \- what you're building, the experience you're aiming for, and the libraries you'll wire together.
3. **The set list** \- the Copilot CLI moves that keep your loop tight: model picks\, parallel agents\, MCP servers\, tips\, resources\, and stretch ideas\. Skim it for shape; you'll put it to work next\.
4. **Take the stage** \- concrete first prompts to run with Copilot CLI: plan\, research\, set up project context\, and build\. This is where the actual building happens\.
5. **Take it on the road** \- stretch ideas, in\-room awards, retro questions, and curated resources to keep the energy going after the lab wraps\.

## Let's get started!

Select **NEXT** down below to move onto the next page!

===

# 0. Backstage

Before we can take the stage we need to show our all access pass. We need to authenticate! Let's tackle that first!!

> [!IMPORTANT]
> We aren't going to be using the VM provided in the lab environment, but rather using the browser on the local system. The steps here will walk you through obtaining the credentials from the lab and authenticating locally.

## Authenticate

Unlike most other labs at Build, you'll be working in a cloud codespace rather than a provided VM. You'll still be using the lab credentials, which we'll walk through right now.

1. In the new tab, navigate to [https://github.com/enterprises/skillable-events/sso](https://github.com/enterprises/skillable-events/sso).
2. When prompted to **Single sign-on to Skillable Events**, select **Continue**.
3. From the **Resources** tab in the lab interface, copy the **username** and paste it back into the username field on the login screen.

    !IMAGE[Screenshot of the resources tab with arrow pointing at keyboard for username](../../media/username.png)

> [!IMPORTANT]
> You will use the credentials provided on the Resources tab, rather than the ones on the screenshots. The screenshots are there just to help you see what the interface looks like.

4. Select **Next**.
5. From the **Resources** tab in the lab interface, copy the **TAP** (temporary access code) and paste it into the TAP dialog field on the login screen.

    !IMAGE[Screenshot of the resources tab with arrow pointing at the keyboard for tap](../../media/tap.png)

6. Select **Sign in**.
7. Select **Yes** to stay logged in.

## Summary

You've authenticated!! Next step - setup the development environment. Select **Next** to move forward to creating the starter environment!

===

# 00 Your developer rig

Now that you have access to the stage, you need to soundcheck the rig. Or, more specifically, to spin up the codespace you'll use for the workshop!

> [!NOTE]
> You will be using Codespaces the browser in the lab PC rather than the VM in the browser. This will ensure we have the best possible throughput. For authentication you'll use the credentials from the lab, which these next steps will walk you through. Please feel free to begin working through these steps as you're getting situated.

## Codespaces

[GitHub Codespaces](https://github.com/features/codespaces) is a fully-configurable cloud-based container where you can develop. It even comes with a browser-based version of Visual Studio Code, allowing you to write code without installing anything locally. Additionally, any services you start on your codespace, like a web server, become available via tunneling. It feels a lot like working on your own local system, but everything's being done in the cloud!

## Create your starter environment

Now that you're logged into GitHub, it's time to set up your project! We've provided a starter with a core set of assets. You'll explore it more in the next step (with the help of Copilot!), so for now our focus will be on creating the copy you'll use.

1. Open a new browser tab by selecting <kbd>Ctrl</kbd>+<kbd>T</kbd>.
2. Navigate to [https://github.com/GeekTrainer/lab500-starter](https://github.com/GeekTrainer/lab500-starter).
3. Select **Use this template**.
4. In the **Create new repository** dialog, select **Skillable-Events** for **Owner**.
5. For **Repository name**, use **[YOUR_GITHUB_HANDLE]-dance-party**, replacing **[YOUR_GITHUB_HANDLE]** with your GitHub handle.
6. Scroll to the bottom and select **Create repository**.
7. After a few moments, your repository will be created!
8. Once your repository is created, select **Code**.
9. Select the **Codespaces** tab.
10. Select **Create codespace on main**.

!IMAGE[Screenshot walking through creation of codespace](../../media/CleanShot 2026-06-02 at 17.01.49@2x.png)

This will start a codespace in the cloud on the repository you just created. This will take a few moments to open.

## Launch the starter app

With the codespace environment created, let's launch the starter app! You'll be building on top of this as you progress through the workshop, and starting it now will streamline your development process.

1. Once the codespace is available, and VS Code displays in your browser, select <kbd>Ctrl</kbd>+<kbd>`</kbd> to open a terminal window.
2. Start the sample app by running the following command in the terminal in your codespace:

    ```
    npm run dev
    ```

3. After a moment, the application will start.
4. Display the ports being exposed by the codespace by selecting the **Ports** tab.
5. Open the app in the browser by right clicking on port **5173** and selecting **Open in browser**.

    !IMAGE[Screenshot showing the last three steps of selecting the Ports tab, port 5173, and Open in browser.](../../media/CleanShot 2026-05-26 at 11.38.33@2x.png)

6. Wait for the app to launch in the new browser tab, and the status in the upper right to say Copilot is connected.

## Start Copilot CLI

OK, last setup step! You've authenticated, obtained the starter project, created your dev environment, and launched the starter app. Let's invite GitHub Copilot to the party! You'll be using Copilot CLI to generate your amazing app!

1. Return to the tab in your browser with your codespace.
2. Return to the terminal in your codespace by selecting the **Terminal** tab.
3. Create a new terminal instance by selecting the **+** or new button near the **Terminal** tab.
4. In the new terminal window, launch Copilot CLI in YOLO mode by running the following command in the terminal:

    ```
    copilot --yolo
    ```

    > [!WARNING]
    > YOLO mode (including **--allow-all-tools**, or **/allow-all** / **/yolo** from inside the CLI) gives Copilot the same access to your machine that you have, and it can run any shell command you can run **without prior approval**. It's appropriate inside this disposable lab codespace, but may not be appropriate in other environments. **Don't run YOLO mode on your personal or work machine, or anywhere with real credentials, private code, or files you can't afford to lose, unless you fully understand the risk.**

5. When Copilot prompts you to trust the folder, select **Yes, and remember this folder for future sessions.**

## Setup summary

You've got the stage set! You have a starter project and an environment in which to code. Select **Next** to begin exploring the starter from which you'll build your masterpiece!

===

# 1. Hello, world

As highlighted previously, this workshop is built to focus on exploration, where you'll work with Copilot towards building out a project based on a set of specs. To help get you started, though, we've provided a scaffolded app that contains a couple of key resources. Let's explore what's there and start the app.

## Explore the starter app

At a high level, the starter app contains:

- [Hydra](https://github.com/hydra-synth/hydra)
- [GitHub Copilot SDK](https://github.com/github/copilot-sdk)
- [Vite](https://vite.dev/)
- A server folder with the APIs needed to integrate Copilot SDK
- A web folder with a minimal shell incorporating Hydra and calls to the APIs
- MCP servers including:
  - Playwright, which Copilot can use to interact with the application
  - Microsoft Learn, which provides access to documentation
  - Context7, which provides access to documentation about many modern frameworks

Let's explore the starter project and start it up.

1. Inside Copilot CLI, use the following prompt to ask about the starter app:

    ```
    Tell me about the structure of the app in this folder
    ```

2. Ask Copilot about the MCP servers available to it and what each can do:

    ```
    Tell me about the MCP servers you have access to. What tasks can they perform?
    ```

> [!TIP]
>[!Note] the approach here of asking Copilot not just about the project but about the features and assets it has access to. When in doubt - ask Copilot!

## Hello world summary

You've now got an understanding of the starter app, and the tools you've got at the ready. Select **Next** to explore the vibe, the rig and start building!

===

# 2. The vibe

Let's explore what we're building and the world in which we're building it. As highlighted previously, we're creating a vibe-coded vibe-code development environment (very meta). Let the following help shape your thoughts as you begin to sketch a mental image of what you're going to create and how you're going to create it.

## 🎯 What you're building

A **browser-based, Copilot-powered live-coding tool**: an editor where visuals, sound, and natural-language prompts all feed the same performance. You'll use the GitHub Copilot SDK for integration, Hydra for visuals, and libraries of your choice to bring in the editor, music, and whatever else you think you need to create your masterpiece!

Concretely, your app should feature:

- An IDE a developer could use to create code.
- **Hydra visuals** on the outside of their editor to add some flair to the experience.
- **Music** generated in the browser in sync (or at least vibing) with the visuals, and built using a code-based framework.
- A collection of **themes** the developer could choose from that are combinations of those visuals and music.
- An ability to add and edit themes by **describing them in natural language** to Copilot, which then updates the theme's definition.

Whether you build a polished production rig or a glorious one-hour basement rave is up to you.

> [!NOTE]
> For this lab, "working" doesn't mean production-ready. A successful demo can be as simple as one Hydra canvas in the browser, one sound loop, one editable theme, and one Copilot-assisted change to that theme. Polish is bonus. **Visible, audible, explainable** is the goal.

## 🎛️ The rig

Your rig is the libraries and toolkit you'll be using to build out your application. We've provided a starter project that includes Hydra and GitHub Copilot SDK. The rest - the music, the code editor, the style - all of those are up to you! If you're not sure where to start, you can always ask Copilot! It can do research on your behalf.

### Core libraries

The two core libraries this workshop is built around:

- **[Hydra](https://github.com/hydra-synth/hydra)** \- the live\-coding visuals engine\.
- **[GitHub Copilot SDK](https://www.npmjs.com/package/@github/copilot-sdk)** \- to embed Copilot directly into the app you're building\.

> [!IMPORTANT]
> The Copilot SDK runs in Node, not the browser - so your in-app Copilot integration is actually two pieces: a small backend that hosts the SDK and a browser frontend that calls it. Authentication piggybacks on the Copilot CLI you logged in to in Backstage, so there's no OAuth flow and no GitHub token to manage in your code. That said, it's always worth taking a moment to add a reminder: **Don't put GitHub tokens in browser code!!**

### The rest of the tech stack

Outside of the two listed above, you're free to choose whatever libraries and frameworks you think work best! You'll need to ensure you have techs that can handle the following:

- **A music engine.** Something that produces sound in the browser. A couple of starting points to consider: [Strudel](https://strudel.cc/) (live-coding musical patterns with known Hydra-friendly workflows) or [Tone.js](https://tonejs.github.io/) (general-purpose Web Audio framework). Plenty of other options exist - pick what excites you.

    > [!NOTE]
    > Browsers block audio until the user interacts with the page, so design for a visible **Start audio** (or **Start show**) button rather than trying to autoplay sound on load. This is by far the most common "why isn't there any sound?" detour.

- **A code editor component.** Something to host the live-coding buffers in your app. Two well-known options: [CodeMirror 6](https://codemirror.net/) (lightweight, modern) or [Monaco Editor](https://microsoft.github.io/monaco-editor/) (the same editor that powers Visual Studio Code). Or pick something else.
- **Anything else you might want!** Want to create the project in Svelte? React? TypeScript? JavaScript? Add in testing with Playwright? Vitest? You're the lead developer here, so you make the call!

You're starting from a starter project with Hydra and Copilot SDK. The rest is up to you!!

### Themes as data, not code

When Copilot helps generate a theme, prefer **structured theme definitions** (JSON-ish config objects: colors, tempo, Hydra function names, parameters) over arbitrary JavaScript that your app then evaluates at runtime. Data-shaped themes are safer, easier to validate, and easier for Copilot to iterate on without breaking your app.

> [!TIP]
> Don't know what to pick? Ask Copilot! As we chatted about previously, Copilot can do research for you. Use the following template as a prompt for Copilot to do a deep investigation and recommend with citations.
> 
> You could prompt Copilot, "I'm building [brief description]. I need libraries I can use for [feature request here]. Can you make some suggestions?". (Don't forget to swap the [placeholders] with the actual text!)

## The vibes are good

With the knowledge in hand of what you're building and the libraries you'll use, select **Next** to see how we can use Copilot to build out your masterpiece!

===

# 3. The set list

This page is your pre-flight checklist. You don't need to master every command before building - read the minimum requirements, skim the CLI moves, and come back to the tips and resources when you need them.

## 🎯 Minimum requirements

Quick reminder of what your app needs to do:

- Have a working **IDE in the browser**.
- Render **Hydra visuals** live around the IDE.
- Generate **music** in the browser using code, vibing with the visuals.
- Let someone **edit themes** via Copilot.

The implementation details - framework, libraries, architecture, polish level - are up to you.

> [!TIP]
> Need inspiration? Ask Copilot for theme ideas, visual concepts, or music moods.

## 🛠️ The Copilot CLI set list

These are the moves that will keep the next hour from turning into feedback squeal. Not every feature is mandatory, but the more you lean on these, the better Copilot will work for you. Skim them now to get the shape of what's possible - you'll put them to work in just a few beats.

### Context is key

Not every imperfect answer is Copilot getting it wrong. Oftentimes the answer is valid but there wasn't enough context to provide the expected result.

For example, if you prompt Copilot to "Create some cool music," you likely won't get a beat you can dance to. However, if you prompt, "Create a music loop that's about a minute long, has good body, and is in the style of 80s alternative dance music," you'll find something quite a bit closer to what you have in your head! (Or at least closer to what we had in mind when writing this section.)

> [!TIP]
> Be prescriptive when you're prompting Copilot! If you're asking for UX updates, new features, or a better beat, describe exactly what you want and how you want it.

### Pick the right model for the job

Copilot CLI lets you switch models on the fly with **/model**. GitHub's [model comparison docs](https://docs.github.com/en/copilot/reference/ai-models/model-comparison) group models by task area - *general-purpose coding*, *deep reasoning and debugging*, *agentic software development*, and *fast help with simple or repetitive tasks* \- and recommend different models for each\. Switch models as your task changes\, and pair it with [rubber-ducking](https://en.wikipedia.org/wiki/Rubber_duck_debugging) your plan: plan and critique with one model, implement with another.

### Run agents in parallel with **/fleet**

This is the headline drop for this lab. **/fleet** lets you spin up subagents that work in parallel - for example, one subagent generating a new theme while another updates tests, all while you keep typing in your own editor. Don't wait for one agent to finish its solo before you cue the next track.

### Lean on MCP servers

[Model Context Protocol (MCP)](https://modelcontextprotocol.io/) servers extend what Copilot can do - giving it new tools, data sources, and ways to interact with the world. Inside Copilot CLI, run **/mcp** to manage them. You already have 3 installed:

- Playwright, which allows Copilot to interact with your app
- Microsoft Learn, which provides access to Microsoft documentation
- Context7, which provides access to documentation for many frameworks

You can also browse the [GitHub MCP Registry](https://github.com/mcp) to discover what's available, or (and stop us if you've heard this already) you can always Ask Copilot!

### Use tests as your feedback loop

Even quick smoke tests are your soundcheck. A Playwright test that loads the page and confirms the canvas is rendering gives Copilot something objective to tune against.

## 💡 Tips & tricks

- **Write the PRD first.** Even a short one. It anchors everything else.
- **Start with a plan before creating code.** Always.
- **Author your instructions files early.** A 10-minute investment that pays off for the rest of the project.
- **Share documentation URLs in your prompts.** When you ask Copilot to add a Hydra effect, paste the Hydra docs link in the prompt, or ask Copilot to look them up.
- **Playwright MCP comes in clutch.** Anytime you wonder "did that actually work in the browser?" - let Copilot check.
- **Good tests help.** Even one or two. They give the agent a reason to stop.

## 📖 Resources

Documentation and curated lists for the tools and libraries you might find helpful:

- [GitHub Copilot CLI documentation](https://docs.github.com/copilot/concepts/agents/about-copilot-cli) \- the canonical reference for the CLI you'll be living in\.
- [Choosing the right AI model for your task](https://docs.github.com/en/copilot/reference/ai-models/model-comparison) \- guidance for the **/model** switch.
- [GitHub Copilot SDK](https://github.com/github/copilot-sdk) \- to embed Copilot directly into the app you're building\.
- [Hydra documentation](https://hydra.ojack.xyz/docs/) and the [Hydra repository](https://github.com/hydra-synth/hydra) \- your visuals engine\.
- [GitHub MCP Registry](https://github.com/mcp) \- discover MCP servers worth wiring up\.
- [Microsoft Learn MCP server](https://github.com/MicrosoftDocs/MCP) and [Playwright MCP server](https://github.com/microsoft/playwright-mcp) \- two MCP picks called out in the set list\.
- [github/awesome-copilot](https://github.com/github/awesome-copilot) \- a community\-curated catalog of instructions\, prompts\, and patterns for Copilot\. Great place to grab a head\-start on instructions files and other context.
- [Model Context Protocol](https://modelcontextprotocol.io/) \- the spec behind every MCP server\.

## 🌟 Stretch ideas

When you have your core editor working and you're hungry for more, unlock the bonus tracks:

- **Save and share themes.** Persist them to `localStorage`, or encode them into the URL hash so a friend can open your vibe.
- **Author your own MCP server.** A small custom MCP server that, say, exposes a "generate theme" tool to Copilot.
- **Polish for production.** Error handling, mobile layout, accessibility. Make it something you'd actually ship.
- **Multi-buffer performance mode.** Two themes running side-by-side with a crossfader.

> [!TIP]
> Not sure how you'd go about implementing these features? Ask Copilot!!

## The set list is set

You've seen how Copilot can help you build. Now it's time to put it all into action! Select **Next** for some tips on how to start creating!

===

# 4. Take the stage

You've got the vibe, the rig, and the set list. Time to step up to the mic. This section gives you some ideas on first prompts to run with Copilot CLI as you start writing app code. Feel free to use the prompts as you see them, modify them, or ad lib and use your own!

> [!TIP]
> In a prior exercise you already started Copilot CLI in the starter folder. You will use that to build your app! Return to the terminal in your codespace and select the first tab with Copilot CLI. Then use the following steps to help guide you through the process of building the app.

## 🎼 Step 1 - Create a product requirements doc

The more context you provide Copilot about what you're building, the better it's able to understand your approach and provide quality suggestions. The initial time you spend here will streamline future development. Creating a product requirements doc (PRD) is always a great first step.

Try a prompt like:

> *"I'm building a browser-based live-coding booth for music and visuals. It needs to render Hydra visuals, generate music in the browser, let me edit themes that bundle a visual + a musical mood, and accept natural-language prompts via the GitHub Copilot SDK. I'm starting from a blank repo. Draft a product requirements doc that covers the architecture, the key components, and a recommended build order for a one-hour hackathon. Save it to **docs/PRD.md**."*

Once you have a PRD, every future Copilot session has a north star to point at. Because this PRD will become central to what Copilot creates, spending some time adding requirements and context will help drive a better end result.

## 🧭 Step 2 - Pick your libraries with Copilot's help

Unsure about what libraries are needed or which ones are best? Don't know the first thing about how to create sounds or manage Hydra visualizations? Ask Copilot! It can not only answer your questions, but also identify which libraries will fit the bill.

Try a prompt like:

> *Given our PRD, what libraries would work best? Can you explore and find some options? Give me the top two for each category, and a brief explanation of why they work. We'll use this to decide which ones to implement."*

> [!TIP]
> Use this same energy throughout the lab! Not sure of what's available? Ask Copilot! Don't understand a block of code? Ask Copilot! Need to see if a feature is supported? Ask Copilot!

## 📝 Step 3 - Persist project context with instructions files

**/init** initializes instructions files in your project. Once Copilot scaffolds a **.github/copilot-instructions.md**, the root for your instructions, you can then **edit it** to describe your stack, conventions, libraries, and any "always do this / never do that" rules.

Try a prompt like:

> *"**/init** Update our instructions to capture: this is a TypeScript browser app using Hydra for visuals, [your music engine] for sound, [your editor] as the in-app code editor, and the **@github/copilot-sdk** for in-app AI prompts. Always use TypeScript, never put tokens in browser code, and prefer small focused modules where appropriate."*

The set list's Tips & tricks cover more on getting the most out of instructions files.

## 🎤 Step 4 - Plan and build

The old saying of "measure twice, cut once" absolutely applies to working with AI coding tools. Just as we took the time to create a PRD, taking the additional step to first plan then tell Copilot to build will help ensure you get the code you want the way you want it.

Don't try to scaffold the whole app at once; work in stages. Layer on audio, themes, and other features as you build.

> [!TIP]
> Being able to single shot an application is neither the goal nor some arbitrary gold standard of working with AI coding tools. You will always iterate, building in steps, like you've done all through your career. AI doesn't change the core fundamentals of creating code, it provides another tool in your toolbox.

Start with a plan! Then once that looks good ask Copilot to start building based on that plan. Something like:

> *"**/plan** Using the PRD in **docs/PRD.md** and the conventions in **.github/copilot-instructions.md**, identify and plan a good first feature to implement. Rubber duck this plan with another model to ensure we've got a good approach."*

Once you're past the scaffold, the loop opens up. As you keep iterating, lean on the moves from the set list:

- **Use /fleet** \- Spin up a subagent on themes while another updates the UI.
- **Lean on MCP servers** \- wire up the Playwright MCP server so Copilot can actually open your running app and confirm the canvas is rendering.
- **Use tests as your feedback loop** \- even one smoke test gives Copilot something objective to tune against\.
- **Pick the right model for the job** \- switch models with **/model** as the task shifts from architecture to implementation to debugging.

From here on out you're in the groove: prompt → run → tweak → prompt again.

## 🔁 Step 5 - Iterate

The goal is never "single shot/single prompt" where you have one golden piece of text you send to Copilot and magically create a fully featured product. That's not how development works, regardless of the tooling you're using. (And Copilot is, at the end of it all, a tool.) You'll build, iterate, redirect, prompt, and guide to the solution you're seeking.

## 🛠️ Tips & troubleshooting

A few moves that help you strike the right chord:

- To generate better music, try guiding Copilot to:
    - create a longer loop.
    - match a particular style of music you like.
    - refine based on the improvements you want to see.
- **Break things down into smaller chunks.** If you were creating code without the help of AI you'd likely create smaller components, each building on the one prior. Don't be afraid to do the same here! You could:
    - Create a "Hello, Copilot" page to ensure you can connect to Copilot SDK.
    - Add the browser-based code editor.
    - Incorporate visuals.
    - Play some music.
    - Refine as needed.
- **Split the SDK host from the browser frontend.** The Copilot SDK is a Node library (it shells out to the local Copilot CLI), so the cleanest shape is a small backend that hosts the SDK and a browser frontend that calls it over `fetch`. Streaming responses back to the page with Server-Sent Events keeps the UI feeling alive. Try a prompt like:

    > *"Create a small Node HTTP server in `server/` that exposes `POST /api/prompt` accepting `{ prompt }` as JSON, instantiates a `@github/copilot-sdk` client, runs the prompt as a streaming session, and streams the assistant's deltas back to the browser using Server-Sent Events. No framework - use the built-in `http` module. No auth code - the SDK piggybacks on the Copilot CLI I'm already logged into. Static-serve a `public/` folder from the same server with a minimal `index.html` that has a textarea, a Send button, and a div that fills in as the response streams."*
- **Model not available?** If a Copilot SDK call comes back with "model not available," your plan doesn't include that model. Pick a different one in the SDK call (or with `/model` inside Copilot CLI). `gpt-4.1` is a safe default for in-app prompting.
- **Have Copilot read the docs first.** When you're wiring up something unfamiliar, tell Copilot to fetch the source of truth before generating code. Cuts hallucination dramatically. Try a prompt like:

    > *"Before you write any code, fetch and read the README at https://github.com/github/copilot-sdk and the Node.js getting-started doc, then propose how we should structure the SDK integration. Don't touch any files until I sign off on the approach."*
- **Want a second opinion?** Ask Copilot to "rubber duck this with another model" - switching models is one of the cheapest ways to unstick the agent.

> [!TIP]
> When all else fails, ask Copilot!! (Yes, we know we keep saying this. But it's true!! If there's something you don't understand, want Copilot to look up, or updates that need to be made, tell Copilot!)

## ✅ Definition of done

You've shipped the lab when your app can:

- Render **Hydra visuals** live in the browser.
- Generate **music** in the browser, vibing with the visuals.
- Let someone **edit themes** that bundle a visual + a musical mood.
- **Add new themes from natural-language prompts** \- Copilot generates or updates the theme definition\.
- Embed **Copilot in the running app** via the GitHub Copilot SDK so the user can talk to it directly (e.g., *"make the visuals slower and bluer"*).

## Taking it to the streets

Congratulations! You built your app!! Not sure where to go from here? Select **Next** for some suggestions!

===

# 5. Take it on the road

## 🌟 Hungry for more?

If you've got the core working with time to spare, the set list's stretch ideas section has the full list. Quick recap of where to push next:

- **Save and share themes.** Persist them to `localStorage`, or encode them into the URL hash so a friend can open your vibe.
- **Author your own MCP server.** A small custom MCP server that, say, exposes a "generate theme" tool to Copilot.
- **Polish for production.** Error handling, mobile layout, accessibility. Make it something you'd actually ship.
- **Multi-buffer performance mode.** Two themes running side-by-side with a crossfader.

## 🏁 Wrap-up

In the final five minutes, we'll highlight the hackers with the:

- 🥇 **Fastest working POC** \- first to get visuals \+ music \+ editing in the browser\.
- 🎨 **Coolest looking environment** \- pure aesthetic glory\.
- 🏗️ **Most production-ready** \- the build that looks like it could ship Monday\.

## 🎓 Learnings

Some questions to take with you:

- Where did Copilot CLI shine? Where did it struggle?
- How did `/plan`, `/research`, and `/fleet` change how you worked?
- What instructions or context would you add to `.github/copilot-instructions.md` next time?

## 🚐 Take it on the road

When the lab wraps, the show doesn't have to stop. Keep leveling up your Copilot setup back at your day job - start with the [Awesome Copilot Learning Hub](https://awesome-copilot.github.com/learning-hub), a curated home for guides and tutorials covering agents, skills, instructions, hooks, agentic workflows, MCP servers, and the Copilot coding agent.

Other core resources worth bookmarking:

- [Awesome Copilot collection](https://awesome-copilot.github.com/) \- community\-built agents\, instructions\, skills\, hooks\, and plugins\. Full\-text search across hundreds of resources\.
- [GitHub Copilot documentation](https://docs.github.com/copilot) \- the canonical reference for everything Copilot\, across CLI\, IDE\, code review\, and cloud agent\.
- [GitHub Copilot CLI documentation](https://docs.github.com/copilot/concepts/agents/about-copilot-cli) \- deep on the CLI you just spent an hour with\.
- [GitHub Copilot SDK](https://github.com/github/copilot-sdk) \- for the next app you want to embed Copilot into\.
- [GitHub MCP Registry](https://github.com/mcp) \- discover MCP servers worth wiring into your next project\.
- [Copilot Memory](https://docs.github.com/en/copilot/concepts/agents/copilot-memory) \- let Copilot build up persistent\, repository\-scoped understanding of your codebase across sessions\.
- [Your next step after Build 2026](https://aka.ms/build26-next-steps) \- curated follow\-on from the Build team\.

