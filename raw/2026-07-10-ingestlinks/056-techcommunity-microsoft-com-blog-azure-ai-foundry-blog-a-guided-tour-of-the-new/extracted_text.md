Microsoft Community Hub

Communities Products

Microsoft Foundry Blog

A Guided Tour of the New Microsoft Foundry Labs

Where You Can Build with Microsoft's Boldest AI Experiments

There's a moment every developer chases — the first time you take something genuinely at the edge of what's possible and watch it run on your screen, against your problem. Microsoft Foundry Labs exists to give you that moment on repeat.

This is the place where Microsoft's most ambitious AI research stops being a headline and becomes something you can click, run, fork, and ship. Frontier models for computer use, biomolecular structure prediction, real-time 3D generation, multilingual speech — they're not locked behind a paper or a waitlist. They're live, they're interactive, and a lot of them are one button away from your next project. Let's walk through what's waiting for you.

The mission: closing the gap between research and reality

Foundry Labs starts from a conviction stated plainly on its About page : AI advances fast, and access to it should too. Historically, the distance between a breakthrough research paper and real-world impact has been far too wide — months or years of reimplementation between the idea and anyone actually using it.

Labs is built to close that gap. It takes experiments straight out of Microsoft's labs and puts them directly in the hands of builders and researchers, framed around three moves: discover what's at the frontier, experiment with it hands-on, and connect with the people pushing it forward.

And the work isn't scattered randomly — it concentrates in six domains where AI is having outsized real-world impact:

Pick the domain that maps to your work, and Labs becomes a map of the frontier in your field.

Featured and fresh: the homepage

The homepage opens with "Breakthrough AI you can try today" — a rotating showcase of the experiments worth knowing about right now, each with a Try it now button straight into Microsoft Foundry and a Learn more link for the deep dive. A quick look at the marquee:

MAI-Image-2.5 — Microsoft AI's image-generation model with image-to-image editing and "control with preservation," a recent No. 2 debut for editing capabilities among image-model families on Arena.ai.

MAI-Thinking-1 — Microsoft AI's first large language model, tuned for strong reasoning and math at a fraction of frontier-scale cost.

MagenticLite — an open-source agentic app for small models and the successor to Magentic-UI, pairing the MagenticBrain orchestrator with Fara 1.5 to run autonomously and transparently on your own hardware.

Fara 1.5 — Microsoft's agentic small language models for computer use, perceiving the screen from screenshots and predicting clicks directly.

EO/OS Object Detection — a first-party Earth Observation model that detects and localizes objects in satellite and aerial imagery at petabyte scale, anchoring the new GeoAI category alongside the Planetary Computer team.

Scroll on and the "Just added to Labs" strip keeps a finger on the pulse, surfacing the newest arrivals — recently VibeVoice ASR, MAI-Image-2-Efficient, Magentic Marketplace, and BugPilot. It's the fastest way to see what shipped this week without going hunting.

Going deeper: the Innovations catalog

The homepage is the highlight reel; the Innovations tab is the whole library — 50+ experiments and growing, built from frontier research and available to you today. The images across the experience are generated using Microsoft’s in-house MAI image models.

This is where the experience really opens up, because you're not stuck scrolling. You can filter and sort the entire catalog to cut straight to what matters to you — narrow by the six domains, by what's newest, or by the kind of artifact you're after. Hunting for a vision model in Creative & Generative Media? A production-ready framework in Code & Software Engineering? A few clicks and the list is exactly your shortlist. Each result opens onto its own page, where the experiment goes from a name to something you can understand and try.

A closer look: TRELLIS

To see what one of those pages actually delivers, open Trellis — and it's a great one to start with, because it doesn't just describe the model, it lets you use it on the spot.

An interactive playground, right on the page. TRELLIS turns a single image (or a text prompt) into a fully textured 3D asset, and the page gives you a live playground to do exactly that. Drop in an image, tune the parameters — latent and sparse-structure CFG scale, sampling steps, seed — hit Generate 3D Model , and preview the result. When you like it, export a GLB and pull it straight into your pipeline. No setup, no notebook, no GPU of your own.

The substance behind the demo. Below the playground, the page lays out what makes TRELLIS notable. It's built on a novel Structured LATent (SLat) representation with rectified-flow transformers scaled to 2 billion parameters, trained on 500,000 diverse 3D objects. Its trick is decoupling the latent from the decoder, so a single model can output meshes, radiance fields, and 3D Gaussians — pick the format your pipeline needs without retraining. It can go from one image to a textured mesh in under 10 seconds on a single A100, supports local editing that changes specific 3D regions while preserving the rest, and was adopted by NVIDIA AI Blueprints in September 2025. (The usage counter on the page — north of 2.4 million users — tells you it's resonating.)

Everything you need to go further. Clear tags label it (Creative & Generative Media · Model · Vision · Experimental), the technology stack is spelled out (PyTorch, diffusion models, NeRF, 3D Gaussians, CUDA), and a "Ready to Explore?" section links you to the GitHub repo , the research paper , and the project blog. That's the full arc on one page: try it, understand it, then take the code.

Every experiment page follows this same shape — so once you've explored TRELLIS, you know how to read any of them.

Proof it works: Customer Stories

Trying a model is exciting; betting a product on it takes evidence. That's what the Stories page delivers — accounts from teams who took Labs experiments into production and came back with hard numbers.

Space Intelligence — A UK-based organization mapping the world’s forests. By combining Microsoft Foundry with the Microsoft Planetary Computer, they increased data production 100× and reduced forest mapping timelines from six months to six weeks (a 75% reduction), covering 3 billion hectares across 50+ countries in a single year.

Sight Machine — Achieved a 10% lift in manufacturing productivity using Foundry-powered capabilities.

Commerzbank — Scaled to 30,000 customer conversations per month on Foundry Agent Service.

MediaTek — Delivered 50% faster on-device AI performance using Phi models.

If you're building a case for adoption, these are concrete signals of impact. And if you've shipped something with Labs, you can submit your own story to be featured.

Better together: Community

Great tools build communities, and the Community page is where 25,000+ developers and researchers gather under a simple banner: build together, think further. It brings three things into one place:

An events calendar — where the Foundry team and community will be, from Microsoft Build and Ignite to the KubeCon circuit, GitHub Universe, and NeurIPS, each with a registration link so you can plan to meet up in person.

The latest from the labs — a feed of blogs and publications straight from the teams behind the experiments, so you follow the research as it unfolds.

The conversation — direct lines into Discord, Reddit, the Microsoft Research Blog, and Tech Community, where you can ask questions, swap ideas, and watch your feedback help steer what comes next.

Foundry Labs is the shortest path from Microsoft's most ambitious research to something running in front of you. The frontier is open, the experiments are live, and the community is already building. Go explore it — and tell us what you create.

Surface Laptop Studio 2

Copilot for organizations

Copilot for personal use

Explore Microsoft products

Microsoft Store support

Certified Refurbished

Microsoft Store Promise

Microsoft in education

Devices for education

Microsoft Teams for Education

Microsoft 365 Education

How to buy for your school

Educator training and development

Deals for students and parents

Microsoft Power Platform

Microsoft 365 Copilot

Support for AI marketplace apps

Microsoft Tech Community

Microsoft Marketplace

Privacy at Microsoft

Diversity and inclusion