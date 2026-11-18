# 12. Customer Use Cases and Proofs of Concept

[Back to agenda](./00_Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [12.1 Identify Building Blocks for a PoC](#121-identify-building-blocks-for-a-poc)
- [12.2 Document Processing and Verification](#122-document-processing-and-verification)
- [12.3 Call and Media Analytics](#123-call-and-media-analytics)
- [12.4 Customer Support with a Data Agent](#124-customer-support-with-a-data-agent)
- [12.5 Real-World Customer Case Studies](#125-real-world-customer-case-studies)
- [12.6 Generative AI and Agent Scenarios](#126-generative-ai-and-agent-scenarios)
- [12.7 Machine Learning Use Cases](#127-machine-learning-use-cases)
- [12.8 Suggested Seminar Focus](#128-suggested-seminar-focus)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. ⭐ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

The links below distinguish real customer case studies, solution ideas, and tutorials with sample data. The example scenarios and tutorials are not complete production solutions; integration, validation, and business-specific rules remain separate work.

## 12.1 Identify Building Blocks for a PoC

- **Customer use cases and PoCs** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/ai-services/ai-services-overview" target="_blank" rel="noopener noreferrer">Use prebuilt Azure AI services (Foundry Tools) in Fabric</a> — **Overview/reference:** identify services that can support a proof of concept.

## 12.2 Document Processing and Verification

- **Tax automation** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/ai-functions/pyspark/extract" target="_blank" rel="noopener noreferrer">Use ai.extract with PySpark in Fabric</a> — **Practical code guide:** use extraction as a building block for tax-document processing.

- **Mortgage application processing** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/create-a-multilingual-search-engine-from-forms" target="_blank" rel="noopener noreferrer">Load forms and extract fields with Document Intelligence in Fabric</a> — **Related tutorial:** form extraction can support an application-processing PoC; the tutorial is not a complete mortgage solution.

- **Invoice and contract verification** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/create-a-multilingual-search-engine-from-forms" target="_blank" rel="noopener noreferrer">Extract data from forms with Document Intelligence in Fabric</a> — **Related tutorial:** form extraction is a starting point; invoice/contract matching and verification require additional work.

## 12.3 Call and Media Analytics

- **Post-call analytics** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/ai-services/how-to-use-text-analytics" target="_blank" rel="noopener noreferrer">Use Azure AI Language text analytics in Fabric with SynapseML</a> — **Practical code guide:** text analytics can be applied to call transcripts after they have been obtained.

- **Media asset management** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/ai-functions/multimodal-overview" target="_blank" rel="noopener noreferrer">Use multimodal input with AI Functions in Fabric</a> — **Practical reference:** multimodal input, including image analysis, as a building block for media workflows.

## 12.4 Customer Support with a Data Agent

- **Enhanced customer support** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/data-agent-end-to-end-tutorial" target="_blank" rel="noopener noreferrer">End-to-end tutorial: Create a Fabric data agent</a> — **Related tutorial:** demonstrates a Data Agent; adapting it for customer support requires scenario-specific data and design.

## 12.5 Real-World Customer Case Studies

- **T-Mobile: AI-assisted customer service** — <a href="https://learn.microsoft.com/en-us/power-platform/guidance/case-studies/tmobile-empowers-customer-service" target="_blank" rel="noopener noreferrer">T-Mobile empowers customer service representatives using Power Apps and Copilot Studio</a> — **Customer case study:** a Power Apps application with a Copilot Studio agent helps staff answer questions about devices and offers. Fabric pipelines load promotional data into Dataverse. This uses a Copilot Studio agent, not a Fabric Data Agent; it complements the customer support scenario in section 12.4.

- **AECOM: project onboarding automation** — <a href="https://learn.microsoft.com/en-us/power-platform/guidance/case-studies/aecom-streamlined-onboarding" target="_blank" rel="noopener noreferrer">AECOM simplifies project onboarding with Power Platform, Azure, and Microsoft Fabric</a> — **Customer case study:** an application coordinates project onboarding and access across multiple systems. Fabric supports data integration and reporting, while Copilot assists development. Additional natural-language Copilot capabilities for end users are described as future plans.

## 12.6 Generative AI and Agent Scenarios

- **Detect spending anomalies** — <a href="https://learn.microsoft.com/en-us/power-platform/architecture/solution-ideas/agent-anomaly-detection" target="_blank" rel="noopener noreferrer">Build anomaly detection with Copilot Studio and Fabric</a> — **Solution idea:** combine Fabric, KQL, a Fabric Data Agent, and Copilot Studio to identify and investigate potential duplicate invoices, unusual vendor activity, and policy violations. This extends the document-verification scenario in section 12.2, but is an architecture starting point rather than a complete hands-on lab.

- **Analyze customer feedback with generative AI** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/tutorial-text-classification" target="_blank" rel="noopener noreferrer">Classify natural language text with generative AI in Microsoft Fabric</a> — **Conceptual guide with practical code examples:** classify free-text survey responses and analyze sentiment using an LLM. Adapting the example's data, placeholders, and pipeline configuration requires additional work. This resource is also listed in [section 3.5](./03_GenAI_based_Report_Commenting.md#35-related-foundry-tools-in-fabric).

## 12.7 Machine Learning Use Cases

These notebook tutorials demonstrate classical machine learning rather than primarily generative AI. They use sample data and require adaptation and validation before production use.

- ⭐ **Predictive maintenance** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/predictive-maintenance" target="_blank" rel="noopener noreferrer">Create, evaluate, and score a machine fault detection model</a> — **Hands-on notebook tutorial:** predict potential equipment failures from factors such as process temperature and rotational speed. The separate <a href="https://learn.microsoft.com/en-us/fabric/real-time-intelligence/architectures/predictive-maintenance" target="_blank" rel="noopener noreferrer">predictive maintenance reference architecture</a> describes a real-time solution; it is not part of the notebook exercise.

- ⭐ **Customer churn** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/customer-churn" target="_blank" rel="noopener noreferrer">Create, evaluate, and score a churn prediction model</a> — **Hands-on notebook tutorial:** predict bank customer churn, evaluate models, and visualize results in Power BI.

- ⭐ **Sales forecasting** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/sales-forecasting" target="_blank" rel="noopener noreferrer">Develop a forecasting model for superstore sales</a> — **Hands-on notebook tutorial:** use historical sales data to forecast future sales by product category.

- ⭐ **Fraud detection** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/fraud-detection" target="_blank" rel="noopener noreferrer">Create, evaluate, and score a fraud detection model</a> — **Hands-on notebook tutorial:** train and evaluate a model for identifying potentially fraudulent credit card transactions.

- ⭐ **Product recommendations** — <a href="https://learn.microsoft.com/en-us/fabric/data-science/retail-recommend-model" target="_blank" rel="noopener noreferrer">Create, evaluate, and score a recommendation system</a> — **Hands-on notebook tutorial:** build a book recommendation model using customer ratings.

Microsoft collects these and additional examples in <a href="https://learn.microsoft.com/en-us/fabric/data-science/use-ai-samples" target="_blank" rel="noopener noreferrer">Use end-to-end AI samples in Microsoft Fabric</a>. Check each tutorial's capacity, workspace, lakehouse, library, permission, and cost requirements before running it. [Chapter 13](./13_General_Fabric_Samples.md) also links to the broader Fabric samples repository.

## 12.8 Suggested Seminar Focus

For the closest fit to the existing AI and agent topics, start with the T-Mobile case study, the spending-anomaly solution idea, and the generative AI feedback example. Predictive maintenance and sales forecasting are useful additions when the seminar also covers classical machine learning. Select examples based on the participants' business needs and available exercise time.

[Back to contents](#chapter-contents)

[Back to agenda](./00_Agenda%20with%20Tutorials.md)
