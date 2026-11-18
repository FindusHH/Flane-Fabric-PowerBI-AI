# 10. Fabric Apps with Rayfin

[Back to agenda](./00_Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [10.1 Rayfin Overview and Ready-to-Run Examples](#101-rayfin-overview-and-ready-to-run-examples)
- [10.2 Build Fabric Apps: From Quickstart to GitHub Copilot](#102-build-fabric-apps-from-quickstart-to-github-copilot)
- [10.3 When to Use Fabric Apps](#103-when-to-use-fabric-apps)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. ⭐ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

**Hands-on tutorials at a glance**

| Hands-on tutorial | Section | Focus |
| --- | --- | --- |
| ⭐ <a href="https://learn.microsoft.com/en-us/fabric/apps/create-app" target="_blank" rel="noopener noreferrer">Create your first Fabric app</a> | [10.2 Build Fabric Apps: From Quickstart to GitHub Copilot](#102-build-fabric-apps-from-quickstart-to-github-copilot) | Scaffold an app with Rayfin tooling, deploy its backend to Fabric, and run the frontend locally. |
| ⭐ <a href="https://learn.microsoft.com/en-us/fabric/apps/create-app-with-github-copilot" target="_blank" rel="noopener noreferrer">Create a semantic model app with GitHub Copilot</a> | [10.2 Build Fabric Apps: From Quickstart to GitHub Copilot](#102-build-fabric-apps-from-quickstart-to-github-copilot) | Use GitHub Copilot in VS Code to build and deploy an analytical app connected to a Fabric semantic model. |

**Teaching note:** Start with the Fabric Apps overview, the Rayfin website, and the example collections, then scaffold a first app before building a Copilot-assisted app connected to a semantic model. The app exercises build applications, not PBIR reports.

## 10.1 Rayfin Overview and Ready-to-Run Examples

- **Fabric Apps overview** — <a href="https://learn.microsoft.com/en-us/fabric/apps/overview" target="_blank" rel="noopener noreferrer">What are Fabric Apps?</a> — **Overview/reference:** explains how Fabric Apps, built on the Rayfin SDK, turn TypeScript data models into generated APIs with authentication, hosting, Fabric data connectors, and file storage. Also covers supported regions and licensing/workspace prerequisites.

- **Rayfin** — [Rayfin](https://rayfin.ai/) — **Product website and documentation:** introduces Rayfin as a TypeScript backend platform that deploys to Microsoft Fabric, with a CLI quickstart, agent-ready setup instructions, and reference documentation. Not a guided exercise.

- **Microsoft awesome-rayfin** — [awesome-rayfin (Microsoft)](https://github.com/microsoft/awesome-rayfin) — **Curated examples and reference collection:** the original Microsoft collection of Rayfin resources and examples.

- **Updated ready-to-run examples** — [awesome-rayfin (FindusHH)](https://github.com/FindusHH/awesome-rayfin) — **Curated examples and reference collection:** based on the Microsoft repository above; contains only a subset of the upstream collection, but the included examples have been updated to be ready to run. Follow each example's documented setup instructions and prerequisites.

## 10.2 Build Fabric Apps: From Quickstart to GitHub Copilot

- ⭐ **Create your first Fabric app** — <a href="https://learn.microsoft.com/en-us/fabric/apps/create-app" target="_blank" rel="noopener noreferrer">Create your first Fabric apps project</a> — **Hands-on quickstart (preview):** scaffold an app with the Rayfin tooling, deploy its backend to Fabric, and run the frontend locally. Requires Node.js 20 or later, suitable workspace permissions, and the Fabric apps tenant setting.

- ⭐ **Create a semantic model app with GitHub Copilot** — <a href="https://learn.microsoft.com/en-us/fabric/apps/create-app-with-github-copilot" target="_blank" rel="noopener noreferrer">Create a semantic model app with GitHub Copilot</a> — **Hands-on tutorial:** use GitHub Copilot agent mode in VS Code to scaffold an analytical app, connect a Fabric semantic model, generate DAX and visualizations, validate changes, and deploy to Fabric. This builds an app connected to a semantic model rather than a PBIR report.

## 10.3 When to Use Fabric Apps

Fabric Apps are a good fit for:

- **Prototypes:** Develop and deploy an initial application quickly using the provided infrastructure.
- **Internal tools and dashboards:** Create authenticated administrative interfaces without building all backend services from scratch.
- **Data exploration and visualization:** Query supported Fabric data sources through connectors and present results in a custom frontend.
- **AI and agent applications:** Provide backend services and persistent state for applications that use AI agents.

Consider alternatives when an application requires complex multi-step transactions or stored procedures, or when it needs authentication providers beyond the supported options. Deployed Fabric Apps use Fabric SSO; email and password are available for local development.

**Source:** <a href="https://learn.microsoft.com/en-us/fabric/apps/overview#when-to-use-fabric-apps" target="_blank" rel="noopener noreferrer">When to use Fabric Apps</a> — **Overview/reference:** use cases and scenarios where Fabric Apps might not be suitable.

[Back to contents](#chapter-contents)

[Back to agenda](./00_Agenda%20with%20Tutorials.md)
