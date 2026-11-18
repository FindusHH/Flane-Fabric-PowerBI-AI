# Addendum 2 to Build RAG in Fabric

This addendum evaluates Microsoft's preview guide, <a href="https://learn.microsoft.com/en-us/fabric/data-science/data-agent-ai-search-index" target="_blank" rel="noopener noreferrer">Connect Data Agents to your Azure Search Index in Microsoft Foundry</a>, alongside the earlier <a href="https://learn.microsoft.com/en-us/fabric/data-science/quickstart-building-retrieval-augmented-generation" target="_blank" rel="noopener noreferrer">Build retrieval-augmented generation in Microsoft Fabric</a> notebook tutorial. It explains what is new, what to verify before reusing the notebook's Search index, and where this integration fits in the seminar.

## What is new?

The earlier RAG notebook builds a retrieval pipeline: it prepares and chunks text, creates embeddings, writes them to an Azure AI Search index, retrieves relevant content, and generates an answer. The new guide describes a different consumption path: connect an existing Azure AI Search index to a Fabric Data Agent, which can use the indexed content when answering questions and can be configured alongside supported Fabric data sources.

This is a new Data Agent integration scenario, not simply another way to run the notebook. The guide is a short integration how-to rather than an end-to-end lab: it assumes that the Search service and index already exist. It does not promise a literal SQL-style join between unstructured indexed content and structured Fabric data.

The guide recommends configuring how the index is searched, providing context and agent instructions, and limiting the number of documents returned; it recommends 3–20 documents. Treat this as guidance, not a documented hard limit. Available search modes depend on the index configuration.

## Authentication and tenant boundaries

The new integration uses the requesting user's identity and Azure AI Search role-based access control (RBAC), rather than the API key used by the earlier notebook. Do not apply the earlier notebook's API-key conclusion to this identity-based connection.

The guide lists both **Search Index Data Reader** and **Search Index Data Contributor**. Microsoft documents that the Contributor role can query and modify indexed documents, while Reader is read-only. The guide does not establish that Reader alone is sufficient for this integration. Confirm the required role with a least-privilege test before a workshop or deployment.

Microsoft's documentation does not clearly establish whether this specific Data Agent-to-Search connection supports a Search service in a different tenant. Do not assume either that a shared tenant is mandatory or that cross-tenant access is supported. Verify sign-in, token, guest identity, role assignment, and network requirements in the target environment.

This is distinct from a Foundry agent calling a Fabric Data Agent. Microsoft's current Fabric IQ integration guide says the Foundry agent and Fabric Data Agent must be in the same tenant, with the same account used to sign in to Fabric and Foundry. That requirement applies to that Foundry-to-Fabric flow; it does not answer the tenant question for the Search index connection.

References: <a href="https://learn.microsoft.com/en-us/azure/search/search-security-rbac" target="_blank" rel="noopener noreferrer">Role-based access control for Azure AI Search</a> · <a href="https://learn.microsoft.com/en-us/fabric/data-science/data-agent-sharing" target="_blank" rel="noopener noreferrer">Sharing and permissions for Fabric Data Agents</a> · <a href="https://learn.microsoft.com/en-us/fabric/data-science/data-agent-foundry-fabric-iq" target="_blank" rel="noopener noreferrer">Add Fabric Data Agents to a Foundry agent with Fabric IQ</a>.

## Reusing the index from the RAG notebook

The index created by the earlier notebook may be a useful starting point, but compatibility is not guaranteed. Check its schema, authentication mode, network access, and search configuration before connecting it to a Data Agent.

### Source citations need a recognized field

The Data Agent guide says that citations are displayed only when the index includes at least one of these case-sensitive field names: `url`, `sourceUrl`, `filePath`, `path`, or `folderPath`.

The earlier notebook's example index uses fields such as `ArticleTitle`, `ExtractedPath`, `Chunk`, and `Embedding`. `ExtractedPath` is not one of the documented citation field names. To test displayed citations with that index, add and populate a recognized field with a useful source URL or path. Seeing documents in the agent's reasoning steps is not the same as seeing citations in its answer.

### Embeddings and hybrid search

The notebook generates embeddings in Python and defines a vector field. The Data Agent guide does not fully explain how it constructs a query vector for every hybrid-search configuration. Azure AI Search can use a configured vectorizer to convert query text to vectors, but the guide does not say that a vectorizer is mandatory for every supported Data Agent search mode.

Check whether the chosen search mode is compatible with the index and its vector configuration. When vector search is used, query and document embeddings must come from compatible embedding models; matching vector dimensions alone is not sufficient.

References: <a href="https://learn.microsoft.com/en-us/azure/search/hybrid-search-overview" target="_blank" rel="noopener noreferrer">Hybrid search in Azure AI Search</a> · <a href="https://learn.microsoft.com/en-us/azure/search/vector-search-how-to-configure-vectorizer" target="_blank" rel="noopener noreferrer">Configure a vectorizer in a search index</a>.

## Security and networking considerations

