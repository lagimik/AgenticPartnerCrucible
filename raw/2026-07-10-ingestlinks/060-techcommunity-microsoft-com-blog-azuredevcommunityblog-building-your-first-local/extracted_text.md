Microsoft Community Hub

Communities Products

Microsoft Developer Community Blog

Building Your First Local RAG Application with Foundry Local

A developer's guide to building an offline, mobile-responsive AI support agent using Retrieval-Augmented Generation, the Foundry Local SDK, and JavaScript.

Imagine you are a gas field engineer standing beside a pipeline in a remote location. There is no Wi-Fi, no mobile signal, and you need a safety procedure right now. What do you do?

This is the exact problem that inspired this project: a fully offline RAG-powered support agent that runs entirely on your machine. No cloud. No API keys. No outbound network calls. Just a local language model, a local vector store, and your own documents, all accessible from a browser on any device.

In this post, you will learn how it works, how to build your own, and the key architectural decisions behind it. If you have ever wanted to build an AI application that runs locally and answers questions grounded in your own data, this is the place to start.

The finished application: a browser-based AI support agent that runs entirely on your machine.

What Is Retrieval-Augmented Generation?

Retrieval-Augmented Generation (RAG) is a pattern that makes AI models genuinely useful for domain-specific tasks. Rather than hoping the model "knows" the answer from its training data, you:

Retrieve relevant chunks from your own documents using a vector store

Augment the model's prompt with those chunks as context

Generate a response grounded in your actual data

The result is fewer hallucinations, traceable answers with source attribution, and an AI that works with your content rather than relying on general knowledge.

If you are building internal tools, customer support bots, field manuals, or knowledge bases, RAG is the pattern you want.

RAG vs CAG: Understanding the Trade-offs

If you have explored AI application patterns before, you have likely encountered Context-Augmented Generation (CAG) . Both RAG and CAG solve the same core problem: grounding an AI model's answers in your own content. They take different approaches, and each has genuine strengths and limitations.

How it works: Documents are split into chunks, vectorised, and stored in a database. At query time, the most relevant chunks are retrieved and injected into the prompt.

Scales to thousands or millions of documents

Fine-grained retrieval at chunk level with source attribution

Documents can be added or updated dynamically without restarting

Token-efficient: only relevant chunks are sent to the model

Supports runtime document upload via the web UI

More complex architecture: requires a vector store and chunking strategy

Retrieval quality depends on chunking parameters and scoring method

May miss relevant content if the retrieval step does not surface it

How it works: All documents are loaded at startup. The most relevant ones are selected per query using keyword scoring and injected into the prompt.

Drastically simpler architecture with no vector database or embeddings

All information is always available to the model

Minimal dependencies and easy to set up

Near-instant document selection

Constrained by the model's context window size

Best suited to small, curated document sets (tens of documents)

Adding documents requires an application restart

Want to compare these patterns hands-on? There is a CAG-based implementation of the same gas field scenario using whole-document context injection. Clone both repositories, run them side by side, and see how the architectures differ in practice.

When Should You Choose Which?

For the sample application in this post (20 gas engineering procedure documents with runtime upload), RAG is the clear winner. If your document set is small and static, CAG may be simpler. Both patterns run fully offline using Foundry Local.

Foundry Local: Your On-Device AI Runtime

Foundry Local is a lightweight runtime from Microsoft that downloads, manages, and serves language models entirely on your device. No cloud account, no API keys, no outbound network calls (after the initial model download).

What makes it particularly useful for developers:

No GPU required : runs on CPU or NPU, making it accessible on standard laptops and desktops

Native SDK bindings : in-process inference via the foundry-local-sdk npm package, with no HTTP round-trips to a local server

Automatic model management : downloads, caches, and loads models automatically

Hardware-optimised variant selection : the SDK picks the best variant for your hardware (GPU, NPU, or CPU)

Real-time progress callbacks : ideal for building loading UIs that show download and initialisation progress

The integration code is refreshingly minimal:

That is it. No server configuration, no authentication tokens, no cloud provisioning. The model runs in the same process as your application.

The Technology Stack

The sample application is deliberately simple. No frameworks, no build steps, no Docker:

The total dependency footprint is three npm packages: express , foundry-local-sdk , and better-sqlite3 .

Architecture Overview

The five-layer architecture, all running on a single machine.

The system has five layers, all running on a single machine:

Client layer: a single HTML file served by Express, with quick-action buttons and a responsive chat interface

Server layer: Express.js starts immediately and serves the UI plus SSE status and chat endpoints

RAG pipeline: the chat engine orchestrates retrieval and generation; the chunker handles TF-IDF vectorisation; the prompts module provides safety-first system instructions

Data layer: SQLite stores document chunks and their TF-IDF vectors; documents live as .md files in the docs/ folder

AI layer: Foundry Local runs Phi-3.5 Mini on CPU or NPU via native SDK bindings

Building the Solution Step by Step

You need two things installed on your machine:

Node.js 20 or later: download from nodejs.org

Foundry Local: Microsoft's on-device AI runtime: winget install Microsoft.FoundryLocal

The SDK will automatically download the Phi-3.5 Mini model (approximately 2 GB) the first time you run the application.

Getting the Code Running

Open http://127.0.0.1:3000 in your browser. You will see the status indicator whilst the model loads. Once the model is ready, the status changes to "Offline Ready" and you can start chatting.

How the RAG Pipeline Works

Let us trace what happens when a user asks: "How do I detect a gas leak?"

The query flow from browser to model and back.

When you run npm run ingest , every .md file in the docs/ folder is read, parsed (with optional YAML front-matter for title, category, and ID), split into overlapping chunks of approximately 200 tokens, and stored in SQLite with TF-IDF vectors.

