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
| ⭐ [Copilot in Power BI: End-to-End Tutorial](https://learn.microsoft.com/en-us/power-bi/create-reports/tutorial-copilot-power-bi-introduction) | [1.1 Overview and Orientation](#11-overview-and-orientation) | Follow the tutorial series from preparing a semantic model to exploring insights with Copilot. |
| ⭐ [Create a report with Copilot using sample financial data](https://learn.microsoft.com/en-us/power-bi/fundamentals/service-get-started#use-copilot-to-create-a-report-in-power-bi) | [1.5 Create and Refine Reports with Copilot](#15-create-and-refine-reports-with-copilot) | Import the Financial Sample data, create report pages with Copilot, and pin visuals to a dashboard. |

**Teaching note:** The linked resources use different datasets: Financial Sample for report creation, Revenue Opportunities for AI-ready model preparation, and an AdventureWorks scenario in the DAX learning unit. Use one primary seminar dataset and adapt prompts, table names, and measures, or clearly announce each dataset switch. The exercises should not be treated as one continuous lab with interchangeable models. The Artificial Intelligence (Contoso) sample is optional enrichment, not a Copilot report-generation exercise.

## 1.1 Overview and Orientation

- **Copilot for Power BI overview** — [Copilot for Power BI overview](https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-introduction) — **Overview/reference:** introduces Copilot experiences in Power BI.

- ⭐ **Copilot in Power BI** — [Copilot in Power BI: End-to-End Tutorial](https://learn.microsoft.com/en-us/power-bi/create-reports/tutorial-copilot-power-bi-introduction) — **Hands-on tutorial series overview:** introduces an end-to-end scenario from preparing a semantic model to exploring insights with Copilot; follow the linked tutorial pages for the practical steps.

## 1.2 Sample Data and Exercise Setup

- **Download and understand Power BI sample files** — [Download and understand Power BI sample files](https://learn.microsoft.com/en-us/power-bi/create-reports/sample-datasets#download-and-understand-power-bi-sample-files) — **Sample collection and setup guide:** download sample reports and datasets, open them in Power BI Desktop, and explore their models and visuals as starting points for exercises.

- **Exercise data downloads** — **Sample files and setup:**

  - **Financial Sample** — [Download Excel workbook (.xlsx)](https://go.microsoft.com/fwlink/?LinkID=521962) — use this sales and profit dataset for the report-creation tutorial in section 1.5.

  - **Revenue Opportunities** — [Download Power BI file (.pbix)](https://github.com/microsoft/powerbi-desktop-samples/raw/refs/heads/main/Sample%20Reports/Revenue%20Opportunities.pbix) — use the software-sales model required for the model-preparation tutorial in the Copilot tutorial series. Review the [tutorial setup and prerequisites](https://learn.microsoft.com/en-us/power-bi/create-reports/tutorial-copilot-power-bi-get-started) before starting.

  - **AdventureWorks Sales** — [Download Power BI file (.pbix)](https://github.com/microsoft/powerbi-desktop-samples/raw/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix) or [Excel workbook (.xlsx)](https://github.com/microsoft/powerbi-desktop-samples/raw/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx) — use the prepared report/model or import the source tables for DAX practice. This is an alternative AdventureWorks variant, not the exact model used in the DAX learning unit; check and adapt table names and measures.

- **Artificial Intelligence sample for Power BI** — [Artificial Intelligence sample for Power BI: Take a tour](https://learn.microsoft.com/en-us/power-bi/create-reports/sample-artificial-intelligence) — **Guided sample tour (optional):** explore the Contoso report to investigate revenue contributors, breakdowns, and anomalies. ⚠️ **This is a Power BI AI-feature sample, not a Copilot report-generation tutorial.** Follow the [sample setup and .pbix download instructions](https://learn.microsoft.com/en-us/power-bi/create-reports/sample-artificial-intelligence#get-the-sample): first add the built-in sample to **My workspace**, then download the report and data from the Power BI service.

**Copilot access:** Downloading the sample files does not provide Copilot access. The Copilot exercises require suitable capacity, permissions, and enabled settings as described in the linked setup guide.

## 1.3 Prepare the Semantic Model for Copilot

- **Ask questions about a semantic model** — [Use Copilot with semantic models](https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-semantic-models) — **Feature and workflow guide:** explains model preparation and Copilot experiences; useful context, but not one end-to-end exercise. Use questions to validate how well Copilot understands the prepared model.

## 1.4 Develop DAX Queries and Measures

- **Create DAX queries with Copilot** — [Write DAX queries with Copilot](https://learn.microsoft.com/en-us/dax/dax-copilot#sample-prompts) — **Step-by-step how-to:** enter a natural-language prompt to generate a DAX query, run it to inspect results, refine it conversationally, and keep or discard it. Includes examples such as sales or profit by product.

- **Generate and add measures to a semantic model** — [Use Copilot in Power BI to prepare and model data: Create measures from DAX queries](https://learn.microsoft.com/en-us/training/modules/power-bi-copilot/2-prepare-data-copilot#create-measures-from-dax-queries) — **Guided learning unit:** prompt Copilot to suggest measures, run the generated DAX query to evaluate them, and use **Update model with changes** to add selected measures to the model.

**Key distinction:** Keeping a DAX query does not create reusable model measures. Run and validate the query first, then use **Update model with changes** on a writable model to persist selected measures.

## 1.5 Create and Refine Reports with Copilot

⚠️ **Copilot workspace:** For this exercise, use a shared workspace in Fabric or the Power BI service rather than relying on **My workspace**. In Power BI Desktop, if prompted, select a Copilot-compatible workspace to associate with the report; it does not have to be the workspace where you publish it. Your organization must enable Copilot and provide appropriate permissions and supported capacity; a user-assigned Fabric Copilot capacity can also provide access. See [Use Copilot in Power BI Desktop](https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-power-bi-desktop) and [Fabric Copilot capacity](https://learn.microsoft.com/en-us/fabric/enterprise/fabric-copilot-capacity).

- **Write prompts for report pages** — [Write Copilot prompts for creating report pages in Power BI](https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-prompts-report-pages) — **Prompt examples and guidance:** use sample prompts and generated pages to improve report-creation requests; review and refine the generated results.

- ⭐ **Create a report with Copilot using sample financial data** — [Tutorial: Get started creating in the Power BI service](https://learn.microsoft.com/en-us/power-bi/fundamentals/service-get-started#use-copilot-to-create-a-report-in-power-bi) — **Hands-on tutorial:** import the Financial Sample Excel data, ask Copilot to create a Gross Sales report, generate a Profit Analysis by Product page, and pin visuals to a dashboard. If Copilot is unavailable, the tutorial provides a manual-reporting alternative.

- **Create reports with Copilot** — [Create and edit Power BI reports with Copilot](https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-create-reports) — **Step-by-step how-to:** create a report page with prompts, then add, change, or delete visuals. Use this as a transfer task: apply the steps to an additional page or your own report.

## 1.6 Use Copilot as a Business User (Optional)

- **Standalone Copilot in Power BI** — [Standalone Copilot in Power BI](https://learn.microsoft.com/en-us/power-bi/explore-reports/mobile/mobile-standalone-copilot) — **Feature guide:** covers the standalone Copilot experience in Power BI mobile as a consumer perspective, not a report-authoring exercise.

[Back to contents](#chapter-contents)

[Back to agenda](./00_Agenda%20with%20Tutorials.md)
