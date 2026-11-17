# 5. Fabric AI Functions and Azure OpenAI

[Back to agenda](./00_Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [5.1 Fabric AI Functions: Overview and Setup](#51-fabric-ai-functions-overview-and-setup)
- [5.2 Use and Customize AI Functions in Notebooks](#52-use-and-customize-ai-functions-in-notebooks)
- [5.3 Use AI Functions in Fabric Data Warehouse](#53-use-ai-functions-in-fabric-data-warehouse)
- [5.4 Integrate Azure OpenAI in Fabric Notebooks](#54-integrate-azure-openai-in-fabric-notebooks)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. ⭐ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

**Hands-on tutorials at a glance**

| Hands-on tutorial | Section | Focus |
| --- | --- | --- |
| ⭐ [Get started with AI Functions in PySpark](https://github.com/microsoft/fabric-samples/blob/main/docs-samples/data-science/ai-functions/starter-notebooks/AIFunctions-PySpark-starter-notebook.ipynb) | [5.2 Use and Customize AI Functions in Notebooks](#52-use-and-customize-ai-functions-in-notebooks) | Apply AI Functions to customer reviews with PySpark, inspect results, and build a dashboard. |
| ⭐ [Get started with AI Functions in pandas](https://github.com/microsoft/fabric-samples/blob/main/docs-samples/data-science/ai-functions/starter-notebooks/AIFunctions-pandas-starter-notebook.ipynb) | [5.2 Use and Customize AI Functions in Notebooks](#52-use-and-customize-ai-functions-in-notebooks) | Apply AI Functions to customer reviews with pandas, inspect results, and build a dashboard. |
| ⭐ [Use AI Functions in a Fabric Warehouse](https://learn.microsoft.com/en-us/fabric/data-warehouse/tutorial-ai-functions) | [5.3 Use AI Functions in Fabric Data Warehouse](#53-use-ai-functions-in-fabric-data-warehouse) | Run guided T-SQL exercises to extract, generate, summarize, and persist AI results. |
| ⭐ [Use Azure OpenAI for big data with SynapseML](https://learn.microsoft.com/en-us/fabric/data-science/open-ai) | [5.4 Integrate Azure OpenAI in Fabric Notebooks](#54-integrate-azure-openai-in-fabric-notebooks) | Modernize the notebook for a Microsoft Foundry resource and the Responses API, then run Spark examples for prompts and embeddings. |

**Teaching note:** Start with the shared AI Functions concepts and prerequisites. Then explore notebook-based use and configuration, followed by the separate SQL experience in Fabric Data Warehouse. Finish with direct Azure OpenAI integrations in notebooks. Distinguish Fabric AI Functions, which provide managed functions for data transformation, from calling Azure OpenAI through SynapseML or the OpenAI Python SDK; these approaches have different setup, configuration, and endpoint requirements.

## 5.1 Fabric AI Functions: Overview and Setup

- **Fabric AI Functions** — [AI Functions: Transform data at scale with AI](https://learn.microsoft.com/en-us/fabric/data-science/ai-functions/overview?tabs=pandas) — **Practical code guide:** setup instructions and examples for using AI functions across Fabric, with the pandas tab selected. Requires an enabled Fabric tenant setting and paid Fabric capacity.

## 5.2 Use and Customize AI Functions in Notebooks

- **AI Functions with Python and PySpark** — [Apply AI Functions in pandas and PySpark](https://learn.microsoft.com/en-us/fabric/data-science/ai-functions/overview#apply-ai-functions) — **Practical code examples:** jumps to pandas and PySpark examples in the AI Functions guide; follow along in a Fabric notebook.

- ⭐ **Get started with AI Functions in PySpark** — [PySpark AI Functions starter notebook](https://github.com/microsoft/fabric-samples/blob/main/docs-samples/data-science/ai-functions/starter-notebooks/AIFunctions-PySpark-starter-notebook.ipynb) — **Hands-on notebook tutorial:** configure and apply AI Functions to a sample of customer reviews, inspect the results, and build a compact dashboard. Requires Fabric Runtime 1.3 or later and the AI Functions prerequisites described above.

- ⭐ **Get started with AI Functions in pandas** — [Pandas AI Functions starter notebook](https://github.com/microsoft/fabric-samples/blob/main/docs-samples/data-science/ai-functions/starter-notebooks/AIFunctions-pandas-starter-notebook.ipynb) — **Hands-on notebook tutorial:** apply AI Functions to sample customer reviews, inspect the results, and build a compact dashboard. Requires Fabric Runtime 1.3 or later, the AI Functions prerequisites described above, and the notebook's Python package setup.

- **Further AI Functions notebooks** — [AI Functions notebook collection](https://github.com/microsoft/fabric-samples/tree/main/docs-samples/data-science/ai-functions) — **Sample notebook collection:** find links to further PySpark and pandas notebooks, including examples for evaluating sentiment analysis, classification, extraction, grammar correction, summarization, and translation. The collection itself is not a single guided exercise.

- **Customize AI Functions with PySpark** — [Customize AI Functions with PySpark](https://learn.microsoft.com/en-us/fabric/data-science/ai-functions/pyspark/configuration?tabs=llm-global-pyspark%2Cembedding-global-pyspark%2Cfoundry-openai-pyspark) — **Practical configuration guide:** customize model and embedding settings, concurrency, chaining, statistics, and endpoint configuration for PySpark AI Functions.

## 5.3 Use AI Functions in Fabric Data Warehouse

- **AI Functions in Fabric Data Warehouse** — [AI Functions in a warehouse or SQL analytics endpoint](https://learn.microsoft.com/en-us/fabric/data-warehouse/ai-functions) — **Practical SQL guide:** demonstrates text analysis and transformation with T-SQL examples. The feature is in preview and requires supported Fabric capacity and tenant settings.

- ⭐ **Use AI Functions in a Fabric Warehouse** — [Tutorial: Use AI functions in a warehouse](https://learn.microsoft.com/en-us/fabric/data-warehouse/tutorial-ai-functions) — **Hands-on tutorial:** run guided T-SQL exercises to extract, generate, summarize, and persist AI results using sample sales data. First complete the setup steps to [create a workspace](https://learn.microsoft.com/en-us/fabric/data-warehouse/tutorial-create-workspace), [create a warehouse](https://learn.microsoft.com/en-us/fabric/data-warehouse/tutorial-create-warehouse), and [ingest sample data](https://learn.microsoft.com/en-us/fabric/data-warehouse/tutorial-ingest-data). Requires a paid Fabric capacity and enabled tenant settings; run the data-changing steps in a test warehouse.

  ⚠️ **Training environment notes:**

  - The data-ingestion instructions are not fully up to date for this training environment. Use both a Fabric Copy job and the necessary T-SQL import steps, although the guide presents them as alternatives. Check existing tables and data first to avoid creation conflicts or duplicate imports.
  - If a `SELECT` query takes too long, try `SELECT TOP (1000) ...` to limit the returned rows. Use `ORDER BY` when a reproducible subset is needed. The results then cover only that subset; this does not limit rows changed by a subsequent `UPDATE`.

## 5.4 Integrate Azure OpenAI in Fabric Notebooks

- **Azure OpenAI with SynapseML** — [Use Azure OpenAI in Fabric with SynapseML](https://learn.microsoft.com/en-us/fabric/data-science/ai-services/how-to-use-openai-synapse-ml) — **Practical code guide:** run PySpark examples for prompts, responses, and embeddings in a Fabric notebook.

- ⭐ **Use Azure OpenAI for big data with SynapseML** — [Azure OpenAI for big data](https://learn.microsoft.com/en-us/fabric/data-science/open-ai) — **Hands-on notebook tutorial:** download and import the provided notebook into Fabric, configure a working Azure OpenAI resource, install SynapseML, then run and adapt Spark examples for prompts and embeddings. Requires an Azure OpenAI resource and a compatible Fabric Spark runtime.

  ⚠️ **Notebook modernization notes:**

  - The tutorial notebook uses older implementation patterns, including the Chat Completions API rather than the Responses API. For this workshop, update text-generation calls to use Responses. Chat Completions remains supported; this is a modernization recommendation. Keep embedding calls on the embeddings API. The [current SynapseML guide](https://learn.microsoft.com/en-us/fabric/data-science/ai-services/how-to-use-openai-synapse-ml) includes Responses examples.
  - GitHub Copilot can help modernize the notebook with a few focused prompts. Review and test the updated cells, and verify compatibility with the installed SynapseML version and selected model deployments.
  - The original tutorial uses an Azure OpenAI resource. For the updated training version, use a **Microsoft Foundry resource** instead. An existing Azure OpenAI resource can be [upgraded to Microsoft Foundry](https://learn.microsoft.com/en-us/azure/foundry/how-to/upgrade-azure-openai), subject to the documented prerequisites and limitations, without creating a replacement resource.

- **Azure OpenAI with the OpenAI Python SDK** — [Use Azure OpenAI in Fabric with the OpenAI Python SDK](https://learn.microsoft.com/en-us/fabric/data-science/ai-services/how-to-use-openai-python-sdk) — **Practical code guide:** set up a client and run API examples in a Fabric notebook.

[Back to contents](#chapter-contents)

[Back to agenda](./00_Agenda%20with%20Tutorials.md)
