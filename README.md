LLMs are usually trained for a finite time-period on a (vast but) finite quantity of data. Oftentimes, the LLMs may not have access to the most up-to-date data or even data that is private to an organization. In such situations, to allow the LLM to answer the user’s query without hallucinations, a RAG (Retrieval Augmented Generation) approach is chosen. 
Here the data is first chunked and then converted into vectors [aka embeddings]. When the user’s query comes in, it is also converted into a vector and then compared against the existing vectors as part of a semantic similarity search operation (example: using cosine similarity).
The relevant document chunks that correspond to the vectors that match the user’s query are returned to the user after converting the embeddings to natural language. 
Traditional RAG (also called Vector RAG) involves the use of two models - one to convert the data to embeddings and the other to interface with the user in natural language
However, if the user’s query requires nuanced analysis of the hierarchical relationships between different entities in the data and/or if the data itself is spread across multiple documents and modalities, merely performing a semantic similarity search operation to return the top-k search results, will not yield the answer that the user’s query requires. 
Cue in - a graph data-structure [also called a Knowledge Graph] that allows for capturing and representing the entities in the dataset along with their relationships. The entities form the nodes of the graph and their relationship forms the paths connecting different nodes.
 This approach that adds on a graph data structure to the traditional RAG is called a GraphRAG. Using a GraphRAG allows the LLM to traverse the relevant graph paths to connect seemingly random facts into a logical sequence that provides the necessary causal analysis required to answer the user’s queries.  


For example:
If a user searches an e-commerce site for an electric tooth-brush,then using only Vector RAG would allow the site to list the top-k most popular electric tooth-brushes on the site. 
However, if a Knowledge Graph is defined such that an electric tooth-brush (entity) is vital to (relationship) oral hygiene (another entity), then it is possible to design a recommendation system that could potentially list other entities (such as a water-based flosser  - for instance) that also shares a relationship to the entity ‘oral hygiene’.1

Advantages of GraphRAGs:

Using a Knowledge Graph allows the model to ‘connect the dots’ between entities defined across multiple documents. 
GraphRAGs help the LLM answer queries that require understanding the entirety of the corpus of data to arrive at the underlying big-picture theme(s)/summaries or in accurately performing causal analysis that needs to examine multiple levels of hierarchical relationships between the entities in the data.
Since the relationships between the entities in the dataset are explicitly defined in a Knowledge Graph, the model can provide the exact path it took to arrive at a solution to the user’s query, making this solution an example of Explainable AI. This in turn, serves to increase trust in the use of such an AI solution, which could directly increase the adoption of AI tools in sectors governed by strict laws/regulations pertaining to the use of AI (or) where the users may not otherwise be inclined to use AI.

Disadvantages of GraphRAGs:


Just as with any other approach used to train a LLM, garbage in equals garbage out. So it is important to prioritize the process of defining the entities and their relationships in the ontology of the Knowledge Graph and this requires a lot of human expertise/oversight especially for data that is very specific to a domain
In turn, the additional preprocessing tasks add to both time and cost in creating the GraphRAG solution as the LLM would need to be trained with both positive and negative graph traversal paths to build up the expertise required to correctly answer the user’s queries.
The query latency ends up being at a higher order of magnitude compared to Vector RAG as both graph traversal and semantic similarity search operations need to complete successfully for the user’s query to be answered, so GraphRAGs may not be suited for low latency use-cases.

GraphRAGs work best for complex domain specific queries (such as in the medical/legal/financial sectors)  that rely on multi-hop reasoning where the nuanced/hierarchical relationships between entities in the data is as important as the individual entities themselves and where the AI needs to be Explainable to foster trust and usage.


References:

[Build your first GraphRAG Powered Agent! (No Graph Expert Required) | Databases for AI](https://www.youtube.com/live/gv6zK265OUE?si=5wNNh55sCmoOZUGr)
[Project GraphRAG - Microsoft Research](https://www.microsoft.com/en-us/research/project/graphrag/)
[GitHub - microsoft/graphrag: A modular graph-based Retrieval-Augmented Generation (RAG) system](https://github.com/microsoft/graphrag)
[Benchmarking Vector, Graph and Hybrid Retrieval Augmented Generation (RAG) Pipelines for Open Radio Access Networks (ORAN)]([url](https://arxiv.org/html/2507.03608v1))
[VectorRAG vs GraphRAG: March 2025 Technical Challenges](https://www.falkordb.com/blog/vectorrag-vs-graphrag-technical-challenges-enterprise-ai-march25/)