- **Search RBAC is not document-level authorization.** Passing the user's identity and assigning Search roles does not by itself prove that permissions from the original document repository are enforced for each result. Design and test document-level access controls separately, including with users who have different source permissions. See <a href="https://learn.microsoft.com/en-us/azure/search/search-document-level-access-overview" target="_blank" rel="noopener noreferrer">Document-level access control in Azure AI Search</a>.
- **Do not assume the notebook's network path applies to the Data Agent.** The notebook sends requests from its Spark environment; the native Data Agent connection is a separate access path. A working notebook or managed private endpoint does not demonstrate that the Data Agent can reach the same Search service.
- **Check workspace outbound access protection before enabling it.** Microsoft documents that the Data Agent makes outbound requests when it adds or queries an Azure AI Search source, and currently lists Azure AI Search as unsupported by workspace outbound access protection. Do not assume that an allow-list rule will enable this connection under that protection; test the intended security configuration. See <a href="https://learn.microsoft.com/en-us/fabric/security/workspace-outbound-access-protection-data-agent" target="_blank" rel="noopener noreferrer">Workspace outbound access protection for Data Agent</a>.
- **An API-key-only notebook may stop working after an RBAC change.** If the Search service is changed to RBAC-only, the earlier notebook's unchanged API-key requests will no longer authenticate. Azure AI Search supports a temporary **Both** mode during some migrations, but use it only if permitted by your security policy. See <a href="https://learn.microsoft.com/en-us/azure/search/search-security-enable-roles" target="_blank" rel="noopener noreferrer">Enable role-based access for Azure AI Search</a>.

## Prerequisites and documentation caveats

- The guide lists paid Fabric capacity **F2 or higher**, or **P1 or higher** with Fabric enabled. The earlier RAG notebook separately lists **F64**. Do not infer that F2 is sufficient for the complete notebook-based RAG exercise; verify the capacity requirement for each part of the workshop.
- The guide also lists a populated Fabric data source, such as a lakehouse or semantic model. The documentation does not clearly resolve whether every index-only agent scenario requires an additional structured source. For a workshop, prepare one rather than relying on an index-only setup.
- Fabric Data Agent requirements include tenant and regional settings for AI features. Review the current <a href="https://learn.microsoft.com/en-us/fabric/data-science/data-agent-tenant-settings" target="_blank" rel="noopener noreferrer">Fabric Data Agent tenant settings</a> before the session.
- The Data Agent guide is marked **preview**. Test the complete workflow in the actual training tenant and do not treat the integration as a production guarantee.
- The general <a href="https://learn.microsoft.com/en-us/fabric/data-science/concept-data-agent#limitations" target="_blank" rel="noopener noreferrer">Data Agent concepts and limitations</a> page says that the agent does not directly support unstructured files such as PDF, DOCX, or TXT. The Search integration is a separate route through content already prepared and indexed in Azure AI Search; it is not direct file ingestion by the Data Agent. The documentation is not fully aligned, so verify current behavior.
- The general limitations page also says that non-English languages are not currently supported and recommends English questions, instructions, and examples. Plan to run the exercise in English.

## Related Foundry integration: an important update

Do not confuse connecting a Search index to a Fabric Data Agent with connecting a Fabric Data Agent to a Foundry agent. The latter is a separate, opposite-direction integration.

Microsoft's older Foundry integration documentation states that the Fabric Data Agent tool in Foundry is no longer supported starting **November 6, 2026** and directs users to the Fabric IQ (OneLake Catalog) tool. Since that date has passed, use the current Fabric IQ guide for new Foundry-to-Fabric setups:

- <a href="https://learn.microsoft.com/en-us/fabric/data-science/data-agent-foundry" target="_blank" rel="noopener noreferrer">Older Fabric Data Agent integration with Microsoft Foundry</a>
- <a href="https://learn.microsoft.com/en-us/fabric/data-science/data-agent-foundry-fabric-iq" target="_blank" rel="noopener noreferrer">Current Fabric IQ integration guide</a>
- <a href="https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/tools/fabric" target="_blank" rel="noopener noreferrer">Use the Microsoft Fabric data agent tool in Foundry</a>

## Seminar recommendation

The Search-index guide adds a useful Data Agent scenario: answer questions over already indexed document content, optionally alongside supported Fabric sources. Its best primary location is **Chapter 6, Fabric Data Agents**, with a cross-reference from **Chapter 11, RAG**, where the notebook-based index creation is covered. It is not primarily a Semantic Link topic for Chapter 8.

For a practical exercise, create and validate the index first, then connect it to the Data Agent. Include checks for RBAC, citation field names, search mode and vector compatibility, network access, and the behavior of users with different permissions. Because the feature is in preview and the guide assumes a prepared index, describe it as an integration exercise rather than a self-contained lab.

Related seminar materials: [Chapter 6: Fabric Data Agents](./06_Fabric_Data_Agents.md) · [Chapter 11: Retrieval-Augmented Generation](./11_Retrieval_Augmented_Generation_RAG.md) · [First RAG addendum](./Addendum%20to%20Build%20RAG%20in%20Fabric.md).
