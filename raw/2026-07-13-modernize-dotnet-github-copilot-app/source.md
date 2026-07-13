# Modernize .NET in the GitHub Copilot App

**Source:** https://devblogs.microsoft.com/dotnet/modernize-dotnet-in-github-copilot-app/
**Captured:** 2026-07-13
**Issue:** lagimik/AgenticPartnerCrucible#2

---

Upgrading a .NET application isn't a single prompt.

Every upgrade begins with understanding your application, evaluating dependencies, planning the work, applying code transformations, fixing build failures, and validating the results. Each phase uncovers new information that shapes the work that follows. A dependency update can uncover compatibility issues, a build failure can change the next task, and dependencies between projects can change the order of work.

GitHub Copilot upgrade carries out that workflow. The GitHub Copilot upgrade agent assesses your application, generates a structured upgrade plan, creates implementation tasks, and executes the work.

Now you can follow that workflow in the GitHub Copilot app through an interactive upgrade canvas. Instead of piecing together progress across chat, generated Markdown artifacts, and code changes, the upgrade canvas gives you a live view of the modernization workflow as it unfolds.

The result is a .NET modernization experience that's easier to follow, easier to review, and easier to steer.

## From assessment to execution

The GitHub Copilot upgrade agent starts by assessing your .NET application and identifying what needs to change:

- What version of .NET is this application targeting?
- Which NuGet packages need to be updated?
- Are there breaking API changes?
- Which projects can be upgraded independently?
- What should happen first?

From there, the agent generates a structured upgrade plan and breaks the work into actionable implementation tasks. As execution begins, the canvas reflects the latest state of the upgrade, including the assessment, upgrade plan, implementation tasks, execution progress, code changes, build failures, and final results.

## Available wherever you work

While the GitHub Copilot app provides the interactive upgrade canvas, GitHub Copilot upgrade is also available across the developer tools you already use:

- **Visual Studio** – Built directly into Visual Studio. Right-click your solution or project in Solution Explorer and select Modernize to start a .NET upgrade.
- **Visual Studio Code** – Install the GitHub Copilot upgrade extension, select the Upgrade agent from the agent picker dropdown, and prompt it to modernize your .NET application.
- **GitHub Copilot CLI** – Install the GitHub Copilot upgrade plugin to assess, plan, and execute .NET upgrades directly from the terminal.

## Get started

1. Add the GitHub Copilot upgrade marketplace (microsoft/upgrade-agent-plugins).
2. In the Add plugin marketplace? dialog, select Allow.
3. In the Plugins window, select Add marketplace.
4. Select Install for the upgrade-agent plugin.
5. Open your repository, start a new agent session, and select the Upgrade agent from the agent picker dropdown.

To open the interactive upgrade canvas:

1. In the upper-right corner of the GitHub Copilot app, select the review panel icon (Toggle review panel).
2. In the review panel, select + (Open in panel).
3. Choose Upgrade Dashboard.

The Upgrade Dashboard opens an interactive upgrade canvas where you can assess your application, review the upgrade plan, track execution, and monitor your modernization effort from start to finish.

Repository: https://github.com/microsoft/upgrade-agent-plugins
