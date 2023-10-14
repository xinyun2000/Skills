## Core Concept

LLaMAIndex helps to build application based on personal or private data driven by LLM. 

**RAG(Retrieval Augmented Generation)** is the core concept for LLaMAIndex.

### RAG

RAG, also called **Search Generation Enhancement.** It is a paradigm for enhancing LLM with personal or private data.

RAG contains two section:

1. Index(索引)

   help users to build the knowledge base

2. Query(查询)

   query the in-context information from the knowledge base, help LLM to answer the questions. 

LLaMAIndex provides various tools to help users finish these two section conveniently.



### Index Section

LLaMAIndex helps users build the knowledge base by providing Data connection(数据连接器) and indexes(索引) 

the tools or plugin which will be used in this section:

#### Data connection

- data connection will get those personal or private data from different places and switch them to the documents(文档表现形式) supported by LLaMAIndex

#### Document/Nodes

- document is the concept of a **container** in LLaMAIndex. It **can contain any data source**, such as database, txt or APIs. 
- the smallest part of documents is called **Nodes**, which represent the **chunk(分块)**of the document. Node also **contains** the **metadata(元数据) and the relationships** between other nodes or APIs.

![1697189723784](C:\Users\QUAN\Documents\WeChat Files\wxid_huobapv11fgp21\FileStorage\Temp\1697189723784.png)
#### Data Indexes

- convenient tool provided by LLaMAIndex, help users to build indexes for knowledge base. let the index become easy and efficient.

- usually use index: ***VectorStoreIndex*** 



### Query Section

- During the query section, the RAG pipeline **find the most relevant context** based on the user query and **passes it along with the query to LLM** to synthesize a response. 
- This enables LLM to obtain up-to-date knowledge that was not in its original training data, while also reducing fake content. The **key challenges** in this section are **finding, arranging and reasoning** based on the knowledge base.

![f355aec24b9a0cf80e6b11eaca4d965](C:\Users\QUAN\Documents\WeChat Files\wxid_huobapv11fgp21\FileStorage\Temp\f355aec24b9a0cf80e6b11eaca4d965.jpg)

- LLaMAIndex provide **composable(可组合的) module** to help users **build and integrated(集成) RAG pipeline** to use as an chatbot or a part of agent.
- these module can be customized by ranking preference and be mixed up to reason in the structured mode. 

#### module in this section:

1. Retrievers

   > 检索器。Define how to efficiently retrieve relevant contextual information from the knowledge base based on queries

2. Node Postprocessors

   > 节点后处理器。 It performs transformation, filtering, or ranking on a series of document nodes (Node).

3. Response Synthesizers

   > 响应合成器。 It leverages LLM to generate a response based on the user's query, and a set of retrieved text chunks (forming the context).
   >
   > always be used in chat

不同管道但构建器是相似的，都会基于检索器来检索知识库中的内容数据得到文本分块，也就是相关的上下文，然后基于节点和后处理器对数据对文本进行过滤转换排名，并由大语言模型来生成合成响应，再将响应供给给不同的管道。

#### RAG pipeline:

1. Query Engines

   > end-to-end
   >
   > Allow users ask the question by using natural language, which can get the answer and relevant context.

2. Chat Engines

   > end-to-end
   >
   > allow user to chat based on knowledge base.

3. Agents

   > It is an automated decision maker（自动化决策器） powered by LLM. 
   >
   > Agents can be used as query engines or chat engines. 
   >
   > The main difference is that the agent dynamically decides on the best sequence of actions rather than following a predetermined logic(预定的逻辑). This gives it additional flexibility to handle more complex tasks.

不同管道但构建器是相似的，都会基于检索器来检索知识库中的内容数据得到文本分块，也就是相关的上下文，然后基于节点和后处理器对数据对文本进行过滤转换排名，并由大语言模型来生成合成响应，再将响应供给给不同的管道。

![02_2.png](https://github.com/sugarforever/LlamaIndex-Tutorials/blob/main/02_Core_Concepts/02_2.png?raw=true)
