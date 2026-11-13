# Proposed Agenda

**Course:** Power BI & Fabric AI Advanced

**Contents**

1. [Copilot in Power BI: Reports and DAX](#1-copilot-in-power-bi-reports-and-dax)
2. [Vibe Coding with Power BI and Visual Studio Code](#2-vibe-coding-with-power-bi-and-visual-studio-code)
3. [GenAI-based Report-Commenting](#3-genai-based-report-commenting)
4. [Copilot in Fabric: Data Transformation, Spark, and SQL](#4-copilot-in-fabric-data-transformation-spark-and-sql)
5. [Fabric AI Functions and Azure OpenAI](#5-fabric-ai-functions-and-azure-openai)
6. [Fabric IQ and Ontology](#6-fabric-iq-and-ontology)
7. [Fabric Data Agents](#7-fabric-data-agents)
8. [Fabric Operations Agents](#8-fabric-operations-agents)
9. [Semantic Link and Semantic Model Analysis](#9-semantic-link-and-semantic-model-analysis)
10. [Retrieval-Augmented Generation (RAG)](#10-retrieval-augmented-generation-rag)
11. [Customer Use Cases and Proofs of Concept](#11-customer-use-cases-and-proofs-of-concept)
12. [General Fabric Samples](#12-general-fabric-samples)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

## 1. Copilot in Power BI: Reports and DAX

- **Copilot for Power BI overview** — [Copilot for Power BI overview](https://learn.microsoft.com/power-bi/create-reports/copilot-introduction) — **Overview/reference:** introduces Copilot experiences in Power BI.
- **Download and understand Power BI sample files** — [Download and understand Power BI sample files](https://learn.microsoft.com/en-us/power-bi/create-reports/sample-datasets#download-and-understand-power-bi-sample-files) — **Sample collection and setup guide:** download sample reports and datasets, open them in Power BI Desktop, and explore their models and visuals as starting points for exercises.
- **Artificial Intelligence sample for Power BI** — [Artificial Intelligence sample for Power BI: Take a tour](https://learn.microsoft.com/en-us/power-bi/create-reports/sample-artificial-intelligence) — **Guided sample tour:** explore the Contoso report to investigate revenue contributors, breakdowns, and anomalies. This is a Power BI AI-feature sample, not a Copilot report-generation tutorial.
- **Standalone Copilot in Power BI** — [Standalone Copilot in Power BI](https://learn.microsoft.com/power-bi/explore-reports/mobile/mobile-standalone-copilot) — **Feature guide:** covers the standalone Copilot experience in Power BI mobile.
- **Ask questions about a semantic model** — [Use Copilot with semantic models](https://learn.microsoft.com/power-bi/create-reports/copilot-semantic-models) — **Feature and workflow guide:** explains model preparation and Copilot experiences; useful context, but not one end-to-end exercise.
- **Copilot in Power BI** — [Copilot in Power BI: End-to-End Tutorial](https://learn.microsoft.com/power-bi/create-reports/tutorial-copilot-power-bi-introduction) — **Hands-on end-to-end tutorial:** follows a scenario from preparing a semantic model to exploring insights with Copilot.
- **Prepare a semantic model for AI** — [Copilot in Power BI tutorial: Prepare semantic model for AI](https://learn.microsoft.com/power-bi/create-reports/tutorial-copilot-power-bi-prepare-model) — **Hands-on tutorial:** prepare a semantic model for Copilot and AI experiences.
- **AI instructions for a semantic model** — [Prepare your data for AI: AI instructions](https://learn.microsoft.com/power-bi/create-reports/copilot-prepare-data-ai-instructions) — **Feature and configuration guide:** add instructions to help AI interpret model-specific business context.
- **Create reports with Copilot** — [Create and edit Power BI reports with Copilot](https://learn.microsoft.com/power-bi/create-reports/copilot-create-reports) — **Step-by-step how-to:** create a report page with prompts, then add, change, or delete visuals.
- **Write prompts for report pages** — [Write Copilot prompts for creating report pages in Power BI](https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-prompts-report-pages) — **Prompt examples and guidance:** use sample prompts and generated pages to improve report-creation requests; review and refine the generated results.
- **Create DAX queries with Copilot** — [Write DAX queries with Copilot](https://learn.microsoft.com/dax/dax-copilot) — **Step-by-step how-to:** enable Copilot in DAX query view, generate a query, run it, and keep or discard it.

[Back to top](#proposed-agenda)

## 2. Vibe Coding with Power BI and Visual Studio Code

- **Agentic Power BI development on Windows** — [Vibe Coding with Power BI on Windows](./06-vibe-coding-power-bi-windows.en.md) — **Training material:** covers VS Code, PBIP, TMDL, PBIR, agentic workflows, validation, and deployment, including alternatives when MCP is prohibited.
- **Rayfin** — [Rayfin](https://rayfin.ai/) — **External product website:** related reference for the Rayfin-based Fabric apps workflow below; not a guided exercise. The website could not be retrieved during this review.
- **Create your first Fabric app** — [Create your first Fabric apps project](https://learn.microsoft.com/en-us/fabric/apps/create-app) — **Hands-on quickstart (preview):** scaffold an app with the Rayfin tooling, deploy its backend to Fabric, and run the frontend locally. Requires Node.js 20 or later, suitable workspace permissions, and the Fabric apps tenant setting.
- **Create a semantic model app with GitHub Copilot** — [Create a semantic model app with GitHub Copilot](https://learn.microsoft.com/en-us/fabric/apps/create-app-with-github-copilot) — **Hands-on tutorial:** use GitHub Copilot agent mode in VS Code to scaffold an analytical app, connect a Fabric semantic model, generate DAX and visualizations, validate changes, and deploy to Fabric. This builds an app connected to a semantic model rather than a PBIR report.
- **Power BI Embedded** — [Embedded analytics documentation](https://learn.microsoft.com/en-us/power-bi/developer/embedded/) — **Documentation hub:** explore embedding Power BI analytics in applications; a related application-development path, not a single hands-on tutorial.
- **Fabric notebooks in VS Code** — [Create and manage Fabric notebooks in VS Code](https://learn.microsoft.com/en-us/fabric/data-engineering/author-notebook-with-vs-code) — **Practical how-to:** use the Fabric Data Engineering extension to create, edit, synchronize, and run notebooks from VS Code.

[Back to top](#proposed-agenda)

## 3. GenAI-based Report-Commenting

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
- **Try industry-specific prebuilt analyzers** — [Quickstart: Try Content Understanding Studio or Microsoft Foundry](https://learn.microsoft.com/azure/ai-services/content-understanding/quickstart/content-understanding-studio) — **Hands-on Studio quickstart:** select a prebuilt analyzer for your scenario, analyze sample or uploaded content, and review extracted fields. Use Studio to explore the available domain-specific analyzers.
- **Create and improve a custom analyzer in Studio** — [Create and improve your custom analyzer in Content Understanding Studio](https://learn.microsoft.com/azure/ai-services/content-understanding/how-to/customize-analyzer-content-understanding-studio) — **Step-by-step UI guide:** upload sample content, select a template, refine suggested fields, test the schema, and build an analyzer. Optionally use labeled document examples to improve extraction quality.
- **Inspect confidence and grounding; improve extraction with labeled samples** — [Validate document analyzer quality with confidence, grounding, and labeled samples](https://learn.microsoft.com/azure/ai-services/content-understanding/document/analyzer-improvement) — **Mixed concept and practical guide:** understand confidence scores and source references, then follow the Studio labeling workflow to correct sample values and rebuild the analyzer. Training is limited to document analyzers and does not currently support generated fields.
- **Classify content types and route documents** — [Classify and route your data using Content Understanding](https://learn.microsoft.com/azure/ai-services/content-understanding/how-to/classification-content-understanding-studio) — **Step-by-step Studio and API guide:** create custom document categories, test classification, and route each category to an analyzer for field extraction.
- **Create a custom analyzer with confidence and source information** — [Create a custom analyzer](https://learn.microsoft.com/azure/ai-services/content-understanding/tutorial/create-custom-analyzer) — **Hands-on API/SDK tutorial:** define an extraction schema, enable field-source and confidence estimation, create the analyzer, submit a document, and inspect the structured results. Suitable for practicing programmatic integration.

**Content Understanding prerequisites:** an Azure subscription, a Microsoft Foundry resource in a supported region, and the required model deployments/configuration. Follow each guide's setup instructions; Azure resource and model usage can incur costs.

### Related Foundry Tools in Fabric

The following links cover related Azure AI services and Fabric workflows; they are not Content Understanding tutorials or a complete report-commenting solution.

- **Prebuilt Foundry Tools in Fabric** — [Use prebuilt Azure AI services (Foundry Tools) in Fabric](https://learn.microsoft.com/fabric/data-science/ai-services/ai-services-overview) — **Overview/reference:** introduces available AI services for Fabric scenarios and proofs of concept.
- **Foundry Tools with SynapseML** — [Use Foundry Tools with SynapseML in Microsoft Fabric](https://learn.microsoft.com/fabric/data-science/how-to-use-ai-services-with-synapseml) — **Practical code guide:** use Azure AI services with SynapseML in Fabric.
- **Classify natural-language text** — [Classify natural language text with generative AI in Microsoft Fabric](https://learn.microsoft.com/fabric/data-science/tutorial-text-classification) — **Hands-on tutorial:** a Fabric text-classification example, distinct from Content Understanding document classification.
- **Azure AI Language text analytics** — [Use Azure AI Language text analytics in Fabric with SynapseML](https://learn.microsoft.com/fabric/data-science/ai-services/how-to-use-text-analytics) — **Practical code guide:** apply text analytics in Fabric; relevant to text and transcript analysis.
- **Content Safety and Responsible AI** — [What is Azure AI Content Safety?](https://learn.microsoft.com/azure/ai-services/content-safety/overview) — **Overview/reference:** introduces Azure AI Content Safety. This is a conceptual Azure reference, not a Fabric-native hands-on exercise.

[Back to top](#proposed-agenda)

## 4. Copilot in Fabric: Data Transformation, Spark, and SQL

- **Copilot in Fabric overview** — [What is Copilot in Fabric?](https://learn.microsoft.com/fabric/fundamentals/copilot-fabric-overview) — **Overview/reference:** introduces Copilot across Fabric workloads.
- **Copilot in Dataflow Gen2** — [Work smarter with Copilot in Microsoft Fabric Dataflow Gen2](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22a-copilot-fabric-dataflow-gen2.html) — **Hands-on lab (approximately 30 minutes):** clean retail store data, parse XML, create categorical groups, and set data types using natural language prompts. Publish the results to a lakehouse. Requires paid Fabric capacity; trial capacity is not supported.
- **Copilot in Fabric notebooks** — [Analyze data with Apache Spark and Copilot in Microsoft Fabric notebooks](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22b-copilot-fabric-notebooks.html) — **Hands-on lab (approximately 30 minutes):** generate Spark code to clean, filter, and reshape population data, save it to a lakehouse, and visualize the results. Requires paid Fabric capacity; trial capacity is not supported.
- **Copilot in Data Engineering and Data Science** — [Overview of Copilot for Data Engineering and Data Science](https://learn.microsoft.com/fabric/data-engineering/copilot-notebooks-overview) · [Use the Copilot chat pane in notebooks](https://learn.microsoft.com/fabric/data-engineering/copilot-notebooks-chat-pane) — **Overview and feature guide:** introduce notebook Copilot and its chat pane.
- **Copilot in Fabric Data Warehouse** — [Use Copilot in Microsoft Fabric data warehouse](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22c-copilot-fabric-data-warehouse.html) — **Hands-on lab (approximately 30 minutes):** use retail sales data to generate and refine SQL queries, fix syntax errors, and create reusable views with Copilot. Requires paid Fabric capacity; trial capacity is not supported.
- **Data Warehouse Copilot chat pane** — [How to use the Copilot chat pane in Fabric Data Warehouse](https://learn.microsoft.com/fabric/data-warehouse/copilot-chat-pane) — **Feature guide:** use the warehouse Copilot chat experience.
- **Copilot in Data Factory pipelines** — [Get started with Copilot in Fabric in the Data Factory workload](https://learn.microsoft.com/fabric/data-factory/copilot-fabric-data-factory-get-started) — **Getting-started guide:** covers Copilot in the Data Factory workload, including pipelines; distinct from the Dataflow Gen2 lab.
- **Copilot in Real-Time Intelligence** — [Copilot for Real-Time Intelligence](https://learn.microsoft.com/fabric/real-time-intelligence/copilot-real-time-intelligence) · [Generate Real-Time dashboards with Copilot](https://learn.microsoft.com/fabric/real-time-intelligence/copilot-generate-dashboard) — **Overview and how-to:** use Copilot for Real-Time Intelligence, including KQL scenarios and dashboard generation.

[Back to top](#proposed-agenda)

## 5. Fabric AI Functions and Azure OpenAI

- **Fabric AI Functions** — [AI Functions: Transform data at scale with AI](https://learn.microsoft.com/en-us/fabric/data-science/ai-functions/overview?tabs=pandas) — **Practical code guide:** setup instructions and examples for using AI functions across Fabric, with the pandas tab selected. Requires an enabled Fabric tenant setting and paid Fabric capacity.
- **AI Functions in Fabric Data Warehouse** — [AI Functions in a warehouse or SQL analytics endpoint](https://learn.microsoft.com/fabric/data-warehouse/ai-functions) — **Practical SQL guide:** demonstrates text analysis and transformation with T-SQL examples. The feature is in preview and requires supported Fabric capacity and tenant settings.
- **AI Functions with Python and PySpark** — [Apply AI Functions in pandas and PySpark](https://learn.microsoft.com/fabric/data-science/ai-functions/overview#apply-ai-functions) — **Practical code examples:** jumps to pandas and PySpark examples in the AI Functions guide; follow along in a Fabric notebook.
- **Customize AI Functions with PySpark** — [Customize AI Functions with PySpark](https://learn.microsoft.com/en-us/fabric/data-science/ai-functions/pyspark/configuration?tabs=llm-global-pyspark%2Cembedding-global-pyspark%2Cfoundry-openai-pyspark) — **Practical configuration guide:** customize model and embedding settings, concurrency, chaining, statistics, and endpoint configuration for PySpark AI Functions.
- **Azure OpenAI with SynapseML** — [Use Azure OpenAI in Fabric with SynapseML](https://learn.microsoft.com/fabric/data-science/ai-services/how-to-use-openai-synapse-ml) — **Practical code guide:** run PySpark examples for prompts, responses, and embeddings in a Fabric notebook.
- **Azure OpenAI with the OpenAI Python SDK** — [Use Azure OpenAI in Fabric with the OpenAI Python SDK](https://learn.microsoft.com/fabric/data-science/ai-services/how-to-use-openai-python-sdk) — **Practical code guide:** set up a client and run API examples in a Fabric notebook.

[Back to top](#proposed-agenda)

## 6. Fabric IQ and Ontology

- **Fabric IQ** — [What is Fabric IQ?](https://learn.microsoft.com/fabric/iq/overview) — **Overview/reference:** introduces Fabric IQ and its components; it is not a build tutorial.
- **Create a Fabric ontology** — [Ontology tutorial: Introduction and environment setup](https://learn.microsoft.com/fabric/iq/ontology/tutorial-0-introduction) — **Hands-on tutorial series (preview):** prepare sample data, create an ontology with entity types and relationships, bind data, and explore it. Requires Fabric capacity and enabled tenant settings.
- **Build a healthcare ontology manually** — [Create an ontology with Fabric IQ](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/23-build-ontology-manually.html) — **Hands-on lab (preview, approximately 40 minutes):** create entity types, properties, keys, and relationships, then bind hospital reference data from a lakehouse and sample time-series readings from an eventhouse. Uses the new ontology experience; paid or trial Fabric capacity and enabled ontology tenant settings are required.
- **Generate an ontology from a semantic model** — [Build an ontology from a semantic model in Fabric IQ](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/24-build-ontology-semantic-model.html) — **Hands-on lab (preview, approximately 45 minutes):** build a healthcare semantic model, generate ontology entities and relationships, and add eventhouse time-series bindings. Uses the new ontology experience; requires paid or trial Fabric capacity, enabled tenant settings, and Read and Build permissions on the semantic model.
- **Visualize healthcare ontology data** — [Visualize ontology data with Microsoft Fabric IQ](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/27-visualize-ontology.html) — **Hands-on lab (preview, approximately 30 minutes):** use a setup notebook to create the sample ontology, then explore entity instances, relationship graphs, property charts, time-series data, and the Query builder. Requires paid or trial Fabric capacity and enabled ontology tenant settings. Uses the older ontology experience rather than the new experience used in labs 23 and 24.

[Back to top](#proposed-agenda)

## 7. Fabric Data Agents

- **Data Agent concepts and fundamentals** — [What is a Fabric data agent?](https://learn.microsoft.com/fabric/data-science/concept-data-agent) — **Overview/reference:** introduces Fabric Data Agent concepts and capabilities.
- **Fabric Data Agents** — [Create a Fabric data agent](https://learn.microsoft.com/fabric/data-science/how-to-create-data-agent) — **Step-by-step how-to:** create an agent, add data sources, select tables, and configure it. Requires paid Fabric capacity and accessible data.
- **Fabric Data Agent with AdventureWorks** — [Data agent example with the AdventureWorks dataset](https://learn.microsoft.com/fabric/data-science/data-agent-end-to-end-tutorial) — **Hands-on tutorial (preview):** populate a lakehouse with sample data, create an agent, and ask questions. Requires paid Fabric capacity and appropriate tenant settings.
- **Chat with sales data using a Fabric Data Agent** — [Chat with your data using Microsoft Fabric data agents](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22d-copilot-fabric-data-agents.html) — **Hands-on lab (approximately 30 minutes):** create a sales warehouse and configure a data agent, then ask plain English questions and inspect how they are translated into SQL queries. Requires paid Fabric capacity; trial capacity is not supported.
- **Connect a Data Agent to an ontology** — [Create a data agent grounded in an ontology](https://learn.microsoft.com/fabric/iq/ontology/how-to-create-data-agent) — **Step-by-step how-to (preview):** add an ontology as a data source and ask questions in natural language. Currently, ontologies bound to semantic models are not supported by this integration.
- **Build a healthcare Data Agent with an ontology** — [Build a Fabric data agent with an ontology](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/28-build-data-agent-ontology.html) — **Hands-on lab (preview, approximately 30 minutes):** create the Lamna Healthcare ontology with a setup notebook, configure agent instructions, test natural language questions, and publish and share the agent. Requires paid Fabric capacity and appropriate tenant settings; trial capacity is not supported. Uses the older ontology experience, scheduled to retire on January 31, 2027; it is not a direct continuation of lab 24.
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
- **Analyze functional dependencies** — [Analyze functional dependencies in a semantic model](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-dependencies) — **Hands-on notebook tutorial:** use SemPy and a sample model to test dependencies between columns and identify data-quality issues.
- **Extract and calculate Power BI measures** — [Calculate Power BI measures from a Jupyter notebook](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-measures) — **Hands-on notebook tutorial:** list and evaluate measures from a sample semantic model using SemPy.
- **Discover semantic model relationships** — [Discover relationships in a semantic model using semantic link](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-relationships) — **Hands-on notebook tutorial:** discover relationships between tables and check for relationship violations using SemPy.
- **Discover relationships in the Synthea dataset** — [Discover relationships in the Synthea dataset](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-relationships-detection) — **Hands-on notebook tutorial:** detect and visualize relationships in sample data, from a small example to a larger set of tables.
- **Validate data with SemPy and Great Expectations** — [Validate data using SemPy and Great Expectations](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-great-expectations) — **Hands-on notebook tutorial:** configure expectations and validate data from a Power BI semantic model. The tutorial uses Great Expectations versions earlier than 1.0.

[Back to top](#proposed-agenda)

## 10. Retrieval-Augmented Generation (RAG)

- **Build RAG in Fabric** — [Build retrieval-augmented generation in Microsoft Fabric](https://learn.microsoft.com/fabric/data-science/quickstart-building-retrieval-augmented-generation) — **Hands-on notebook quickstart:** prepare data, create embeddings and a vector index, then generate answers. Requires Fabric capacity, a lakehouse, and an Azure AI Search resource.
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
