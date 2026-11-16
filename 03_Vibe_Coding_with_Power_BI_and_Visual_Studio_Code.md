# 3. Vibe Coding with Power BI and Visual Studio Code

[Back to agenda](./Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [3.1 Agentic Power BI Development Workflow](#31-agentic-power-bi-development-workflow)
- [3.2 Build Fabric Apps: From Quickstart to GitHub Copilot](#32-build-fabric-apps-from-quickstart-to-github-copilot)
- [3.3 Optional Paths: Notebook Authoring and Embedded Analytics](#33-optional-paths-notebook-authoring-and-embedded-analytics)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. 🛠️ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

**Teaching note:** Start with the agentic Power BI workflow to establish development concepts, validation, and deployment practices. Then follow the separate Fabric app track: scaffold a first app before building a Copilot-assisted app connected to a semantic model. The app exercises build applications, not PBIR reports. Notebook authoring and Power BI Embedded are optional related paths, not prerequisites for the app exercises.

## 3.1 Agentic Power BI Development Workflow

- **Agentic Power BI development on Windows** — [Vibe Coding with Power BI on Windows](./06-vibe-coding-power-bi-windows.en.md) — **Training material:** covers VS Code, PBIP, TMDL, PBIR, agentic workflows, validation, and deployment, including alternatives when MCP is prohibited.

## 3.2 Build Fabric Apps: From Quickstart to GitHub Copilot

- **Rayfin** — [Rayfin](https://rayfin.ai/) — **External product website:** related reference for the Rayfin-based Fabric apps workflow below; not a guided exercise. The website could not be retrieved during this review.

- **Rayfin guidance and ready-to-run examples** — [awesome-rayfin (FindusHH)](https://github.com/FindusHH/awesome-rayfin) — **Curated examples and reference collection:** covers Rayfin in depth and is based on [Microsoft's awesome-rayfin repository](https://github.com/microsoft/awesome-rayfin). It contains only a subset of the upstream collection, but the included examples have been updated to be ready to run. Follow each example's documented setup instructions and prerequisites.

- 🛠️ **Create your first Fabric app** — [Create your first Fabric apps project](https://learn.microsoft.com/en-us/fabric/apps/create-app) — **Hands-on quickstart (preview):** scaffold an app with the Rayfin tooling, deploy its backend to Fabric, and run the frontend locally. Requires Node.js 20 or later, suitable workspace permissions, and the Fabric apps tenant setting.

- 🛠️ **Create a semantic model app with GitHub Copilot** — [Create a semantic model app with GitHub Copilot](https://learn.microsoft.com/en-us/fabric/apps/create-app-with-github-copilot) — **Hands-on tutorial:** use GitHub Copilot agent mode in VS Code to scaffold an analytical app, connect a Fabric semantic model, generate DAX and visualizations, validate changes, and deploy to Fabric. This builds an app connected to a semantic model rather than a PBIR report.

## 3.3 Optional Paths: Notebook Authoring and Embedded Analytics

- **Fabric notebooks in VS Code** — [Create and manage Fabric notebooks in VS Code](https://learn.microsoft.com/en-us/fabric/data-engineering/author-notebook-with-vs-code) — **Practical how-to:** use the Fabric Data Engineering extension to create, edit, synchronize, and run notebooks from VS Code.

- **Power BI Embedded** — [Embedded analytics documentation](https://learn.microsoft.com/en-us/power-bi/developer/embedded/) — **Documentation hub:** explore embedding Power BI analytics in applications; a related application-development path, not a single hands-on tutorial.

[Back to contents](#chapter-contents)

[Back to agenda](./Agenda%20with%20Tutorials.md)
