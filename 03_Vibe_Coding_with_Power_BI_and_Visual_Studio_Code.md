# 3. Vibe Coding with Power BI and Visual Studio Code

[Back to agenda](./00_Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [3.1 Learning Goals and Workflow](#31-learning-goals-and-workflow)
- [3.2 Choose the Windows Development Environment](#32-choose-the-windows-development-environment)
- [3.3 Understand PBIP, PBIR, and TMDL](#33-understand-pbip-pbir-and-tmdl)
- [3.4 Select Agent Tools and an MCP Policy](#34-select-agent-tools-and-an-mcp-policy)
- [3.5 Prepare a Project and Plan Changes](#35-prepare-a-project-and-plan-changes)
- [3.6 Develop and Test the Semantic Model](#36-develop-and-test-the-semantic-model)
- [3.7 Design and Validate a PBIR Report](#37-design-and-validate-a-pbir-report)
- [3.8 Query a Published Model (Optional)](#38-query-a-published-model-optional)
- [3.9 Quality, Security, and Governance](#39-quality-security-and-governance)
- [3.10 Review and Deploy Changes](#310-review-and-deploy-changes)
- [3.11 Optional: Notebook Authoring and Embedded Analytics](#311-optional-notebook-authoring-and-embedded-analytics)
- [3.12 Optional: One-Day Workshop Plan](#312-optional-one-day-workshop-plan)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. 🛠️ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

**Teaching note:** This chapter integrates the Windows training material into one development path. First understand the tools and project formats, then prepare a baseline, work on the model, build the report, validate, and deploy. AI agents, MCP, published-data queries, and the one-day schedule are optional extensions. The separate [Fabric Apps with Rayfin](./10_Fabric_Apps_with_Rayfin.md) chapter builds applications rather than PBIR reports.

## 3.1 Learning Goals and Workflow

Here, **vibe coding** means describing a goal in natural language and using an AI coding assistant to propose or make reviewable changes to a Power BI project. It is a workshop term, not the name of a Power BI product. The developer remains responsible for business rules, permissions, testing, and approval.

Participants should be able to:

- distinguish the project, report, and semantic model formats **PBIP**, **PBIR**, and **TMDL**;
- select an appropriate combination of Power BI Desktop, VS Code, Git, and optional agent tools;
- plan and implement a small model or report change, with or without MCP;
- test DAX results and visually review the report before approving changes; and
- review a Git diff and deploy to a nonproduction Fabric workspace in a controlled way.

The teaching sequence is **requirements → baseline → model inspection → plan → model and DAX → report → validation → review and deployment**. It follows the data-to-model-to-report-to-publishing progression in the Microsoft Learn tutorial in section 3.5, with additional version-control and approval gates. GitHub Copilot in VS Code is a coding assistant; Copilot in Power BI is a separate product experience with its own prerequisites. See [Chapter 1](./01_Copilot_in_Power_BI_Reports_and_DAX.md) for the latter.

## 3.2 Choose the Windows Development Environment

| Tool | Role in this workshop |
| --- | --- |
| **Power BI Desktop** | Load data, edit and run the semantic model, render reports, and review results. The complete local workflow uses Windows; check Microsoft's [download and minimum requirements](https://learn.microsoft.com/en-us/power-bi/fundamentals/desktop-get-the-desktop#minimum-requirements). |
| **Visual Studio Code** | Inspect PBIP files, edit supported TMDL and PBIR files, use Git, and optionally work with an approved AI agent. |
| **Git** | Store a baseline, create a feature branch, review text diffs, and support rollback. |
| **GitHub Copilot and optional Power BI agent tools** | Assist with plans and changes when the organization permits their use and the required access is available. The exercises can also be performed manually. |
| **Visual Studio with Analysis Services Projects** | Optional specialist environment for tabular/SSDT projects and XMLA-based model work; it is not a Power BI report designer. See [Analysis Services tools](https://learn.microsoft.com/en-us/analysis-services/tools-and-applications-used-in-analysis-services) and [XMLA endpoint requirements](https://learn.microsoft.com/en-us/fabric/enterprise/powerbi/service-premium-connect-tools). |

Use a current Power BI Desktop release, a test model without confidential data, and an isolated development workspace when publishing. Suitable GitHub Copilot access, tenant settings, workspace permissions, licenses, and capacity depend on the selected optional tools and deployment path. DAX Studio, Tabular Editor, and ALM Toolkit are optional tools, subject to organizational approval.

## 3.3 Understand PBIP, PBIR, and TMDL

| Artifact | What it represents | Why it matters |
| --- | --- | --- |
| **PBIX** | A Power BI Desktop file containing a report and model and, when applicable, imported data. | Convenient for Desktop, but a single file is less suitable for line-by-line Git review. |
| **PBIP** | A **Power BI Project**: a folder of report and semantic model definitions. The `.pbip` file points to a report folder; it is not the whole project by itself. | Text-based project files support source control and collaboration. See [Power BI Desktop projects](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-overview). |
| **PBIR** | The **Power BI enhanced report format** stores report definitions such as pages, visuals, bookmarks, and formatting as structured JSON files. `definition.pbir` contains report settings and a reference to its semantic model; the report definition is in the `definition` folder. | Supports schema-aware editing and smaller report diffs. See the [report folder and PBIR format](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-report#pbir-format). |
| **TMDL** | **Tabular Model Definition Language** is a text representation of semantic model metadata, including tables, columns, relationships, measures, and roles. DAX expressions can be part of a measure definition. | Makes model metadata easier to inspect, review, and edit. See the [semantic model folder](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-dataset#tmdl-format) and the [TMDL language reference](https://learn.microsoft.com/en-us/analysis-services/tmdl/tmdl-overview). |

**Example project:** the exact folders depend on the project and its saved formats.

```text
SalesDemo/
├── SalesDemo.pbip
├── SalesDemo.Report/
│   ├── definition.pbir
│   └── definition/
│       ├── report.json
│       └── pages/
│           ├── pages.json
│           └── <page-id>/
│               ├── page.json
│               └── visuals/<visual-id>/visual.json
├── SalesDemo.SemanticModel/
│   ├── definition.pbism
│   └── definition/
│       ├── model.tmdl
│       ├── relationships.tmdl
│       └── tables/Sales.tmdl
└── .gitignore
```

In this example, PBIP organizes the project, PBIR describes how the report looks and what it references, and TMDL describes the model and its calculations. A report can instead reference a published model; it does not always contain a locally editable model. A semantic model can also use the TMSL `model.bim` representation instead of a TMDL `definition` folder. `definition.pbism` is semantic model configuration, not the model's table data. Microsoft's TMDL extension for VS Code, linked in the semantic model folder guidance above, provides a richer editing experience.

For illustration, a TMDL table definition can contain a DAX measure:

```tmdl
table Sales
    measure 'Total Sales' = SUM('Sales'[Sales Amount])
        formatString: #,##0.00
```

The indentation expresses the relationship between the table, measure, and format. The DAX expression calculates a value; PBIR can then bind a visual to that measure. This is an excerpt, not a complete model or a ready-to-run script: the table and column must exist in the chosen sample. The [TMDL view in Power BI Desktop](https://learn.microsoft.com/en-us/power-bi/transform-model/desktop-tmdl-view) is a separate scripting interface for applying changes directly to a model in either a PBIX or PBIP; save the project after applying them.

**Status and safety:** Microsoft Learn, checked November 16, 2026, documents PBIP and PBIR as generally available, while detecting and reloading external PBIP changes is in preview. Desktop TMDL view is generally available; the web TMDL view is in preview. Check the linked documentation for current status and limitations. Project files contain metadata, not necessarily all underlying data; report filters and model definitions can nevertheless contain sensitive values or connection information.

## 3.4 Select Agent Tools and an MCP Policy

[Power BI Agentic](https://learn.microsoft.com/en-us/power-bi/developer/agentic/power-bi-agentic-overview) combines **skills** that guide an agent with **tools** that let it inspect or change Power BI artifacts. These are optional; approve the agent, tools, data flows, and permitted operations before installation.

| Option | Purpose and boundary |
| --- | --- |
| **Power BI Report skill** | Plans, designs, authors, validates, and manages PBIR reports. Microsoft now describes these as capabilities of one [Power BI Report skill](https://learn.microsoft.com/en-us/power-bi/developer/agentic/power-bi-report-skill-overview), rather than requiring separate skills for each step. |
| **Power BI Authoring MCP server** | Reads and changes semantic models and can run DAX for model validation. The **local** option works with Desktop and local PBIP/TMDL files; the **hosted** option works with Fabric workspace models, not local files. Microsoft documents local as generally available and hosted as preview. Some related packages still use the name *Modeling MCP*. See [server setup and permissions](https://learn.microsoft.com/en-us/power-bi/developer/mcp/power-bi-authoring-mcp). |
| **Fabric IQ MCP** | A separate, read-only path for an agent to discover permitted published content and query data. The agent selects tools and composes queries; the server does not itself provide a natural-language answering tool. See [Fabric IQ MCP](https://learn.microsoft.com/en-us/fabric/iq/connectors/fabric-iq-mcp). |
| **Power BI Desktop Bridge** | A local bridge for checking Desktop state, reloading supported changes, and capturing report screenshots. It uses a Windows named pipe and JSON-RPC, not MCP; see the [Desktop Bridge overview](https://learn.microsoft.com/en-us/power-bi/developer/agentic/power-bi-desktop-bridge-overview). |

For a Fabric workspace model, authoring requires the documented write permissions and configuration; local Desktop and local files require the local authoring server. Choose one authoring server option for a task rather than registering overlapping local and hosted tool sets. The Desktop Bridge and external-change reload must be evaluated separately, including their preview and policy status.

**Optional approved plugin setup:** Microsoft's `powerbi-authoring` plugin includes skills and automatically registers the local MCP server. The Microsoft Learn Agentic overview gives current prerequisites and installation instructions for VS Code and Copilot CLI. For the CLI path, its documented commands are:

```powershell
copilot plugin marketplace add microsoft/skills-for-fabric
copilot plugin install powerbi-authoring@fabric-collection
```

After installation, use `/skills` in Copilot CLI to verify that the expected skills are loaded. Do not install the default plugin when MCP is prohibited unless the organization has verified an allowed configuration that excludes or disables the MCP component.

**Without MCP:** an approved agent can inspect and, if policy permits, edit scoped project files; otherwise it only proposes changes. A person reviews and applies changes in Power BI Desktop or another approved interface, runs DAX tests, and reviews reports. Distinguish proposed code, static validation, and tests actually executed. A ban on MCP does not automatically answer whether the separate Desktop Bridge, scripts, XMLA, or APIs are allowed—obtain approval for each relevant interface.

## 3.5 Prepare a Project and Plan Changes

- 🛠️ **Microsoft Learn end-to-end Power BI tutorial** — [From raw data to a shared Power BI app](https://learn.microsoft.com/en-us/power-bi/create-reports/tutorial-end-to-end-power-bi) — **Hands-on tutorial:** acquire and transform data, build a semantic model and report, then publish and distribute a Power BI app. It includes a TMDL fast path and an optional Copilot/MCP path. Follow the article's version, account, license, workspace-role, and tenant-setting prerequisites; the Power BI app is not a Fabric app.

For this workshop, start from phases 1–3 of that tutorial or a suitable prepared model from the [sample files in Chapter 1](./01_Copilot_in_Power_BI_Reports_and_DAX.md#12-sample-data-and-exercise-setup). These samples have different schemas; inspect the actual tables and adapt all examples instead of assuming they are interchangeable.

1. Define the audience, business questions, KPI and date logic, security requirements, and measurable expected results.
2. Save the working PBIX as a Power BI Project. Inspect whether the report uses PBIR and the model uses TMDL; use the relevant format guidance in section 3.3.
3. Before committing, review the project contents and `.gitignore` for sensitive information. When no `.gitignore` exists in the chosen folder or parent repository, Power BI Desktop creates one that excludes `.pbi/localSettings.json` and `.pbi/cache.abf`; these defaults do not guarantee that all sensitive information is excluded. Open the project folder in VS Code, initialize Git or use an approved repository, commit a clean baseline, and create a feature branch. See [Power BI projects Git integration](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-git).
4. Inspect the existing model before requesting edits: table granularity, relationships and filter direction, measures, date table, roles, and data sources. Identify what is missing and what must not change.
5. Request a plan and test cases; approve the scope before the agent writes files or invokes write tools.

**Example planning prompt:**

```text
Inspect the provided semantic model for a sales report.
List tables and granularity, relationships, existing measures, and date logic.
Identify what is missing for current sales and year-over-year comparison.
Propose the smallest change and three tests with expected results.
Do not edit files, change security or data sources, or run write operations.
State what you could not verify and wait for approval.
```

## 3.6 Develop and Test the Semantic Model

**Exercise 1 — measures and DAX.** Using the approved plan, create or propose measures for sales, previous-year sales, and year-over-year percentage. Use the actual model's names and date logic; request meaningful descriptions, format strings, and safe division. With an approved authoring MCP server, an agent can make and test the changes. Without it, review and apply the proposed changes in Desktop and run the queries yourself.

Check the grand total, a filtered month or region, and a year with no prior-year data against independently known values. A syntactically valid query does not prove that a KPI is correct. If the example measure from section 3.3 exists in the model, this simple [DAX query](https://learn.microsoft.com/en-us/dax/dax-queries) returns its value:

```dax
EVALUATE
ROW ( "Total Sales", [Total Sales] )
```

The query evaluates a measure; it does not create one. For creating and persisting measures with Copilot in Power BI, see [Chapter 1, section 1.4](./01_Copilot_in_Power_BI_Reports_and_DAX.md#14-develop-dax-queries-and-measures).

**Exercise 2 — controlled TMDL bulk change.** Ask the agent to list candidate technical key columns and missing descriptions without changing anything. Review exceptions: an `ID`, `Key`, or `_SK` suffix alone does not prove that a column should be hidden. After approval, make the limited changes, preserve source columns and security rules, and inspect the resulting diff. Use transactions where the selected tool supports them.

## 3.7 Design and Validate a PBIR Report

**Exercise 3 — a management overview.** First produce a design brief for the audience and business questions. Then, using only existing model fields and measures, create or modify a PBIR page with appropriate KPI cards, a time trend, a product comparison, and relevant filters. List missing model objects rather than inventing them. Agree on layout, theme, accessibility, and a maximum number of visuals before authoring.

Validate the supported PBIR files against their schemas, then render the page in Power BI Desktop. An approved Report skill and Desktop Bridge can assist with file validation, reload, and screenshots; otherwise perform those steps manually. Structural validation is not a visual or business review. Use the checks in section 3.9 before accepting the page.

**Synchronize Desktop and external edits:** follow [Edit PBIP files outside Power BI Desktop](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-external-editing). Save Desktop changes first, edit supported files, save them in VS Code, then use **Apply external changes** when the preview feature is enabled. If it is unavailable, follow the applicable guidance for reopening the project. Applying external changes can overwrite unsaved Desktop work and reset filters or UI state. Resolve pending Power Query changes before editing model expressions, and keep project file paths within the documented Windows limit. The guide lists files such as `definition.pbir`, `report.json`, `mobileState.json`, and `semanticModelDiagramLayout.json` as unsupported for external editing in this preview. Check the exact file path and current guidance: PBIR's `definition/report.json` is distinct from the PBIR-Legacy root `report.json`.

## 3.8 Query a Published Model (Optional)

**Exercise 4 — a read-only data question.** With approved MCP access, follow the Fabric IQ MCP setup linked in section 3.4, sign in with a test identity, and select a published report or semantic model the identity can access. Ask for the ten best-selling products in the last complete quarter. Have the agent show the DAX and filter logic, run the query, and compare the results with a trusted report or known test values.

The Fabric IQ MCP guide specifies region, account, client, and access prerequisites and demonstrates setup with GitHub Copilot CLI; other compatible clients require their own configuration. It respects the signed-in user's existing access. Without MCP, generate or write the query and run it manually in DAX Query View. Do not claim a query was executed unless the result is available.

The [earlier Power BI Consumption MCP endpoint](https://learn.microsoft.com/en-us/power-bi/developer/mcp/remote-mcp-server-get-started) remains documented for existing integrations, but Microsoft recommends Fabric IQ MCP for consumption. Its authentication and permission requirements differ; do not assume configuration or security behavior is identical.

## 3.9 Quality, Security, and Governance

Before approving a change, record evidence for:

- **Model and DAX:** correct grain, relationships, filter context, date logic, totals, empty results, division by zero, formatting, and performance. Compare results with known values; business owners approve KPI definitions.
- **Report:** valid structure and a rendered review of each changed page, including readability, clipped text, visual choice, number formats, contrast, alt text, filters, interactions, and relevant mobile layouts.
- **Access and data:** least-privilege permissions, separate development/test/production environments, and tests using representative identities and RLS/OLS roles. Do not infer security from an administrator's results; perspectives are not security boundaries.
- **AI and files:** assess which model metadata, filter values, query results, and project files can be sent to the agent or model provider. MCP clients can pass context outside Fabric's compliance boundary. Review project files and Git ignores for sensitive data, caches, connection details, and secrets before committing.
- **Change control:** require approval for destructive actions, role or data-source changes, and production deployment. Record limitations, preview dependencies, results actually executed, and rollback steps.

For example, the older Consumption MCP documentation states that user-authenticated queries enforce RLS but service-principal authentication does not support RLS in that endpoint. Apply the documentation and test the actual identity for the selected integration rather than generalizing this behavior to every MCP server.

## 3.10 Review and Deploy Changes

1. Review the Git diff, remove unintended changes, and create a pull request describing the business goal, affected objects, DAX test results, screenshots, limitations, and rollback.
2. Run the agreed checks and obtain technical and business approval. Deploy first to a dedicated development or test workspace.
3. Verify model connections, credentials, refresh where needed, report behavior, and representative user access. Promote to production only through the approved release process.

Local Git tracks the project files. [Fabric Git integration](https://learn.microsoft.com/en-us/fabric/cicd/git-integration/intro-to-git-integration) connects a workspace to a repository and is a separate capability; check the supported item types and preview status. Deployment pipelines, APIs, and `fabric-cicd` are alternative or complementary delivery options, not requirements for every local exercise.

- 🛠️ **Deploy a Power BI project with fabric-cicd** — [Deploy Power BI projects using fabric-cicd](https://learn.microsoft.com/en-us/power-bi/developer/projects/projects-deploy-fabric-cicd) — **Hands-on quickstart:** install the documented Python library, prepare a PBIP project, create the guide's deployment script, and deploy to a Fabric workspace. Requires a supported Python version, a PBIP project, and Contributor access; automation has additional identity and repository prerequisites. Configure data-source credentials as required and use a test workspace. Review deployment and cleanup settings before running automation.

## 3.11 Optional: Notebook Authoring and Embedded Analytics

- **Fabric notebooks in VS Code** — [Create and manage Fabric notebooks in VS Code](https://learn.microsoft.com/en-us/fabric/data-engineering/author-notebook-with-vs-code) — **Practical how-to:** use the Fabric Data Engineering extension to create, edit, synchronize, and run notebooks from VS Code.

- **Power BI Embedded** — [Embedded analytics documentation](https://learn.microsoft.com/en-us/power-bi/developer/embedded/) — **Documentation hub:** explore embedding Power BI analytics in applications; a related application-development path, not a single hands-on tutorial.

These are related paths, not prerequisites for the report exercises or the separate Fabric Apps chapter.

## 3.12 Optional: One-Day Workshop Plan

This is an optional deep-dive schedule for this chapter, not a requirement for the overall course.

| Time | Focus |
| --- | --- |
| 09:00–09:30 | Goals, agentic workflow, and human responsibilities |
| 09:30–10:15 | Windows tools and PBIP, PBIR, and TMDL |
| 10:15–10:30 | Break |
| 10:30–11:30 | Approved integration path, sample project, and Git baseline |
| 11:30–12:15 | Model inspection, DAX, and TMDL exercises |
| 12:15–13:00 | Lunch |
| 13:00–14:15 | Report planning, PBIR authoring, and Desktop review |
| 14:15–14:30 | Break |
| 14:30–15:30 | Optional published-data question and quality checks |
| 15:30–16:15 | Git review and deployment to a test workspace |
| 16:15–17:00 | Governance, pilot readiness, questions, and wrap-up |

Before the workshop, verify the approved tools and policies, sample data, repository baseline, test identities, expected results, and any required workspace access. If MCP or the Bridge is not approved, prepare the manual alternatives described above.

[Back to contents](#chapter-contents)

[Back to agenda](./00_Agenda%20with%20Tutorials.md)
