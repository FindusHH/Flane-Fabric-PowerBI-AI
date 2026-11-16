# 7. Fabric Data Agents

[Back to agenda](./Agenda%20with%20Tutorials.md)

<a id="chapter-contents"></a>

**Contents**

- [7.1 Data Agent Concepts and Setup](#71-data-agent-concepts-and-setup)
- [7.2 Hands-on Data Agent Scenarios](#72-hands-on-data-agent-scenarios)
- [7.3 Ground a Data Agent in an Ontology](#73-ground-a-data-agent-in-an-ontology)
- [7.4 Integrate Data Agents with Copilot Studio and Foundry](#74-integrate-data-agents-with-copilot-studio-and-foundry)
- [7.5 Related Path: Connect AI Agents to Fabric through MCP](#75-related-path-connect-ai-agents-to-fabric-through-mcp)

**Link guide:** **Hands-on tutorial** means a guided, step-by-step exercise. 🛠️ marks hands-on tutorials, labs, and quickstarts, but not overview pages or code example collections. **Practical code guide** means examples to run in a notebook or SQL editor. **Overview/reference** explains concepts, features, or architecture but is not a complete exercise to follow.

**Teaching note:** Learn the agent basics, then select a lakehouse or warehouse exercise. Ontology grounding and external integrations are separate paths; the GraphQL MCP guide connects AI agents to Fabric but does not configure a Fabric Data Agent.

## 7.1 Data Agent Concepts and Setup

- **Data Agent concepts and fundamentals** — [What is a Fabric data agent?](https://learn.microsoft.com/fabric/data-science/concept-data-agent) — **Overview/reference:** introduces Fabric Data Agent concepts and capabilities.

- **Fabric Data Agents** — [Create a Fabric data agent](https://learn.microsoft.com/fabric/data-science/how-to-create-data-agent) — **Step-by-step how-to:** create an agent, add data sources, select tables, and configure it. Requires paid Fabric capacity and accessible data.

## 7.2 Hands-on Data Agent Scenarios

- 🛠️ **Fabric Data Agent with AdventureWorks** — [Data agent example with the AdventureWorks dataset](https://learn.microsoft.com/fabric/data-science/data-agent-end-to-end-tutorial) — **Hands-on tutorial (preview):** populate a lakehouse with sample data, create an agent, and ask questions. Requires paid Fabric capacity and appropriate tenant settings.

- 🛠️ **Chat with sales data using a Fabric Data Agent** — [Chat with your data using Microsoft Fabric data agents](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/22d-copilot-fabric-data-agents.html) — **Hands-on lab (approximately 30 minutes):** create a sales warehouse and configure a data agent, then ask plain English questions and inspect how they are translated into SQL queries. Requires paid Fabric capacity; trial capacity is not supported.

## 7.3 Ground a Data Agent in an Ontology

- **Connect a Data Agent to an ontology** — [Create a data agent grounded in an ontology](https://learn.microsoft.com/fabric/iq/ontology/how-to-create-data-agent) — **Step-by-step how-to (preview):** add an ontology as a data source and ask questions in natural language. Currently, ontologies bound to semantic models are not supported by this integration.

- 🛠️ **Build a healthcare Data Agent with an ontology** — [Build a Fabric data agent with an ontology](https://microsoftlearning.github.io/mslearn-fabric/Instructions/Labs/28-build-data-agent-ontology.html) — **Hands-on lab (preview, approximately 30 minutes):** create the Lamna Healthcare ontology with a setup notebook, configure agent instructions, test natural language questions, and publish and share the agent. Requires paid Fabric capacity and appropriate tenant settings; trial capacity is not supported. Uses the older ontology experience, scheduled to retire on January 31, 2027; it is not a direct continuation of lab 24.

## 7.4 Integrate Data Agents with Copilot Studio and Foundry

- **Use a Data Agent in Copilot Studio** — [Consume a Fabric data agent in Microsoft Copilot Studio](https://learn.microsoft.com/fabric/data-science/data-agent-microsoft-copilot-studio) — **Integration guide:** consume a Fabric Data Agent from Copilot Studio.

- **Add a Data Agent as a Copilot Studio tool** — [Add a Fabric data agent as a tool in Microsoft Copilot Studio](https://learn.microsoft.com/fabric/data-science/data-agent-microsoft-copilot-studio-tool) — **Integration guide:** configure a Fabric Data Agent as a tool in Copilot Studio.

- **Use a Data Agent with Microsoft Foundry** — [Consume Fabric data agent from Microsoft Foundry Services](https://learn.microsoft.com/fabric/data-science/data-agent-foundry) · [Fabric data agent as a tool in the Foundry Agent Service](https://learn.microsoft.com/azure/foundry/agents/how-to/tools/fabric) — **Integration guides:** use Fabric Data Agents from Foundry and as an agent tool.

## 7.5 Related Path: Connect AI Agents to Fabric through MCP

- **Connect AI agents to Fabric through MCP** — [Connect AI Agents to Fabric API for GraphQL with a local MCP server](https://learn.microsoft.com/fabric/data-engineering/api-graphql-local-model-context-protocol) — **Integration guide:** connect an AI agent to a Fabric GraphQL API using a local MCP server; this is separate from the Fabric Data Agent integrations above.

[Back to contents](#chapter-contents)

[Back to agenda](./Agenda%20with%20Tutorials.md)