The Foundry Local SDK discovers the model in the local catalogue and loads it into memory. If the model is not already cached, it downloads it first (with progress streamed to the browser via SSE).

The question arrives at the Express server. The chat engine converts it into a TF-IDF vector, uses an inverted index to find candidate chunks, and scores them using cosine similarity. The top 3 chunks are returned in under 1 ms.

The engine builds a messages array containing: the system prompt (with safety-first instructions), the retrieved chunks as context, the conversation history, and the user's question.

The prompt is sent to the locally loaded model via the Foundry Local SDK's native chat client. The response streams back token by token through Server-Sent Events to the browser. Source references with relevance scores are included.

A response with safety warnings and step-by-step guidance

The sources panel shows which chunks were used and their relevance

Key Code Walkthrough

The Vector Store (TF-IDF + SQLite)

The vector store uses SQLite to persist document chunks alongside their TF-IDF vectors. At query time, an inverted index finds candidate chunks that share terms with the query, then cosine similarity ranks them:

The inverted index, in-memory row cache, and prepared SQL statements bring retrieval time to sub-millisecond for typical query loads.

Why TF-IDF Instead of Embeddings?

Most RAG tutorials use embedding models for retrieval. This project uses TF-IDF because:

Fully offline: no embedding model to download or run

Zero latency: vectorisation is instantaneous (it is just maths on word frequencies)

Good enough: for 20 domain-specific documents, TF-IDF retrieves the right chunks reliably

Transparent: you can inspect the vocabulary and weights, unlike neural embeddings

For larger collections or when semantic similarity matters more than keyword overlap, you would swap in an embedding model. For this use case, TF-IDF keeps the stack simple and dependency-free.

For safety-critical domains, the system prompt is engineered to prioritise safety, prevent hallucination, and enforce structured responses:

This pattern is transferable to any safety-critical domain: medical devices, electrical work, aviation maintenance, or chemical handling.

Runtime Document Upload

Unlike the CAG approach, RAG supports adding documents without restarting the server. Click the upload button to add new .md or .txt files. They are chunked, vectorised, and indexed immediately.

The upload modal with the complete list of indexed documents.

Adapting This for Your Own Domain

The sample project is designed to be forked and adapted. Here is how to make it yours in four steps:

1. Replace the documents

Delete the gas engineering documents in docs/ and add your own markdown files. The ingestion pipeline handles any markdown content with optional YAML front-matter:

2. Edit the system prompt

Open src/prompts.js and rewrite the system prompt for your domain. Keep the structure (summary, safety, steps, reference) and update the language to match your users' expectations.

3. Tune the retrieval

chunkSize: 200 : smaller chunks give more precise retrieval, less context per chunk

chunkOverlap: 25 : prevents information falling between chunks

topK: 3 : how many chunks to retrieve per query (more gives more context but slower generation)

Change config.model in src/config.js to any model available in the Foundry Local catalogue. Smaller models give faster responses on constrained devices; larger models give better quality.

Building a Field-Ready UI

The front end is a single HTML file with inline CSS. No React, no build tooling, no bundler. This keeps the project accessible to beginners and easy to deploy.

Design decisions that matter for field use:

Dark, high-contrast theme with 18px base font size for readability in bright sunlight

Large touch targets (minimum 44px) for operation with gloves or PPE

Quick-action buttons that wrap on mobile so all options are visible without scrolling

Responsive layout that works from 320px to 1920px+ screen widths

Streaming responses via SSE, so the user sees tokens arriving in real time

The mobile chat experience, optimised for field use.

The project includes unit tests using the built-in Node.js test runner, with no extra test framework needed:

Tests cover the chunker, vector store, configuration, and server endpoints. Use them as a starting point when you adapt the project for your own domain.

Ideas for Extending the Project

Once you have the basics running, there are plenty of directions to explore:

Embedding-based retrieval: use a local embedding model for better semantic matching on diverse queries

Conversation memory: persist chat history across sessions using local storage or a lightweight database

Multi-modal support: add image-based queries (photographing a fault code, for example)

PWA packaging: make it installable as a standalone offline application on mobile devices

Hybrid retrieval: combine TF-IDF keyword search with semantic embeddings for best results

Try the CAG approach: compare with the local-cag sample to see which pattern suits your use case

Ready to Build Your Own?

Clone the RAG sample, swap in your own documents, and have an offline AI agent running in minutes. Or compare it with the CAG approach to see which pattern suits your use case best.

Building a local RAG application does not require a PhD in machine learning or a cloud budget. With Foundry Local, Node.js, and SQLite, you can create a fully offline, mobile-responsive AI agent that answers questions grounded in your own documents.

RAG is ideal for scalable, dynamic document sets where you need fine-grained retrieval with source attribution. Documents can be added at runtime without restarting.

CAG is simpler when you have a small, stable set of documents that fit in the context window. See the local-cag sample to compare.

Foundry Local makes on-device AI accessible: native SDK bindings, in-process inference, automatic model selection, and no GPU required.

TF-IDF + SQLite is a viable vector store for small-to-medium collections, with sub-millisecond retrieval thanks to inverted indexing and in-memory caching.

Start simple, iterate outwards. Begin with RAG and a handful of documents. If your needs are simpler, try CAG. Both patterns run entirely offline.

Clone the repository, swap in your own documents, and start building. The best way to learn is to get your hands on the code.

This project is open source under the MIT licence. It is a scenario sample for learning and experimentation, not production medical or safety advice.

local-rag on GitHub · local-cag on GitHub · Foundry Local

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