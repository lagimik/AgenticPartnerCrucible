# Public source review: issues #156 and #157

Captured: 2026-11-27. These are paraphrased review notes, not full article copies.
Issue provenance and original bodies are preserved separately in `issues.md`.

## #156: Agentic Loop

- Requested URL: https://aiappsgbb.github.io/agentic-loop/
- Retrieval: public HTML returned a React shell. Its title and description
  identify building with GitHub Copilot and running with Microsoft Foundry.
  The rendered portal was not independently inspected.
- Supporting source: public MIT-licensed `aiappsgbb/agentic-loop` repository,
  README retrieved through GitHub REST.
- Reviewed revision: `123d5d2d303d64f3b6725416d290ee990f1bbeae`
- Durable reference: https://github.com/aiappsgbb/agentic-loop/blob/123d5d2d303d64f3b6725416d290ee990f1bbeae/README.md

The README describes customer workshop preparation, reusable guidance and a
Foundry Agentic Loop build plugin. Rapid mode starts with an existing Foundry
project and verifies locally before separately approved deployment. Spec-driven
development starts with a brief and Azure subscription, using Specify,
Implement, Verify and Deploy phases, fresh-context review and bounded fixes.
The production feedback loop observes, evaluates, improves and redeploys.

The source assigns runtime-skills agents to the Copilot SDK and basic agents
or explicit workflows to Microsoft Agent Framework. It calls for clarification
when a workflow also needs skills and one framework per agent. Hosted agents,
models, identity, governed MCP tools and observability form its reference
approach; it is not the same offering as Foundry's managed prompt-agent harness.

The README says browser workshop preparation does not require cloning,
installation or Copilot sign-in. Builds separately require authenticated Azure
access, permissions, approved data and model capacity; billable deployment needs
approval. It explicitly distinguishes a workshop pilot from production readiness.
These are repository-described behaviors, not execution results from this review.
Plugin contents, linked guides, live deployment, model availability, privacy
implementation and product release status were not independently verified.

Partner interpretation: use the resource for scoped discovery and evidence-gated
delivery, not to certify an architecture or promise production readiness.

## #157: Art of play in the age of AI

- Source: https://github.blog/news-insights/company-news/art-of-play-in-the-age-of-ai/
- Publisher: GitHub Blog
- Authors: Polly Davidson and Cassidy Williams
- Published: November 25, 2026
- Retrieval: full public article text reviewed.

The article uses GitHub Universe hackable badges and a Copilot-assisted
accelerometer/pedometer experiment to illustrate small, curiosity-led projects.
It recommends a time limit, human inspection, debugging and testing, and care
for maintainers before submitting AI-assisted open-source contributions:
understand contribution guidance, existing issues and project needs.

The article links Octoverse agent-started pull-request figures, but the underlying
report was not reviewed and the figures are not retained as validated evidence.
Badge examples are anecdotes, not a controlled productivity or learning study.
Linked podcast, keynote, badge software and shopping destinations were not
reviewed; promotional offers are excluded from durable knowledge.

Partner interpretation: use bounded experiments for developer skilling, with
approved inputs and reviewable results. Do not infer enterprise readiness,
business ROI or measured learning gains from a successful personal prototype.
