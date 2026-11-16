<sub>Version 1.2.1</sub>

<a id="proposed-agenda"></a>

# Course: Power BI & Fabric AI Advanced

**Contents**

1. [**Copilot in Power BI: Reports and DAX**](#1-copilot-in-power-bi-reports-and-dax)

   - [1.1 Overview and Orientation](#11-overview-and-orientation)
   - [1.2 Sample Data and Exercise Setup](#12-sample-data-and-exercise-setup)
   - [1.3 Prepare the Semantic Model for Copilot](#13-prepare-the-semantic-model-for-copilot)
   - [1.4 Develop DAX Queries and Measures](#14-develop-dax-queries-and-measures)
   - [1.5 Create and Refine Reports with Copilot](#15-create-and-refine-reports-with-copilot)
   - [1.6 Use Copilot as a Business User (Optional)](#16-use-copilot-as-a-business-user-optional)

2. [Copilot in Fabric: Data Transformation, Spark, and SQL](#2-copilot-in-fabric-data-transformation-spark-and-sql)

   - [2.1 Copilot in Fabric Overview](#21-copilot-in-fabric-overview)
   - [2.2 Data Preparation and Data Factory Pipelines](#22-data-preparation-and-data-factory-pipelines)
   - [2.3 Spark Analysis in Fabric Notebooks](#23-spark-analysis-in-fabric-notebooks)
   - [2.4 SQL Analysis in Fabric Data Warehouse](#24-sql-analysis-in-fabric-data-warehouse)
   - [2.5 Optional: Real-Time Intelligence](#25-optional-real-time-intelligence)

3. [Vibe Coding with Power BI and Visual Studio Code](#3-vibe-coding-with-power-bi-and-visual-studio-code)

   - [3.1 Agentic Power BI Development Workflow](#31-agentic-power-bi-development-workflow)
   - [3.2 Build Fabric Apps: From Quickstart to GitHub Copilot](#32-build-fabric-apps-from-quickstart-to-github-copilot)
   - [3.3 Optional Paths: Notebook Authoring and Embedded Analytics](#33-optional-paths-notebook-authoring-and-embedded-analytics)

4. [GenAI-based Report-Commenting](#4-genai-based-report-commenting)

5. [Fabric AI Functions and Azure OpenAI](#5-fabric-ai-functions-and-azure-openai)

   - [5.1 Fabric AI Functions: Overview and Setup](#51-fabric-ai-functions-overview-and-setup)
   - [5.2 Use and Customize AI Functions in Notebooks](#52-use-and-customize-ai-functions-in-notebooks)
   - [5.3 Use AI Functions in Fabric Data Warehouse](#53-use-ai-functions-in-fabric-data-warehouse)
   - [5.4 Integrate Azure OpenAI in Fabric Notebooks](#54-integrate-azure-openai-in-fabric-notebooks)

6. [Fabric IQ and Ontology](#6-fabric-iq-and-ontology)

7. [Fabric Data Agents](#7-fabric-data-agents)

8. [Fabric Operations Agents](#8-fabric-operations-agents)

9. [Semantic Link and Semantic Model Analysis](#9-semantic-link-and-semantic-model-analysis)

10. [Retrieval-Augmented Generation (RAG)](#10-retrieval-augmented-generation-rag)

11. [Customer Use Cases and Proofs of Concept](#11-customer-use-cases-and-proofs-of-concept)

12. [General Fabric Samples](#12-general-fabric-samples)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. 🛠️ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

## 1. Copilot in Power BI: Reports and DAX

**Teaching note:** The linked resources use different datasets: Financial Sample for report creation, Revenue Opportunities for AI-ready model preparation, and an AdventureWorks scenario in the DAX learning unit. Use one primary seminar dataset and adapt prompts, table names, and measures, or clearly announce each dataset switch. The exercises should not be treated as one continuous lab with interchangeable models. The Artificial Intelligence (Contoso) sample is optional enrichment, not a Copilot report-generation exercise.

### 1.1 Overview and Orientation

- **Copilot for Power BI overview** — [Copilot for Power BI overview](https://learn.microsoft.com/power-bi/create-reports/copilot-introduction) — **Overview/reference:** introduces Copilot experiences in Power BI.

- **Copilot in Power BI** — [Copilot in Power BI: End-to-End Tutorial](https://learn.microsoft.com/power-bi/create-reports/tutorial-copilot-power-bi-introduction) — **Overview of a hands-on tutorial series:** introduces a scenario from preparing a semantic model to exploring insights with Copilot; the practical steps are in the subsequent tutorial pages.

### 1.2 Sample Data and Exercise Setup

- **Download and understand Power BI sample files** — [Download and understand Power BI sample files](https://learn.microsoft.com/en-us/power-bi/create-reports/sample-datasets#download-and-understand-power-bi-sample-files) — **Sample collection and setup guide:** download sample reports and datasets, open them in Power BI Desktop, and explore their models and visuals as starting points for exercises.

- **Exercise data downloads** — **Sample files and setup:**

  - **Financial Sample** — [Download Excel workbook (.xlsx)](https://go.microsoft.com/fwlink/?LinkID=521962) — use this sales and profit dataset for the report-creation tutorial in section 1.5.

  - **Revenue Opportunities** — [Download Power BI file (.pbix)](https://github.com/microsoft/powerbi-desktop-samples/raw/refs/heads/main/Sample%20Reports/Revenue%20Opportunities.pbix) — use the software-sales model required for the model-preparation tutorial in section 1.3. Review the [tutorial setup and prerequisites](https://learn.microsoft.com/en-us/power-bi/create-reports/tutorial-copilot-power-bi-get-started) before starting.

  - **AdventureWorks Sales** — [Download Power BI file (.pbix)](https://github.com/microsoft/powerbi-desktop-samples/raw/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix) or [Excel workbook (.xlsx)](https://github.com/microsoft/powerbi-desktop-samples/raw/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx) — use the prepared report/model or import the source tables for DAX practice. This is an alternative AdventureWorks variant, not the exact model used in the DAX learning unit; check and adapt table names and measures.

- **Artificial Intelligence sample for Power BI** — [Artificial Intelligence sample for Power BI: Take a tour](https://learn.microsoft.com/en-us/power-bi/create-reports/sample-artificial-intelligence) — **Guided sample tour (optional):** explore the Contoso report to investigate revenue contributors, breakdowns, and anomalies. This is a Power BI AI-feature sample, not a Copilot report-generation tutorial. Follow the [sample setup and .pbix download instructions](https://learn.microsoft.com/en-us/power-bi/create-reports/sample-artificial-intelligence#get-the-sample): first add the built-in sample to **My workspace**, then download the report and data from the Power BI service.

**Copilot access:** Downloading the sample files does not provide Copilot access. The Copilot exercises require suitable capacity, permissions, and enabled settings as described in the linked setup guide.

### 1.3 Prepare the Semantic Model for Copilot

- 🛠️ **Prepare a semantic model for AI** — [Copilot in Power BI tutorial: Prepare semantic model for AI](https://learn.microsoft.com/power-bi/create-reports/tutorial-copilot-power-bi-prepare-model) — **Hands-on tutorial:** prepare a semantic model for Copilot and AI experiences.

- **AI instructions for a semantic model** — [Prepare your data for AI: AI instructions](https://learn.microsoft.com/power-bi/create-reports/copilot-prepare-data-ai-instructions) — **Feature and configuration guide:** add instructions to help AI interpret model-specific business context.

- **Ask questions about a semantic model** — [Use Copilot with semantic models](https://learn.microsoft.com/power-bi/create-reports/copilot-semantic-models) — **Feature and workflow guide:** explains model preparation and Copilot experiences; useful context, but not one end-to-end exercise. Use questions to validate how well Copilot understands the prepared model.

### 1.4 Develop DAX Queries and Measures

- **Create DAX queries with Copilot** — [Write DAX queries with Copilot](https://learn.microsoft.com/dax/dax-copilot#sample-prompts) — **Step-by-step how-to:** enter a natural-language prompt to generate a DAX query, run it to inspect results, refine it conversationally, and keep or discard it. Includes examples such as sales or profit by product.

- **Generate and add measures to a semantic model** — [Use Copilot in Power BI to prepare and model data: Create measures from DAX queries](https://learn.microsoft.com/en-us/training/modules/power-bi-copilot/2-prepare-data-copilot#create-measures-from-dax-queries) — **Guided learning unit:** prompt Copilot to suggest measures, run the generated DAX query to evaluate them, and use **Update model with changes** to add selected measures to the model.

**Key distinction:** Keeping a DAX query does not create reusable model measures. Run and validate the query first, then use **Update model with changes** on a writable model to persist selected measures.

### 1.5 Create and Refine Reports with Copilot

- **Write prompts for report pages** — [Write Copilot prompts for creating report pages in Power BI](https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-prompts-report-pages) — **Prompt examples and guidance:** use sample prompts and generated pages to improve report-creation requests; review and refine the generated results.

- 🛠️ **Create a report with Copilot using sample financial data** — [Tutorial: Get started creating in the Power BI service](https://learn.microsoft.com/en-us/power-bi/fundamentals/service-get-started#use-copilot-to-create-a-report-in-power-bi) — **Hands-on tutorial:** import the Financial Sample Excel data, ask Copilot to create a Gross Sales report, generate a Profit Analysis by Product page, and pin visuals to a dashboard. If Copilot is unavailable, the tutorial provides a manual-reporting alternative.

- **Create reports with Copilot** — [Create and edit Power BI reports with Copilot](https://learn.microsoft.com/power-bi/create-reports/copilot-create-reports) — **Step-by-step how-to:** create a report page with prompts, then add, change, or delete visuals. Use this as a transfer task: apply the steps to an additional page or your own report.

### 1.6 Use Copilot as a Business User (Optional)

- **Standalone Copilot in Power BI** — [Standalone Copilot in Power BI](https://learn.microsoft.com/power-bi/explore-reports/mobile/mobile-standalone-copilot) — **Feature guide:** covers the standalone Copilot experience in Power BI mobile as a consumer perspective, not a report-authoring exercise.

[Back to top](#proposed-agenda)

## 2. Copilot in Fabric: Data Transformation, Spark, and SQL

**Teaching note:** Begin with an overview of Copilot across Fabric, then explore data preparation, notebook-based Spark analysis, and SQL analysis in a warehouse. The three labs are separate exercises with their own datasets and setup; they are not a single end-to-end pipeline. The Data Factory pipelines guide covers a related workload, while Real-Time Intelligence is an optional extension.

### 2.1 Copilot in Fabric Overview

- **Copilot in Fabric overview** — [What is Copilot in Fabric?](https://learn.microsoft.com/fabric/fundamentals/copilot-fabric-overview) — **Overview/reference:** introduces Copilot across Fabric workloads.

### 2.2 Data Preparation and Data Factory Pipelines

- 🛠️ **Copilot in Dataflow Gen2** — [Work smarter with Copilot in Microsoft Fabric Dataflow Gen2](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22a-copilot-fabric-dataflow-gen2.html) — **Hands-on lab (approximately 30 minutes):** clean retail store data, parse XML, create categorical groups, and set data types using natural language prompts. Publish the results to a lakehouse. Requires paid Fabric capacity; trial capacity is not supported.

- **Copilot in Data Factory pipelines** — [Get started with Copilot in Fabric in the Data Factory workload](https://learn.microsoft.com/fabric/data-factory/copilot-fabric-data-factory-get-started) — **Getting-started guide:** covers Copilot in the Data Factory workload, including pipelines; distinct from the Dataflow Gen2 lab.

### 2.3 Spark Analysis in Fabric Notebooks

- **Copilot in Data Engineering and Data Science** — [Overview of Copilot for Data Engineering and Data Science](https://learn.microsoft.com/fabric/data-engineering/copilot-notebooks-overview) · [Use the Copilot chat pane in notebooks](https://learn.microsoft.com/fabric/data-engineering/copilot-notebooks-chat-pane) — **Overview and feature guide:** introduce notebook Copilot and its chat pane.

- 🛠️ **Copilot in Fabric notebooks** — [Analyze data with Apache Spark and Copilot in Microsoft Fabric notebooks](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22b-copilot-fabric-notebooks.html) — **Hands-on lab (approximately 30 minutes):** generate Spark code to clean, filter, and reshape population data, save it to a lakehouse, and visualize the results. Requires paid Fabric capacity; trial capacity is not supported.

### 2.4 SQL Analysis in Fabric Data Warehouse

- **Data Warehouse Copilot chat pane** — [How to use the Copilot chat pane in Fabric Data Warehouse](https://learn.microsoft.com/fabric/data-warehouse/copilot-chat-pane) — **Feature guide:** use the warehouse Copilot chat experience.

- 🛠️ **Copilot in Fabric Data Warehouse** — [Use Copilot in Microsoft Fabric data warehouse](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22c-copilot-fabric-data-warehouse.html) — **Hands-on lab (approximately 30 minutes):** use retail sales data to generate and refine SQL queries, fix syntax errors, and create reusable views with Copilot. Requires paid Fabric capacity; trial capacity is not supported.

### 2.5 Optional: Real-Time Intelligence

- **Copilot in Real-Time Intelligence** — [Copilot for Real-Time Intelligence](https://learn.microsoft.com/fabric/real-time-intelligence/copilot-real-time-intelligence) · [Generate Real-Time dashboards with Copilot](https://learn.microsoft.com/fabric/real-time-intelligence/copilot-generate-dashboard) — **Overview and how-to:** use Copilot for Real-Time Intelligence, including KQL scenarios and dashboard generation.

[Back to top](#proposed-agenda)

## 3. Vibe Coding with Power BI and Visual Studio Code

**Teaching note:** Start with the agentic Power BI workflow to establish development concepts, validation, and deployment practices. Then follow the separate Fabric app track: scaffold a first app before building a Copilot-assisted app connected to a semantic model. The app exercises build applications, not PBIR reports. Notebook authoring and Power BI Embedded are optional related paths, not prerequisites for the app exercises.

### 3.1 Agentic Power BI Development Workflow

- **Agentic Power BI development on Windows** — [Vibe Coding with Power BI on Windows](./06-vibe-coding-power-bi-windows.en.md) — **Training material:** covers VS Code, PBIP, TMDL, PBIR, agentic workflows, validation, and deployment, including alternatives when MCP is prohibited.

### 3.2 Build Fabric Apps: From Quickstart to GitHub Copilot

- **Rayfin** — [Rayfin](https://rayfin.ai/) — **External product website:** related reference for the Rayfin-based Fabric apps workflow below; not a guided exercise. The website could not be retrieved during this review.

- **Rayfin guidance and ready-to-run examples** — [awesome-rayfin (FindusHH)](https://github.com/FindusHH/awesome-rayfin) — **Curated examples and reference collection:** covers Rayfin in depth and is based on [Microsoft's awesome-rayfin repository](https://github.com/microsoft/awesome-rayfin). It contains only a subset of the upstream collection, but the included examples have been updated to be ready to run. Follow each example's documented setup instructions and prerequisites.

- 🛠️ **Create your first Fabric app** — [Create your first Fabric apps project](https://learn.microsoft.com/en-us/fabric/apps/create-app) — **Hands-on quickstart (preview):** scaffold an app with the Rayfin tooling, deploy its backend to Fabric, and run the frontend locally. Requires Node.js 20 or later, suitable workspace permissions, and the Fabric apps tenant setting.

- 🛠️ **Create a semantic model app with GitHub Copilot** — [Create a semantic model app with GitHub Copilot](https://learn.microsoft.com/en-us/fabric/apps/create-app-with-github-copilot) — **Hands-on tutorial:** use GitHub Copilot agent mode in VS Code to scaffold an analytical app, connect a Fabric semantic model, generate DAX and visualizations, validate changes, and deploy to Fabric. This builds an app connected to a semantic model rather than a PBIR report.

### 3.3 Optional Paths: Notebook Authoring and Embedded Analytics

- **Fabric notebooks in VS Code** — [Create and manage Fabric notebooks in VS Code](https://learn.microsoft.com/en-us/fabric/data-engineering/author-notebook-with-vs-code) — **Practical how-to:** use the Fabric Data Engineering extension to create, edit, synchronize, and run notebooks from VS Code.

- **Power BI Embedded** — [Embedded analytics documentation](https://learn.microsoft.com/en-us/power-bi/developer/embedded/) — **Documentation hub:** explore embedding Power BI analytics in applications; a related application-development path, not a single hands-on tutorial.

[Back to top](#proposed-agenda)

## 4. GenAI-based Report-Commenting

This topic covers AI-generated Power BI narratives and Azure Content Understanding for extracting and validating information from source content. The Content Understanding exercises do not themselves build a Power BI report-commenting solution; integrating their output into reports is a separate task.

### Analyzing Power BI Reports with Content Understanding

Content Understanding does not natively analyze PBIX files or connect to interactive Power BI reports and their semantic models. It can analyze supported exports, such as PDFs or screenshots, to extract and interpret visible text, tables, and chart content. These exports represent a specific report state: DAX logic, model relationships, non-visible data, and interactive filtering are not available. Verify extracted numbers and chart interpretations; confidence scores do not establish that a business interpretation is correct. See [Supported input file types and limits](https://learn.microsoft.com/azure/ai-services/content-understanding/service-limits#input-file-limits).

For this workshop, distinguish three use cases:

- **Generate commentary inside Power BI:** use Copilot narratives, covered in the practical guide below.

- **Analyze exported reports or supporting source documents:** use Content Understanding, then integrate the extracted results into Power BI separately.

- **Inspect semantic models programmatically:** use Semantic Link/SemPy, covered under Semantic Link and Semantic Model Analysis.

### Background and Quality Considerations

Content Understanding uses multiple AI models to analyze and cross-validate content. Confidence scores and grounding help assess extracted values and trace them to source documents; they do not guarantee correctness. The exercises below cover custom schemas, labeled examples, document classification, and scenario-specific prebuilt analyzers.

Potential industry scenarios include tax preparation, procurement documents, contract analysis, call center analytics, and media analysis. Check the available prebuilt analyzers for the selected scenario and region.

### Practical Tutorials and How-to Guides

- **AI-generated report commentary in Power BI** — [Create a narrative visual with Copilot for Power BI](https://learn.microsoft.com/power-bi/create-reports/copilot-create-narrative) — **Step-by-step how-to:** generate a narrative for a report, page, or selected visuals and refine it with prompts. Requires enabled Copilot and supported paid Fabric capacity.

- **Smart narrative summaries** — [Create smart narrative summaries](https://learn.microsoft.com/power-bi/visuals/power-bi-visualization-smart-narrative) — **Feature guide:** create and customize smart narrative summaries in Power BI; this is a related option distinct from the Copilot narrative guide.

- 🛠️ **Try industry-specific prebuilt analyzers** — [Quickstart: Try Content Understanding Studio or Microsoft Foundry](https://learn.microsoft.com/azure/ai-services/content-understanding/quickstart/content-understanding-studio) — **Hands-on Studio quickstart:** select a prebuilt analyzer for your scenario, analyze sample or uploaded content, and review extracted fields. Use Studio to explore the available domain-specific analyzers.

- **Create and improve a custom analyzer in Studio** — [Create and improve your custom analyzer in Content Understanding Studio](https://learn.microsoft.com/azure/ai-services/content-understanding/how-to/customize-analyzer-content-understanding-studio) — **Step-by-step UI guide:** upload sample content, select a template, refine suggested fields, test the schema, and build an analyzer. Optionally use labeled document examples to improve extraction quality.

- **Inspect confidence and grounding; improve extraction with labeled samples** — [Validate document analyzer quality with confidence, grounding, and labeled samples](https://learn.microsoft.com/azure/ai-services/content-understanding/document/analyzer-improvement) — **Mixed concept and practical guide:** understand confidence scores and source references, then follow the Studio labeling workflow to correct sample values and rebuild the analyzer. Training is limited to document analyzers and does not currently support generated fields.

- **Classify content types and route documents** — [Classify and route your data using Content Understanding](https://learn.microsoft.com/azure/ai-services/content-understanding/how-to/classification-content-understanding-studio) — **Step-by-step Studio and API guide:** create custom document categories, test classification, and route each category to an analyzer for field extraction.

- 🛠️ **Create a custom analyzer with confidence and source information** — [Create a custom analyzer](https://learn.microsoft.com/azure/ai-services/content-understanding/tutorial/create-custom-analyzer) — **Hands-on API/SDK tutorial:** define an extraction schema, enable field-source and confidence estimation, create the analyzer, submit a document, and inspect the structured results. Suitable for practicing programmatic integration.

**Content Understanding prerequisites:** an Azure subscription, a Microsoft Foundry resource in a supported region, and the required model deployments/configuration. Follow each guide's setup instructions; Azure resource and model usage can incur costs.

### Related Foundry Tools in Fabric

The following links cover related Azure AI services and Fabric workflows; they are not Content Understanding tutorials or a complete report-commenting solution.

- **Prebuilt Foundry Tools in Fabric** — [Use prebuilt Azure AI services (Foundry Tools) in Fabric](https://learn.microsoft.com/fabric/data-science/ai-services/ai-services-overview) — **Overview/reference:** introduces available AI services for Fabric scenarios and proofs of concept.

- **Foundry Tools with SynapseML** — [Use Foundry Tools with SynapseML in Microsoft Fabric](https://learn.microsoft.com/fabric/data-science/how-to-use-ai-services-with-synapseml) — **Practical code guide:** use Azure AI services with SynapseML in Fabric.

- **Classify natural-language text** — [Classify natural language text with generative AI in Microsoft Fabric](https://learn.microsoft.com/fabric/data-science/tutorial-text-classification) — **Conceptual guide with practical code examples:** describes a Fabric text-classification architecture, prompts, and PySpark snippets. Adapting placeholders, data, and pipeline configuration is required; this is distinct from Content Understanding document classification.

- **Azure AI Language text analytics** — [Use Azure AI Language text analytics in Fabric with SynapseML](https://learn.microsoft.com/fabric/data-science/ai-services/how-to-use-text-analytics) — **Practical code guide:** apply text analytics in Fabric; relevant to text and transcript analysis.

- **Content Safety and Responsible AI** — [What is Azure AI Content Safety?](https://learn.microsoft.com/azure/ai-services/content-safety/overview) — **Overview/reference:** introduces Azure AI Content Safety. This is a conceptual Azure reference, not a Fabric-native hands-on exercise.

[Back to top](#proposed-agenda)

## 5. Fabric AI Functions and Azure OpenAI

**Teaching note:** Start with the shared AI Functions concepts and prerequisites. Then explore notebook-based use and configuration, followed by the separate SQL experience in Fabric Data Warehouse. Finish with direct Azure OpenAI integrations in notebooks. Distinguish Fabric AI Functions, which provide managed functions for data transformation, from calling Azure OpenAI through SynapseML or the OpenAI Python SDK; these approaches have different setup, configuration, and endpoint requirements.

### 5.1 Fabric AI Functions: Overview and Setup

- **Fabric AI Functions** — [AI Functions: Transform data at scale with AI](https://learn.microsoft.com/en-us/fabric/data-science/ai-functions/overview?tabs=pandas) — **Practical code guide:** setup instructions and examples for using AI functions across Fabric, with the pandas tab selected. Requires an enabled Fabric tenant setting and paid Fabric capacity.

### 5.2 Use and Customize AI Functions in Notebooks

- **AI Functions with Python and PySpark** — [Apply AI Functions in pandas and PySpark](https://learn.microsoft.com/fabric/data-science/ai-functions/overview#apply-ai-functions) — **Practical code examples:** jumps to pandas and PySpark examples in the AI Functions guide; follow along in a Fabric notebook.

- **Customize AI Functions with PySpark** — [Customize AI Functions with PySpark](https://learn.microsoft.com/en-us/fabric/data-science/ai-functions/pyspark/configuration?tabs=llm-global-pyspark%2Cembedding-global-pyspark%2Cfoundry-openai-pyspark) — **Practical configuration guide:** customize model and embedding settings, concurrency, chaining, statistics, and endpoint configuration for PySpark AI Functions.

### 5.3 Use AI Functions in Fabric Data Warehouse

- **AI Functions in Fabric Data Warehouse** — [AI Functions in a warehouse or SQL analytics endpoint](https://learn.microsoft.com/fabric/data-warehouse/ai-functions) — **Practical SQL guide:** demonstrates text analysis and transformation with T-SQL examples. The feature is in preview and requires supported Fabric capacity and tenant settings.

- 🛠️ **Use AI Functions in a Fabric Warehouse** — [Tutorial: Use AI functions in a warehouse](https://learn.microsoft.com/fabric/data-warehouse/tutorial-ai-functions) — **Hands-on tutorial:** run guided T-SQL exercises to extract, generate, summarize, and persist AI results using sample sales data. First complete the setup steps to [create a workspace](https://learn.microsoft.com/fabric/data-warehouse/tutorial-create-workspace), [create a warehouse](https://learn.microsoft.com/fabric/data-warehouse/tutorial-create-warehouse), and [ingest sample data](https://learn.microsoft.com/fabric/data-warehouse/tutorial-ingest-data). Requires a paid Fabric capacity and enabled tenant settings; run the data-changing steps in a test warehouse.

### 5.4 Integrate Azure OpenAI in Fabric Notebooks

- **Azure OpenAI with SynapseML** — [Use Azure OpenAI in Fabric with SynapseML](https://learn.microsoft.com/fabric/data-science/ai-services/how-to-use-openai-synapse-ml) — **Practical code guide:** run PySpark examples for prompts, responses, and embeddings in a Fabric notebook.

- 🛠️ **Use Azure OpenAI for big data with SynapseML** — [Azure OpenAI for big data](https://learn.microsoft.com/fabric/data-science/open-ai) — **Hands-on notebook tutorial:** download and import the provided notebook into Fabric, configure a working Azure OpenAI resource, install SynapseML, then run and adapt Spark examples for prompts and embeddings. Requires an Azure OpenAI resource and a compatible Fabric Spark runtime.

- **Azure OpenAI with the OpenAI Python SDK** — [Use Azure OpenAI in Fabric with the OpenAI Python SDK](https://learn.microsoft.com/fabric/data-science/ai-services/how-to-use-openai-python-sdk) — **Practical code guide:** set up a client and run API examples in a Fabric notebook.

[Back to top](#proposed-agenda)

## 6. Fabric IQ and Ontology

- **Fabric IQ** — [What is Fabric IQ?](https://learn.microsoft.com/fabric/iq/overview) — **Overview/reference:** introduces Fabric IQ and its components; it is not a build tutorial.

- 🛠️ **Create a Fabric ontology** — [Ontology tutorial: Introduction and environment setup](https://learn.microsoft.com/fabric/iq/ontology/tutorial-0-introduction) — **Hands-on tutorial series (preview):** prepare sample data, create an ontology with entity types and relationships, bind data, and explore it. Requires Fabric capacity and enabled tenant settings.

- 🛠️ **Build a healthcare ontology manually** — [Create an ontology with Fabric IQ](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/23-build-ontology-manually.html) — **Hands-on lab (preview, approximately 40 minutes):** create entity types, properties, keys, and relationships, then bind hospital reference data from a lakehouse and sample time-series readings from an eventhouse. Uses the new ontology experience; paid or trial Fabric capacity and enabled ontology tenant settings are required.

- 🛠️ **Generate an ontology from a semantic model** — [Build an ontology from a semantic model in Fabric IQ](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/24-build-ontology-semantic-model.html) — **Hands-on lab (preview, approximately 45 minutes):** build a healthcare semantic model, generate ontology entities and relationships, and add eventhouse time-series bindings. Uses the new ontology experience; requires paid or trial Fabric capacity, enabled tenant settings, and Read and Build permissions on the semantic model.

- 🛠️ **Visualize healthcare ontology data** — [Visualize ontology data with Microsoft Fabric IQ](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/27-visualize-ontology.html) — **Hands-on lab (preview, approximately 30 minutes):** use a setup notebook to create the sample ontology, then explore entity instances, relationship graphs, property charts, time-series data, and the Query builder. Requires paid or trial Fabric capacity and enabled ontology tenant settings. Uses the older ontology experience rather than the new experience used in labs 23 and 24.

[Back to top](#proposed-agenda)

## 7. Fabric Data Agents

- **Data Agent concepts and fundamentals** — [What is a Fabric data agent?](https://learn.microsoft.com/fabric/data-science/concept-data-agent) — **Overview/reference:** introduces Fabric Data Agent concepts and capabilities.

- **Fabric Data Agents** — [Create a Fabric data agent](https://learn.microsoft.com/fabric/data-science/how-to-create-data-agent) — **Step-by-step how-to:** create an agent, add data sources, select tables, and configure it. Requires paid Fabric capacity and accessible data.

- 🛠️ **Fabric Data Agent with AdventureWorks** — [Data agent example with the AdventureWorks dataset](https://learn.microsoft.com/fabric/data-science/data-agent-end-to-end-tutorial) — **Hands-on tutorial (preview):** populate a lakehouse with sample data, create an agent, and ask questions. Requires paid Fabric capacity and appropriate tenant settings.

- 🛠️ **Chat with sales data using a Fabric Data Agent** — [Chat with your data using Microsoft Fabric data agents](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22d-copilot-fabric-data-agents.html) — **Hands-on lab (approximately 30 minutes):** create a sales warehouse and configure a data agent, then ask plain English questions and inspect how they are translated into SQL queries. Requires paid Fabric capacity; trial capacity is not supported.

- **Connect a Data Agent to an ontology** — [Create a data agent grounded in an ontology](https://learn.microsoft.com/fabric/iq/ontology/how-to-create-data-agent) — **Step-by-step how-to (preview):** add an ontology as a data source and ask questions in natural language. Currently, ontologies bound to semantic models are not supported by this integration.

- 🛠️ **Build a healthcare Data Agent with an ontology** — [Build a Fabric data agent with an ontology](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/28-build-data-agent-ontology.html) — **Hands-on lab (preview, approximately 30 minutes):** create the Lamna Healthcare ontology with a setup notebook, configure agent instructions, test natural language questions, and publish and share the agent. Requires paid Fabric capacity and appropriate tenant settings; trial capacity is not supported. Uses the older ontology experience, scheduled to retire on January 31, 2027; it is not a direct continuation of lab 24.

- **Use a Data Agent in Copilot Studio** — [Consume a Fabric data agent in Microsoft Copilot Studio](https://learn.microsoft.com/fabric/data-science/data-agent-microsoft-copilot-studio) — **Integration guide:** consume a Fabric Data Agent from Copilot Studio.

- **Add a Data Agent as a Copilot Studio tool** — [Add a Fabric data agent as a tool in Microsoft Copilot Studio](https://learn.microsoft.com/fabric/data-science/data-agent-microsoft-copilot-studio-tool) — **Integration guide:** configure a Fabric Data Agent as a tool in Copilot Studio.

- **Use a Data Agent with Microsoft Foundry** — [Consume Fabric data agent from Microsoft Foundry Services](https://learn.microsoft.com/fabric/data-science/data-agent-foundry) · [Fabric data agent as a tool in the Foundry Agent Service](https://learn.microsoft.com/azure/foundry/agents/how-to/tools/fabric) — **Integration guides:** use Fabric Data Agents from Foundry and as an agent tool.

- **Connect AI agents to Fabric through MCP** — [Connect AI Agents to Fabric API for GraphQL with a local MCP server](https://learn.microsoft.com/fabric/data-engineering/api-graphql-local-model-context-protocol) — **Integration guide:** connect an AI agent to a Fabric GraphQL API using a local MCP server; this is separate from the Fabric Data Agent integrations above.

[Back to top](#proposed-agenda)

## 8. Fabric Operations Agents

- **Create a Fabric Operations Agent** — [Create and configure operations agents](https://learn.microsoft.com/fabric/real-time-intelligence/operations-agent) — **Step-by-step how-to:** configure an agent to monitor data, generate a playbook, and recommend actions. Requires non-trial Fabric capacity, a data source, Microsoft Teams, and enabled tenant settings.

- **Connect an Operations Agent to an ontology** — [Create an operations agent grounded in an ontology](https://learn.microsoft.com/fabric/iq/ontology/how-to-create-operations-agent) — **Step-by-step how-to (preview):** use an ontology as the agent's knowledge source, configure monitoring, and receive recommendations in Teams. Currently, ontologies bound to semantic models are not supported by this integration.

[Back to top](#proposed-agenda)

## 9. Semantic Link and Semantic Model Analysis

- **Semantic link** — [What is semantic link?](https://learn.microsoft.com/en-us/fabric/data-science/semantic-link-overview) — **Overview/reference:** explains how semantic link connects Power BI semantic models with Fabric data science and notebooks.

- **Semantic Link Labs code examples** — [Code Examples](https://github.com/microsoft/semantic-link-labs/wiki/Code-Examples) — **Practical code examples:** use Python notebook snippets for tasks such as model best-practice analysis and memory analysis.

- **Semantic link sample notebooks** — [Semantic link samples](https://github.com/microsoft/fabric-samples/tree/main/docs-samples/data-science/semantic-link-samples) — **Sample notebook collection:** download the notebooks accompanying the semantic link tutorials below; the repository itself is not a step-by-step guide.

- **Use notebooks with a semantic model** — [Use notebooks with a semantic model](https://learn.microsoft.com/power-bi/transform-model/service-notebooks) — **Practical guide:** open ready-made notebooks from a semantic model to run best-practice and memory analysis. Requires suitable workspace access, model permissions, and Fabric capacity.

- 🛠️ **Analyze functional dependencies** — [Analyze functional dependencies in a semantic model](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-dependencies) — **Hands-on notebook tutorial:** use SemPy and a sample model to test dependencies between columns and identify data-quality issues.

- 🛠️ **Extract and calculate Power BI measures** — [Calculate Power BI measures from a Jupyter notebook](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-measures) — **Hands-on notebook tutorial:** list and evaluate measures from a sample semantic model using SemPy.

- 🛠️ **Discover semantic model relationships** — [Discover relationships in a semantic model using semantic link](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-relationships) — **Hands-on notebook tutorial:** discover relationships between tables and check for relationship violations using SemPy.

- 🛠️ **Discover relationships in the Synthea dataset** — [Discover relationships in the Synthea dataset](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-relationships-detection) — **Hands-on notebook tutorial:** detect and visualize relationships in sample data, from a small example to a larger set of tables.

- 🛠️ **Validate data with SemPy and Great Expectations** — [Validate data using SemPy and Great Expectations](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-great-expectations) — **Hands-on notebook tutorial:** configure expectations and validate data from a Power BI semantic model. The tutorial uses Great Expectations versions earlier than 1.0.

[Back to top](#proposed-agenda)

## 10. Retrieval-Augmented Generation (RAG)

- 🛠️ **Build RAG in Fabric** — [Build retrieval-augmented generation in Microsoft Fabric](https://learn.microsoft.com/fabric/data-science/quickstart-building-retrieval-augmented-generation) — **Hands-on notebook quickstart:** prepare data, create embeddings and a vector index, then generate answers. Requires Fabric capacity, a lakehouse, and an Azure AI Search resource.

- **Azure OpenAI for embeddings and ingestion** — [Azure OpenAI for big data in Fabric](https://learn.microsoft.com/fabric/data-science/open-ai) — **Practical reference:** Azure OpenAI in Fabric for big-data workflows, including the embeddings/ingestion context for RAG.

- **SQL database in Fabric for AI applications** — [Use SQL database in AI applications](https://learn.microsoft.com/fabric/database/sql/use-case-ai-application) · [Vector search in the SQL Database Engine](https://learn.microsoft.com/sql/sql-server/ai/vectors) — **Use-case and technical references:** explore SQL database AI scenarios and vector search for RAG. The second link covers the SQL Database Engine generally.

- **Cosmos DB in Fabric for vector and hybrid search** — [Vector search sample](https://learn.microsoft.com/samples/azurecosmosdb/cosmos-fabric-samples/vector-search/) · [Index vector data](https://learn.microsoft.com/fabric/database/cosmos-db/index-vector-data) · [Hybrid search](https://learn.microsoft.com/fabric/database/cosmos-db/hybrid-search) · [Sample data sets](https://learn.microsoft.com/fabric/database/cosmos-db/sample-data) — **Sample and practical guides:** explore vector indexing, vector and hybrid search, and sample data in Cosmos DB in Fabric.

[Back to top](#proposed-agenda)

## 11. Customer Use Cases and Proofs of Concept

These are example scenarios rather than complete solutions. The linked guides provide relevant building blocks; integration, validation, and business-specific rules remain separate work.

- **Customer use cases and PoCs** — [Use prebuilt Azure AI services (Foundry Tools) in Fabric](https://learn.microsoft.com/fabric/data-science/ai-services/ai-services-overview) — **Overview/reference:** identify services that can support a proof of concept.

- **Tax automation** — [Use ai.extract with PySpark in Fabric](https://learn.microsoft.com/fabric/data-science/ai-functions/pyspark/extract) — **Practical code guide:** use extraction as a building block for tax-document processing.

- **Mortgage application processing** — [Load forms and extract fields with Document Intelligence in Fabric](https://learn.microsoft.com/fabric/data-science/create-a-multilingual-search-engine-from-forms) — **Related tutorial:** form extraction can support an application-processing PoC; the tutorial is not a complete mortgage solution.

- **Invoice and contract verification** — [Extract data from forms with Document Intelligence in Fabric](https://learn.microsoft.com/fabric/data-science/create-a-multilingual-search-engine-from-forms) — **Related tutorial:** form extraction is a starting point; invoice/contract matching and verification require additional work.

- **Post-call analytics** — [Use Azure AI Language text analytics in Fabric with SynapseML](https://learn.microsoft.com/fabric/data-science/ai-services/how-to-use-text-analytics) — **Practical code guide:** text analytics can be applied to call transcripts after they have been obtained.

- **Media asset management** — [Use multimodal input with AI Functions in Fabric](https://learn.microsoft.com/fabric/data-science/ai-functions/multimodal-overview) — **Practical reference:** multimodal input, including image analysis, as a building block for media workflows.

- **Enhanced customer support** — [End-to-end tutorial: Create a Fabric data agent](https://learn.microsoft.com/fabric/data-science/data-agent-end-to-end-tutorial) — **Related tutorial:** demonstrates a Data Agent; adapting it for customer support requires scenario-specific data and design.

[Back to top](#proposed-agenda)

## 12. General Fabric Samples

- **Microsoft Fabric Samples** — [Fabric samples repository](https://github.com/microsoft/fabric-samples/tree/main) — **Sample collection:** browse documentation, feature, and community examples, including code and sample data.

[Back to top](#proposed-agenda)
