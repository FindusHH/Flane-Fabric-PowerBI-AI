# 4. GenAI-based Report-Commenting

[Back to agenda](./00_Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [4.1 Analyze Power BI Reports with Content Understanding](#41-analyze-power-bi-reports-with-content-understanding)
- [4.2 Content Understanding: Background and Quality](#42-content-understanding-background-and-quality)
- [4.3 Generate Narratives in Power BI](#43-generate-narratives-in-power-bi)
- [4.4 Extract and Validate Content](#44-extract-and-validate-content)
- [4.5 Related Foundry Tools in Fabric](#45-related-foundry-tools-in-fabric)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. 🛠️ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

This topic covers AI-generated Power BI narratives and Azure Content Understanding for extracting and validating information from source content. The Content Understanding exercises do not themselves build a Power BI report-commenting solution; integrating their output into reports is a separate task.

## 4.1 Analyze Power BI Reports with Content Understanding

Content Understanding does not natively analyze PBIX files or connect to interactive Power BI reports and their semantic models. It can analyze supported exports, such as PDFs or screenshots, to extract and interpret visible text, tables, and chart content. These exports represent a specific report state: DAX logic, model relationships, non-visible data, and interactive filtering are not available. Verify extracted numbers and chart interpretations; confidence scores do not establish that a business interpretation is correct. See [Supported input file types and limits](https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/service-limits#input-file-limits).

For this workshop, distinguish three use cases:

- **Generate commentary inside Power BI:** use Copilot narratives, covered in the practical guide below.

- **Analyze exported reports or supporting source documents:** use Content Understanding, then integrate the extracted results into Power BI separately.

- **Inspect semantic models programmatically:** use Semantic Link/SemPy, covered under Semantic Link and Semantic Model Analysis.

## 4.2 Content Understanding: Background and Quality

Content Understanding uses multiple AI models to analyze and cross-validate content. Confidence scores and grounding help assess extracted values and trace them to source documents; they do not guarantee correctness. The exercises below cover custom schemas, labeled examples, document classification, and scenario-specific prebuilt analyzers.

Potential industry scenarios include tax preparation, procurement documents, contract analysis, call center analytics, and media analysis. Check the available prebuilt analyzers for the selected scenario and region.

## 4.3 Generate Narratives in Power BI

- **AI-generated report commentary in Power BI** — [Create a narrative visual with Copilot for Power BI](https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-create-narrative) — **Step-by-step how-to:** generate a narrative for a report, page, or selected visuals and refine it with prompts. Requires enabled Copilot and supported paid Fabric capacity.

- **Smart narrative summaries** — [Create smart narrative summaries](https://learn.microsoft.com/en-us/power-bi/visuals/power-bi-visualization-smart-narrative) — **Feature guide:** create and customize smart narrative summaries in Power BI; this is a related option distinct from the Copilot narrative guide.

## 4.4 Extract and Validate Content

- 🛠️ **Try industry-specific prebuilt analyzers** — [Quickstart: Try Content Understanding Studio or Microsoft Foundry](https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/quickstart/content-understanding-studio) — **Hands-on Studio quickstart:** select a prebuilt analyzer for your scenario, analyze sample or uploaded content, and review extracted fields. Use Studio to explore the available domain-specific analyzers.

- **Create and improve a custom analyzer in Studio** — [Create and improve your custom analyzer in Content Understanding Studio](https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/how-to/customize-analyzer-content-understanding-studio) — **Step-by-step UI guide:** upload sample content, select a template, refine suggested fields, test the schema, and build an analyzer. Optionally use labeled document examples to improve extraction quality.

- **Inspect confidence and grounding; improve extraction with labeled samples** — [Validate document analyzer quality with confidence, grounding, and labeled samples](https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/document/analyzer-improvement) — **Mixed concept and practical guide:** understand confidence scores and source references, then follow the Studio labeling workflow to correct sample values and rebuild the analyzer. Training is limited to document analyzers and does not currently support generated fields.

- **Classify content types and route documents** — [Classify and route your data using Content Understanding](https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/how-to/classification-content-understanding-studio) — **Step-by-step Studio and API guide:** create custom document categories, test classification, and route each category to an analyzer for field extraction.

- 🛠️ **Create a custom analyzer with confidence and source information** — [Create a custom analyzer](https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/tutorial/create-custom-analyzer) — **Hands-on API/SDK tutorial:** define an extraction schema, enable field-source and confidence estimation, create the analyzer, submit a document, and inspect the structured results. Suitable for practicing programmatic integration.

**Content Understanding prerequisites:** an Azure subscription, a Microsoft Foundry resource in a supported region, and the required model deployments/configuration. Follow each guide's setup instructions; Azure resource and model usage can incur costs.

## 4.5 Related Foundry Tools in Fabric

The following links cover related Azure AI services and Fabric workflows; they are not Content Understanding tutorials or a complete report-commenting solution.

- **Prebuilt Foundry Tools in Fabric** — [Use prebuilt Azure AI services (Foundry Tools) in Fabric](https://learn.microsoft.com/en-us/fabric/data-science/ai-services/ai-services-overview) — **Overview/reference:** introduces available AI services for Fabric scenarios and proofs of concept.

- **Foundry Tools with SynapseML** — [Use Foundry Tools with SynapseML in Microsoft Fabric](https://learn.microsoft.com/en-us/fabric/data-science/how-to-use-ai-services-with-synapseml) — **Practical code guide:** use Azure AI services with SynapseML in Fabric.

- **Classify natural-language text** — [Classify natural language text with generative AI in Microsoft Fabric](https://learn.microsoft.com/en-us/fabric/data-science/tutorial-text-classification) — **Conceptual guide with practical code examples:** describes a Fabric text-classification architecture, prompts, and PySpark snippets. Adapting placeholders, data, and pipeline configuration is required; this is distinct from Content Understanding document classification.

- **Azure AI Language text analytics** — [Use Azure AI Language text analytics in Fabric with SynapseML](https://learn.microsoft.com/en-us/fabric/data-science/ai-services/how-to-use-text-analytics) — **Practical code guide:** apply text analytics in Fabric; relevant to text and transcript analysis.

- **Content Safety and Responsible AI** — [What is Azure AI Content Safety?](https://learn.microsoft.com/en-us/azure/ai-services/content-safety/overview) — **Overview/reference:** introduces Azure AI Content Safety. This is a conceptual Azure reference, not a Fabric-native hands-on exercise.

[Back to contents](#chapter-contents)

[Back to agenda](./00_Agenda%20with%20Tutorials.md)
