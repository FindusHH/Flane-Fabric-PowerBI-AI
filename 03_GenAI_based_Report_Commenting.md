# 3. GenAI-based Report-Commenting

[Back to agenda](./00_Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [3.1 Analyze Power BI Reports with Content Understanding](#31-analyze-power-bi-reports-with-content-understanding)
- [3.2 Content Understanding: Background and Quality](#32-content-understanding-background-and-quality)
- [3.3 Generate Narratives in Power BI](#33-generate-narratives-in-power-bi)
- [3.4 Extract and Validate Content](#34-extract-and-validate-content)
- [3.5 Related Foundry Tools in Fabric](#35-related-foundry-tools-in-fabric)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. ⭐ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

**Hands-on tutorials at a glance**

| Hands-on tutorial | Section | Focus |
| --- | --- | --- |
| ⭐ <a href="https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/quickstart/content-understanding-studio" target="_blank" rel="noopener noreferrer">Try industry-specific prebuilt analyzers</a> | [3.4 Extract and Validate Content](#34-extract-and-validate-content) | Explore a prebuilt analyzer in Content Understanding Studio or Microsoft Foundry, analyze sample or uploaded content, and review the extracted fields. |
| ⭐ <a href="https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/tutorial/create-custom-analyzer" target="_blank" rel="noopener noreferrer">Create a custom analyzer with confidence and source information</a> | [3.4 Extract and Validate Content](#34-extract-and-validate-content) | Create an analyzer through the API/SDK, submit a document, and inspect extracted fields, confidence estimates, and source information. |

This topic covers AI-generated Power BI narratives and Azure Content Understanding for extracting and validating information from source content. The Content Understanding exercises do not themselves build a Power BI report-commenting solution; integrating their output into reports is a separate task.

## 3.1 Analyze Power BI Reports with Content Understanding

Content Understanding does not natively analyze PBIX files or connect to interactive Power BI reports and their semantic models. It can analyze supported exports, such as PDFs or screenshots, to extract and interpret visible text, tables, and chart content. These exports represent a specific report state: DAX logic, model relationships, non-visible data, and interactive filtering are not available. Verify extracted numbers and chart interpretations; confidence scores do not establish that a business interpretation is correct. See <a href="https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/service-limits#input-file-limits" target="_blank" rel="noopener noreferrer">Supported input file types and limits</a>.

For this workshop, distinguish three use cases:

- **Generate commentary inside Power BI:** use Copilot narratives, covered in the practical guide below.

- **Analyze exported reports or supporting source documents:** use Content Understanding, then integrate the extracted results into Power BI separately.

- **Inspect semantic models programmatically:** use Semantic Link/SemPy, covered under Semantic Link and Semantic Model Analysis.

## 3.2 Content Understanding: Background and Quality

Content Understanding uses multiple AI models to analyze and cross-validate content. Confidence scores and grounding help assess extracted values and trace them to source documents; they do not guarantee correctness. The exercises below cover custom schemas, labeled examples, document classification, and scenario-specific prebuilt analyzers.

Potential industry scenarios include tax preparation, procurement documents, contract analysis, call center analytics, and media analysis. Check the available prebuilt analyzers for the selected scenario and region.

## 3.3 Generate Narratives in Power BI

- **AI-generated report commentary in Power BI** — <a href="https://learn.microsoft.com/en-us/power-bi/create-reports/copilot-create-narrative" target="_blank" rel="noopener noreferrer">Create a narrative visual with Copilot for Power BI</a> — **Step-by-step how-to:** generate a narrative for a report, page, or selected visuals and refine it with prompts. Requires enabled Copilot and supported paid Fabric capacity.

- **Smart narrative summaries** — <a href="https://learn.microsoft.com/en-us/power-bi/visuals/power-bi-visualization-smart-narrative" target="_blank" rel="noopener noreferrer">Create smart narrative summaries</a> — **Feature guide:** create and customize smart narrative summaries in Power BI; this is a related option distinct from the Copilot narrative guide.

## 3.4 Extract and Validate Content

- ⭐ **Try industry-specific prebuilt analyzers** — <a href="https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/quickstart/content-understanding-studio" target="_blank" rel="noopener noreferrer">Quickstart: Try Content Understanding Studio or Microsoft Foundry</a> — **Hands-on quickstart:** select a prebuilt analyzer for your scenario, analyze sample or uploaded content, and review extracted fields. Explore the available analyzers in Content Understanding Studio or Microsoft Foundry.

  **IMPORTANT: Training environment updates:**

  - In the tutorial, select the **Microsoft Foundry (new)** tab.
  - In the Foundry portal, use **Services** instead of **AI Services** to open the **Content Understanding Playground**.
  - If asked to configure model defaults, try a chat-completion deployment of `gpt-5-mini` or `gpt-5.2`, depending on availability in your training environment. Configure any separately required embedding model as well; see <a href="https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/service-limits#supported-generative-models" target="_blank" rel="noopener noreferrer">supported generative models</a>.

- **Create and improve a custom analyzer in Studio** — <a href="https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/how-to/customize-analyzer-content-understanding-studio" target="_blank" rel="noopener noreferrer">Create and improve your custom analyzer in Content Understanding Studio</a> — **Step-by-step UI guide:** upload sample content, select a template, refine suggested fields, test the schema, and build an analyzer. Optionally use labeled document examples to improve extraction quality.

- **Inspect confidence and grounding; improve extraction with labeled samples** — <a href="https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/document/analyzer-improvement" target="_blank" rel="noopener noreferrer">Validate document analyzer quality with confidence, grounding, and labeled samples</a> — **Mixed concept and practical guide:** understand confidence scores and source references, then follow the Studio labeling workflow to correct sample values and rebuild the analyzer. Training is limited to document analyzers and does not currently support generated fields.

- **Classify content types and route documents** — <a href="https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/how-to/classification-content-understanding-studio" target="_blank" rel="noopener noreferrer">Classify and route your data using Content Understanding</a> — **Step-by-step Studio and API guide:** create custom document categories, test classification, and route each category to an analyzer for field extraction.

- ⭐ **Create a custom analyzer with confidence and source information** — <a href="https://learn.microsoft.com/en-us/azure/ai-services/content-understanding/tutorial/create-custom-analyzer" target="_blank" rel="noopener noreferrer">Create a custom analyzer</a> — **Hands-on API/SDK tutorial:** define an extraction schema, enable field-source and confidence estimation, create the analyzer, submit a document, and inspect the structured results. Suitable for practicing programmatic integration.

**Content Understanding prerequisites:** an Azure subscription, a Microsoft Foundry resource in a supported region, and the required model deployments/configuration. Follow each guide's setup instructions; Azure resource and model usage can incur costs.

## 3.5 Related Foundry Tools in Fabric

The following links cover related Azure AI services and Fabric workflows; they are not Content Understanding tutorials or a complete report-commenting solution.

- **Prebuilt Foundry Tools in Fabric** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/ai-services/ai-services-overview" target="_blank" rel="noopener noreferrer">Use prebuilt Azure AI services (Foundry Tools) in Fabric</a> — **Overview/reference:** introduces available AI services for Fabric scenarios and proofs of concept.

- **Foundry Tools with SynapseML** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/how-to-use-ai-services-with-synapseml" target="_blank" rel="noopener noreferrer">Use Foundry Tools with SynapseML in Microsoft Fabric</a> — **Practical code guide:** use Azure AI services with SynapseML in Fabric.

- **Classify natural-language text** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/tutorial-text-classification" target="_blank" rel="noopener noreferrer">Classify natural language text with generative AI in Microsoft Fabric</a> — **Conceptual guide with practical code examples:** describes a Fabric text-classification architecture, prompts, and PySpark snippets. Adapting placeholders, data, and pipeline configuration is required; this is distinct from Content Understanding document classification.

- **Azure AI Language text analytics** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/ai-services/how-to-use-text-analytics" target="_blank" rel="noopener noreferrer">Use Azure AI Language text analytics in Fabric with SynapseML</a> — **Practical code guide:** apply text analytics in Fabric; relevant to text and transcript analysis.

- **Content Safety and Responsible AI** — <a href="https://learn.microsoft.com/en-us/azure/ai-services/content-safety/overview" target="_blank" rel="noopener noreferrer">What is Azure AI Content Safety?</a> — **Overview/reference:** introduces Azure AI Content Safety. This is a conceptual Azure reference, not a Fabric-native hands-on exercise.

[Back to contents](#chapter-contents)

[Back to agenda](./00_Agenda%20with%20Tutorials.md)
