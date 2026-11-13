# Proposed Agenda

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

## Copilot in Power BI: Reports and DAX

- **Ask questions about a semantic model** — [Use Copilot with semantic models](https://learn.microsoft.com/power-bi/create-reports/copilot-semantic-models) — **Feature and workflow guide:** explains model preparation and Copilot experiences; useful context, but not one end-to-end exercise.
- **Copilot in Power BI** — [Copilot in Power BI: End-to-End Tutorial](https://learn.microsoft.com/power-bi/create-reports/tutorial-copilot-power-bi-introduction) — **Hands-on end-to-end tutorial:** follows a scenario from preparing a semantic model to exploring insights with Copilot.
- **Create reports with Copilot** — [Create and edit Power BI reports with Copilot](https://learn.microsoft.com/power-bi/create-reports/copilot-create-reports) — **Step-by-step how-to:** create a report page with prompts, then add, change, or delete visuals.
- **Create DAX queries with Copilot** — [Write DAX queries with Copilot](https://learn.microsoft.com/dax/dax-copilot) — **Step-by-step how-to:** enable Copilot in DAX query view, generate a query, run it, and keep or discard it.

## GenAI-based Report-Commenting

This topic covers AI-generated Power BI narratives and Azure Content Understanding for extracting and validating information from source content. The Content Understanding exercises do not themselves build a Power BI report-commenting solution; integrating their output into reports is a separate task.

### Analyzing Power BI Reports with Content Understanding

Content Understanding does not natively analyze PBIX files or connect to interactive Power BI reports and their semantic models. It can analyze supported exports, such as PDFs or screenshots, to extract and interpret visible text, tables, and chart content. These exports represent a specific report state: DAX logic, model relationships, non-visible data, and interactive filtering are not available. Verify extracted numbers and chart interpretations; confidence scores do not establish that a business interpretation is correct. See [Supported input file types and limits](https://learn.microsoft.com/azure/ai-services/content-understanding/service-limits#input-file-limits).

For this workshop, distinguish three use cases:

- **Generate commentary inside Power BI:** use Copilot narratives, covered in the practical guide below.
- **Analyze exported reports or supporting source documents:** use Content Understanding, then integrate the extracted results into Power BI separately.
- **Inspect semantic models programmatically:** use Semantic Link/SemPy, covered under Semantic Link and Semantic Model Analysis.

### Background and Quality Considerations

Content Understanding uses multiple AI models to analyze and cross-validate content. Confidence scores and grounding help assess extracted values and trace them to source documents; they do not guarantee correctness. The exercises below cover custom schemas, labeled examples, document classification, and scenario-specific prebuilt analyzers.

### Practical Tutorials and How-to Guides

- **AI-generated report commentary in Power BI** — [Create a narrative visual with Copilot for Power BI](https://learn.microsoft.com/power-bi/create-reports/copilot-create-narrative) — **Step-by-step how-to:** generate a narrative for a report, page, or selected visuals and refine it with prompts. Requires enabled Copilot and supported paid Fabric capacity.
- **Try industry-specific prebuilt analyzers** — [Quickstart: Try Content Understanding Studio or Microsoft Foundry](https://learn.microsoft.com/azure/ai-services/content-understanding/quickstart/content-understanding-studio) — **Hands-on Studio quickstart:** select a prebuilt analyzer for your scenario, analyze sample or uploaded content, and review extracted fields. Use Studio to explore the available domain-specific analyzers.
- **Create and improve a custom analyzer in Studio** — [Create and improve your custom analyzer in Content Understanding Studio](https://learn.microsoft.com/azure/ai-services/content-understanding/how-to/customize-analyzer-content-understanding-studio) — **Step-by-step UI guide:** upload sample content, select a template, refine suggested fields, test the schema, and build an analyzer. Optionally use labeled document examples to improve extraction quality.
- **Inspect confidence and grounding; improve extraction with labeled samples** — [Validate document analyzer quality with confidence, grounding, and labeled samples](https://learn.microsoft.com/azure/ai-services/content-understanding/document/analyzer-improvement) — **Mixed concept and practical guide:** understand confidence scores and source references, then follow the Studio labeling workflow to correct sample values and rebuild the analyzer. Training is limited to document analyzers and does not currently support generated fields.
- **Classify content types and route documents** — [Classify and route your data using Content Understanding](https://learn.microsoft.com/azure/ai-services/content-understanding/how-to/classification-content-understanding-studio) — **Step-by-step Studio and API guide:** create custom document categories, test classification, and route each category to an analyzer for field extraction.
- **Create a custom analyzer with confidence and source information** — [Create a custom analyzer](https://learn.microsoft.com/azure/ai-services/content-understanding/tutorial/create-custom-analyzer) — **Hands-on API/SDK tutorial:** define an extraction schema, enable field-source and confidence estimation, create the analyzer, submit a document, and inspect the structured results. Suitable for practicing programmatic integration.

**Content Understanding prerequisites:** an Azure subscription, a Microsoft Foundry resource in a supported region, and the required model deployments/configuration. Follow each guide's setup instructions; Azure resource and model usage can incur costs.

## Copilot in Fabric: Data Transformation, Spark, and SQL

- **Copilot in Dataflow Gen2** — [Work smarter with Copilot in Microsoft Fabric Dataflow Gen2](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22a-copilot-fabric-dataflow-gen2.html) — **Hands-on lab (approximately 30 minutes):** clean retail store data, parse XML, create categorical groups, and set data types using natural language prompts. Publish the results to a lakehouse. Requires paid Fabric capacity; trial capacity is not supported.
- **Copilot in Fabric notebooks** — [Analyze data with Apache Spark and Copilot in Microsoft Fabric notebooks](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22b-copilot-fabric-notebooks.html) — **Hands-on lab (approximately 30 minutes):** generate Spark code to clean, filter, and reshape population data, save it to a lakehouse, and visualize the results. Requires paid Fabric capacity; trial capacity is not supported.
- **Copilot in Fabric Data Warehouse** — [Use Copilot in Microsoft Fabric data warehouse](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22c-copilot-fabric-data-warehouse.html) — **Hands-on lab (approximately 30 minutes):** use retail sales data to generate and refine SQL queries, fix syntax errors, and create reusable views with Copilot. Requires paid Fabric capacity; trial capacity is not supported.

## Fabric AI Functions and Azure OpenAI

- **Fabric AI Functions** — [AI Functions: Transform data at scale with AI](https://learn.microsoft.com/fabric/data-science/ai-functions/overview) — **Practical code guide:** setup instructions and examples for using AI functions across Fabric. Requires an enabled Fabric tenant setting and paid Fabric capacity.
- **AI Functions in Fabric Data Warehouse** — [AI Functions in a warehouse or SQL analytics endpoint](https://learn.microsoft.com/fabric/data-warehouse/ai-functions) — **Practical SQL guide:** demonstrates text analysis and transformation with T-SQL examples. The feature is in preview and requires supported Fabric capacity and tenant settings.
- **AI Functions with Python and PySpark** — [Apply AI Functions in pandas and PySpark](https://learn.microsoft.com/fabric/data-science/ai-functions/overview#apply-ai-functions) — **Practical code examples:** jumps to pandas and PySpark examples in the AI Functions guide; follow along in a Fabric notebook.
- **Azure OpenAI with SynapseML** — [Use Azure OpenAI in Fabric with SynapseML](https://learn.microsoft.com/fabric/data-science/ai-services/how-to-use-openai-synapse-ml) — **Practical code guide:** run PySpark examples for prompts, responses, and embeddings in a Fabric notebook.
- **Azure OpenAI with the OpenAI Python SDK** — [Use Azure OpenAI in Fabric with the OpenAI Python SDK](https://learn.microsoft.com/fabric/data-science/ai-services/how-to-use-openai-python-sdk) — **Practical code guide:** set up a client and run API examples in a Fabric notebook.

## Fabric IQ and Ontology

- **Fabric IQ** — [What is Fabric IQ?](https://learn.microsoft.com/fabric/iq/overview) — **Overview/reference:** introduces Fabric IQ and its components; it is not a build tutorial.
- **Create a Fabric ontology** — [Ontology tutorial: Introduction and environment setup](https://learn.microsoft.com/fabric/iq/ontology/tutorial-0-introduction) — **Hands-on tutorial series (preview):** prepare sample data, create an ontology with entity types and relationships, bind data, and explore it. Requires Fabric capacity and enabled tenant settings.
- **Build a healthcare ontology manually** — [Create an ontology with Fabric IQ](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/23-build-ontology-manually.html) — **Hands-on lab (preview, approximately 40 minutes):** create entity types, properties, keys, and relationships, then bind hospital reference data from a lakehouse and sample time-series readings from an eventhouse. Uses the new ontology experience; paid or trial Fabric capacity and enabled ontology tenant settings are required.
- **Generate an ontology from a semantic model** — [Build an ontology from a semantic model in Fabric IQ](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/24-build-ontology-semantic-model.html) — **Hands-on lab (preview, approximately 45 minutes):** build a healthcare semantic model, generate ontology entities and relationships, and add eventhouse time-series bindings. Uses the new ontology experience; requires paid or trial Fabric capacity, enabled tenant settings, and Read and Build permissions on the semantic model.
- **Visualize healthcare ontology data** — [Visualize ontology data with Microsoft Fabric IQ](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/27-visualize-ontology.html) — **Hands-on lab (preview, approximately 30 minutes):** use a setup notebook to create the sample ontology, then explore entity instances, relationship graphs, property charts, time-series data, and the Query builder. Requires paid or trial Fabric capacity and enabled ontology tenant settings. Uses the older ontology experience rather than the new experience used in labs 23 and 24.

## Fabric Data Agents

- **Fabric Data Agents** — [Create a Fabric data agent](https://learn.microsoft.com/fabric/data-science/how-to-create-data-agent) — **Step-by-step how-to:** create an agent, add data sources, select tables, and configure it. Requires paid Fabric capacity and accessible data.
- **Fabric Data Agent with AdventureWorks** — [Data agent example with the AdventureWorks dataset](https://learn.microsoft.com/fabric/data-science/data-agent-end-to-end-tutorial) — **Hands-on tutorial (preview):** populate a lakehouse with sample data, create an agent, and ask questions. Requires paid Fabric capacity and appropriate tenant settings.
- **Chat with sales data using a Fabric Data Agent** — [Chat with your data using Microsoft Fabric data agents](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22d-copilot-fabric-data-agents.html) — **Hands-on lab (approximately 30 minutes):** create a sales warehouse and configure a data agent, then ask plain English questions and inspect how they are translated into SQL queries. Requires paid Fabric capacity; trial capacity is not supported.
- **Connect a Data Agent to an ontology** — [Create a data agent grounded in an ontology](https://learn.microsoft.com/fabric/iq/ontology/how-to-create-data-agent) — **Step-by-step how-to (preview):** add an ontology as a data source and ask questions in natural language. Currently, ontologies bound to semantic models are not supported by this integration.
- **Build a healthcare Data Agent with an ontology** — [Build a Fabric data agent with an ontology](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/28-build-data-agent-ontology.html) — **Hands-on lab (preview, approximately 30 minutes):** create the Lamna Healthcare ontology with a setup notebook, configure agent instructions, test natural language questions, and publish and share the agent. Requires paid Fabric capacity and appropriate tenant settings; trial capacity is not supported. Uses the older ontology experience, scheduled to retire on January 31, 2027; it is not a direct continuation of lab 24.

## Fabric Operations Agents

- **Create a Fabric Operations Agent** — [Create and configure operations agents](https://learn.microsoft.com/fabric/real-time-intelligence/operations-agent) — **Step-by-step how-to:** configure an agent to monitor data, generate a playbook, and recommend actions. Requires non-trial Fabric capacity, a data source, Microsoft Teams, and enabled tenant settings.
- **Connect an Operations Agent to an ontology** — [Create an operations agent grounded in an ontology](https://learn.microsoft.com/fabric/iq/ontology/how-to-create-operations-agent) — **Step-by-step how-to (preview):** use an ontology as the agent's knowledge source, configure monitoring, and receive recommendations in Teams. Currently, ontologies bound to semantic models are not supported by this integration.

## Semantic Link and Semantic Model Analysis

- **Semantic link** — [What is semantic link?](https://learn.microsoft.com/en-us/fabric/data-science/semantic-link-overview) — **Overview/reference:** explains how semantic link connects Power BI semantic models with Fabric data science and notebooks.
- **Semantic Link Labs code examples** — [Code Examples](https://github.com/microsoft/semantic-link-labs/wiki/Code-Examples) — **Practical code examples:** use Python notebook snippets for tasks such as model best-practice analysis and memory analysis.
- **Semantic link sample notebooks** — [Semantic link samples](https://github.com/microsoft/fabric-samples/tree/main/docs-samples/data-science/semantic-link-samples) — **Sample notebook collection:** download the notebooks accompanying the semantic link tutorials below; the repository itself is not a step-by-step guide.
- **Use notebooks with a semantic model** — [Use notebooks with a semantic model](https://learn.microsoft.com/power-bi/transform-model/service-notebooks) — **Practical guide:** open ready-made notebooks from a semantic model to run best-practice and memory analysis. Requires suitable workspace access, model permissions, and Fabric capacity.
- **Analyze functional dependencies** — [Analyze functional dependencies in a semantic model](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-dependencies) — **Hands-on notebook tutorial:** use SemPy and a sample model to test dependencies between columns and identify data-quality issues.
- **Extract and calculate Power BI measures** — [Calculate Power BI measures from a Jupyter notebook](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-measures) — **Hands-on notebook tutorial:** list and evaluate measures from a sample semantic model using SemPy.
- **Discover semantic model relationships** — [Discover relationships in a semantic model using semantic link](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-power-bi-relationships) — **Hands-on notebook tutorial:** discover relationships between tables and check for relationship violations using SemPy.
- **Discover relationships in the Synthea dataset** — [Discover relationships in the Synthea dataset](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-relationships-detection) — **Hands-on notebook tutorial:** detect and visualize relationships in sample data, from a small example to a larger set of tables.
- **Validate data with SemPy and Great Expectations** — [Validate data using SemPy and Great Expectations](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-great-expectations) — **Hands-on notebook tutorial:** configure expectations and validate data from a Power BI semantic model. The tutorial uses Great Expectations versions earlier than 1.0.

## Retrieval-Augmented Generation (RAG)

- **Build RAG in Fabric** — [Build retrieval-augmented generation in Microsoft Fabric](https://learn.microsoft.com/fabric/data-science/quickstart-building-retrieval-augmented-generation) — **Hands-on notebook quickstart:** prepare data, create embeddings and a vector index, then generate answers. Requires Fabric capacity, a lakehouse, and an Azure AI Search resource.

## General Fabric Samples

- **Microsoft Fabric Samples** — [Fabric samples repository](https://github.com/microsoft/fabric-samples/tree/main) — **Sample collection:** browse documentation, feature, and community examples, including code and sample data.
