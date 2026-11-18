# 1. Copilot in Power BI: Reports and DAX

[Back to agenda](./00_Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [1.1 Overview and Orientation](#11-overview-and-orientation)
- [1.2 Sample Data and Exercise Setup](#12-sample-data-and-exercise-setup)
- [1.3 Prepare the Semantic Model for Copilot](#13-prepare-the-semantic-model-for-copilot)
- [1.4 Develop DAX Queries and Measures](#14-develop-dax-queries-and-measures)
- [1.5 Create and Refine Reports with Copilot](#15-create-and-refine-reports-with-copilot)
- [1.6 Use Copilot as a Business User (Optional)](#16-use-copilot-as-a-business-user-optional)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. ⭐ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

**Hands-on tutorials at a glance**

| Hands-on tutorial | Section | Focus |
| --- | --- | --- |
| ⭐ <a href="https://learn.microsoft.com/en-us/power-bi/create-reports/tutorial-copilot-power-bi-introduction" target="_blank" rel="noopener noreferrer">Copilot in Power BI: End-to-End Tutorial</a> | [1.1 Overview and Orientation](#11-overview-and-orientation) | Follow the tutorial series from preparing a semantic model to exploring insights with Copilot. |
| ⭐ <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/30-prepare-model-ai.html" target="_blank" rel="noopener noreferrer">Prepare a semantic model for AI</a> | [1.3 Prepare the Semantic Model for Copilot](#13-prepare-the-semantic-model-for-copilot) | Simplify the AI schema, add instructions, verified answers, and synonyms, then validate Copilot with HCAAT and approve the model (approximately 30 minutes). |
| ⭐ <a href="https://learn.microsoft.com/en-us/power-bi/fundamentals/service-get-started#use-copilot-to-create-a-report-in-power-bi" target="_blank" rel="noopener noreferrer">Create a report with Copilot using sample financial data</a> | [1.5 Create and Refine Reports with Copilot](#15-create-and-refine-reports-with-copilot) | Import the Financial Sample data, create report pages with Copilot, and pin visuals to a dashboard. |

**Teaching note:** The linked resources use different datasets: Financial Sample for report creation, Revenue Opportunities for the Copilot tutorial series, Sales Analysis for the AI-readiness lab, and an AdventureWorks scenario in the DAX learning unit. Use one primary seminar dataset and adapt prompts, table names, and measures, or clearly announce each dataset switch. The exercises should not be treated as one continuous lab with interchangeable models. The Artificial Intelligence (Contoso) sample is optional enrichment, not a Copilot report-generation exercise.

## 1.1 Overview and Orientation

- **Copilot for Power BI overview** — <a href="https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-introduction" target="_blank" rel="noopener noreferrer">Copilot for Power BI overview</a> — **Overview/reference:** introduces Copilot experiences in Power BI.

- ⭐ **Copilot in Power BI** — <a href="https://learn.microsoft.com/en-us/power-bi/create-reports/tutorial-copilot-power-bi-introduction" target="_blank" rel="noopener noreferrer">Copilot in Power BI: End-to-End Tutorial</a> — **Hands-on tutorial series overview:** introduces an end-to-end scenario from preparing a semantic model to exploring insights with Copilot; follow the linked tutorial pages for the practical steps.

## 1.2 Sample Data and Exercise Setup

- **Download and understand Power BI sample files** — <a href="https://learn.microsoft.com/en-us/power-bi/create-reports/sample-datasets#download-and-understand-power-bi-sample-files" target="_blank" rel="noopener noreferrer">Download and understand Power BI sample files</a> — **Sample collection and setup guide:** download sample reports and datasets, open them in Power BI Desktop, and explore their models and visuals as starting points for exercises.

- **Exercise data downloads** — **Sample files and setup:**

  - **Financial Sample** — [Download Excel workbook (.xlsx)](https://go.microsoft.com/fwlink/?LinkID=521962) — use this sales and profit dataset for the report-creation tutorial in section 1.5.

  - **Revenue Opportunities** — [Download Power BI file (.pbix)](https://github.com/microsoft/powerbi-desktop-samples/raw/refs/heads/main/Sample%20Reports/Revenue%20Opportunities.pbix) — use the software-sales model required for the model-preparation tutorial in the Copilot tutorial series. Review the <a href="https://learn.microsoft.com/en-us/power-bi/create-reports/tutorial-copilot-power-bi-get-started" target="_blank" rel="noopener noreferrer">tutorial setup and prerequisites</a> before starting.

  - **AdventureWorks Sales** — [Download Power BI file (.pbix)](https://github.com/microsoft/powerbi-desktop-samples/raw/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix) or [Excel workbook (.xlsx)](https://github.com/microsoft/powerbi-desktop-samples/raw/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx) — use the prepared report/model or import the source tables for DAX practice. This is an alternative AdventureWorks variant, not the exact model used in the DAX learning unit; check and adapt table names and measures.

- **Artificial Intelligence sample for Power BI** — <a href="https://learn.microsoft.com/en-us/power-bi/create-reports/sample-artificial-intelligence" target="_blank" rel="noopener noreferrer">Artificial Intelligence sample for Power BI: Take a tour</a> — **Guided sample tour (optional):** explore the Contoso report to investigate revenue contributors, breakdowns, and anomalies. ⚠️ **This is a Power BI AI-feature sample, not a Copilot report-generation tutorial.** Follow the <a href="https://learn.microsoft.com/en-us/power-bi/create-reports/sample-artificial-intelligence#get-the-sample" target="_blank" rel="noopener noreferrer">sample setup and .pbix download instructions</a>: first add the built-in sample to **My workspace**, then download the report and data from the Power BI service.

**Copilot access:** Downloading the sample files does not provide Copilot access. The Copilot exercises require suitable capacity, permissions, and enabled settings as described in the linked setup guide.

## 1.3 Prepare the Semantic Model for Copilot

- **Ask questions about a semantic model** — <a href="https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-semantic-models" target="_blank" rel="noopener noreferrer">Use Copilot with semantic models</a> — **Feature and workflow guide:** explains model preparation and Copilot experiences; useful context, but not one end-to-end exercise. Use questions to validate how well Copilot understands the prepared model.

- ⭐ **Prepare a semantic model for AI** — <a href="https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/30-prepare-model-ai.html" target="_blank" rel="noopener noreferrer">Prepare a semantic model for AI</a> — **Hands-on lab (approximately 30 minutes):** simplify the AI data schema, add AI instructions and verified answers, add synonyms through Q&A linguistic modeling, test Copilot with HCAAT diagnostics, and mark the model as Approved for Copilot. Requires Power BI Desktop (November 2025 or later) and paid Fabric capacity (F2 or higher); a Fabric trial is not supported. The **Prep data for AI** feature used in the lab is in preview. Related learning unit: <a href="https://learn.microsoft.com/en-us/training/modules/fabric-prepare-semantic-layer/" target="_blank" rel="noopener noreferrer">Prepare the semantic layer for AI in Microsoft Fabric</a>.

## 1.4 Develop DAX Queries and Measures

- **Create DAX queries with Copilot** — <a href="https://learn.microsoft.com/en-us/dax/dax-copilot#sample-prompts" target="_blank" rel="noopener noreferrer">Write DAX queries with Copilot</a> — **Step-by-step how-to:** enter a natural-language prompt to generate a DAX query, run it to inspect results, refine it conversationally, and keep or discard it. Includes examples such as sales or profit by product.

- **Generate and add measures to a semantic model** — <a href="https://learn.microsoft.com/en-us/training/modules/power-bi-copilot/2-prepare-data-copilot#create-measures-from-dax-queries" target="_blank" rel="noopener noreferrer">Use Copilot in Power BI to prepare and model data: Create measures from DAX queries</a> — **Guided learning unit:** prompt Copilot to suggest measures, run the generated DAX query to evaluate them, and use **Update model with changes** to add selected measures to the model.

**Key distinction:** Keeping a DAX query does not create reusable model measures. Run and validate the query first, then use **Update model with changes** on a writable model to persist selected measures.

## 1.5 Create and Refine Reports with Copilot

⚠️ **Copilot workspace:** For this exercise, use a shared workspace in Fabric or the Power BI service rather than relying on **My workspace**. In Power BI Desktop, if prompted, select a Copilot-compatible workspace to associate with the report; it does not have to be the workspace where you publish it. Your organization must enable Copilot and provide appropriate permissions and supported capacity; a user-assigned Fabric Copilot capacity can also provide access. See <a href="https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-power-bi-desktop" target="_blank" rel="noopener noreferrer">Use Copilot in Power BI Desktop</a> and <a href="https://learn.microsoft.com/en-us/fabric/enterprise/fabric-copilot-capacity" target="_blank" rel="noopener noreferrer">Fabric Copilot capacity</a>.

- **Write prompts for report pages** — <a href="https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-prompts-report-pages" target="_blank" rel="noopener noreferrer">Write Copilot prompts for creating report pages in Power BI</a> — **Prompt examples and guidance:** use sample prompts and generated pages to improve report-creation requests; review and refine the generated results.

- ⭐ **Create a report with Copilot using sample financial data** — <a href="https://learn.microsoft.com/en-us/power-bi/fundamentals/service-get-started#use-copilot-to-create-a-report-in-power-bi" target="_blank" rel="noopener noreferrer">Tutorial: Get started creating in the Power BI service</a> — **Hands-on tutorial:** import the Financial Sample Excel data, ask Copilot to create a Gross Sales report, generate a Profit Analysis by Product page, and pin visuals to a dashboard. If Copilot is unavailable, the tutorial provides a manual-reporting alternative.

- **Create reports with Copilot** — <a href="https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-create-reports" target="_blank" rel="noopener noreferrer">Create and edit Power BI reports with Copilot</a> — **Step-by-step how-to:** create a report page with prompts, then add, change, or delete visuals. Use this as a transfer task: apply the steps to an additional page or your own report.

## 1.6 Use Copilot as a Business User (Optional)

- **Standalone Copilot in Power BI** — <a href="https://learn.microsoft.com/en-us/power-bi/explore-reports/mobile/mobile-standalone-copilot" target="_blank" rel="noopener noreferrer">Standalone Copilot in Power BI</a> — **Feature guide:** covers the standalone Copilot experience in Power BI mobile as a consumer perspective, not a report-authoring exercise.

[Back to contents](#chapter-contents)

[Back to agenda](./00_Agenda%20with%20Tutorials.md)
