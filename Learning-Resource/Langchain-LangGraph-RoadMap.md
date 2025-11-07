

### **LangChain Learning Roadmap**

* **1. Foundation: Core Concepts & LCEL**
    * 1.1. Package Structure (The `v0.1` Split)
        * 1.1.1. `langchain-core`
        * 1.1.2. `langchain-community`
        * 1.1.3. `langchain-[partner]` (e.g., `langchain-openai`)
    * 1.2. LangChain Expression Language (LCEL)
        * 1.2.1. The `|` (Pipe) Operator
        * 1.2.2. The `Runnable` Protocol (Interface)
        * 1.2.3. Invocation Methods: `.invoke()`, `.stream()`, `.batch()`
    * 1.3. Core `Runnable` Helpers
        * 1.3.1. `RunnablePassthrough`
        * 1.3.2. `RunnableParallel`
        * 1.3.3. `RunnablePick`

---

* **2. The Building Blocks: Models, Prompts, & Parsers**
    * 2.1. Prompts
        * 2.1.1. `ChatPromptTemplate`
        * 2.1.2. Message Types: `SystemMessage`, `HumanMessage`, `AIMessage`
        * 2.1.3. Input Variables (`{variable}`)
    * 2.2. Models
        * 2.2.1. `ChatModels` (e.g., `ChatOpenAI`)
        * 2.2.2. `LLMs` (Legacy)
        * 2.2.3. `Embedding Models`
    * 2.3. Output Parsers
        * 2.3.1. `StrOutputParser`
        * 2.3.2. `JsonOutputParser`
        * 2.3.3. `PydanticOutputParser`

---

* **3. The #1 Use Case: Retrieval-Augmented Generation (RAG)**
    * 3.1. Data Ingestion (The Pipeline)
        * 3.1.1. `DocumentLoaders` (Web, PDF, TXT)
        * 3.1.2. `TextSplitters` (`RecursiveCharacterTextSplitter`)
        * 3.1.3. Vector Store Initialization (Chroma, FAISS)
    * 3.2. Retrieval
        * 3.2.1. The `Retriever` Interface
        * 3.2.2. Search Types: Similarity vs. MMR
        * 3.2.3. Creating a `VectorStoreRetriever`
    * 3.3. RAG Chains
        * 3.3.1. The "Stuff" Chain (Basic RAG)
        * 3.3.2. LCEL Pattern: Passing Context and Question
        * 3.3.3. Advanced RAG: `create_history_aware_retriever`

---

* **4. Agents: Giving LLMs Tools**
    * 4.1. Agent Concepts
        * 4.1.1. **Tools:** `@tool` decorator
        * 4.1.2. **ReAct:** The Reason/Act framework
        * 4.1.3. `AgentExecutor`: The runtime loop
    * 4.2. Building with Modern Tool-Calling
        * 4.2.1. Using Tool-Calling Models (OpenAI, Anthropic, Gemini)
        * 4.2.2. `create_openai_tools_agent` (or equivalent)
        * 4.2.3. Agent State and Intermediate Steps
    * 4.3. Using Pre-built Tools
        * 4.3.1. `DuckDuckGoSearchRun`
        * 4.3.2. `TavilySearchAPIRetriever`
        * 4.3.3. Toolkits (e.g., CSV, SQL)

---

* **5. Advanced Topics**
    * 5.1. Memory (Conversation)
        * 5.1.1. `ChatMessageHistory`
        * 5.1.2. `RunnableWithMessageHistory` (The LCEL way)
        * 5.1.3. Memory Types (Buffer, Window, Summary)
    * 5.2. Observability (Debugging)
        * 5.2.1. **LangSmith** Setup
        * 5.2.2. Reading a Trace
        * 5.2.3. Logging with `.stream_log()`
    * 5.3. Next Steps: LangGraph
        * 5.3.1. State Machines (Graphs)
        * 5.3.2. Nodes and Edges
        * 5.3.3. Building Cyclic (Looping) Agents

---

# LangGraph


### **LangGraph Learning Roadmap**

* **1. Foundation: Core LangGraph Concepts**
    * 1.1. The Core Idea: Beyond Chains
        * 1.1.1. LangChain (LCEL) as a DAG (Directed Acyclic Graph)
        * 1.1.2. LangGraph for Cycles (Loops) and State
        * 1.1.3. Use Case: Building Agents, Not Chains
    * 1.2. The State Machine Abstraction
        * 1.2.1. `State`: The "memory" or "scratchpad" of the graph
        * 1.2.2. `Nodes`: The "workers" that modify state
        * 1.2.3. `Edges`: The "paths" that direct the flow of state
    * 1.3. Graph Types
        * 1.3.1. `Graph` (The general-purpose state machine)
        * 1.3.2. `MessageGraph` (A pre-built graph for chat applications)

---

* **2. Building a Basic Graph**
    * 2.1. Defining State
        * 2.1.1. Using `TypedDict` for state structure
        * 2.1.2. `Annotated` for managing state updates (e.g., `add_messages`)
    * 2.2. Defining Nodes
        * 2.2.1. Creating nodes as simple Python functions
        * 2.2.2. A node's role: Takes state, performs work, returns update
    * 2.3. Constructing the Graph
        * 2.3.1. `add_node(name, function)`
        * 2.3.2. `set_entry_point(name)`
        * 2.3.3. `set_finish_point(name)`
    * 2.4. Defining Edges (Linear Flow)
        * 2.4.1. `add_edge(start_node, end_node)`
        * 2.4.2. `START` and `END` keywords
    * 2.5. Compiling and Running
        * 2.5.1. `compile()`: Creating the `Runnable` graph
        * 2.5.2. `invoke()`: Running the graph
        * 2.5.3. `stream()`: Visualizing the steps

---

* **3. Advanced Graphs: Agents & Control Flow**
    * 3.1. Conditional Edges (Branching)
        * 3.1.1. Creating a "router" node (a function that returns a string)
        * 3.1.2. `add_conditional_edges(source_node, router_function, path_map)`
        * 3.1.3. Use Case: Agent deciding "use tool" vs. "answer user"
    * 3.2. Cycles (Loops)
        * 3.2.1. Implementing loops by adding an edge back to a previous node
        * 3.2.2. Building the "ReAct" Agent Loop (Reason -> Act -> Observe -> Reason...)
    * 3.3. Persistence & State Management (Memory)
        * 3.3.1. `Checkpointers` (e.g., `SqliteSaver`, `MemorySaver`)
        * 3.3.2. Compiling with a checkpointer
        * 3.3.3. Using `configurable={"thread_id": ...}` to manage conversations
    * 3.4. Human-in-the-Loop
        * 3.4.1. Interrupting a graph with `interrupt_before`
        * 3.4.2. Resuming a graph using `.update_state()` and `.invoke()`
    * 3.5. Debugging and Visualization
        * 3.5.1. Using LangSmith (Essential for graphs)
        * 3.5.2. `get_graph().print_ascii()`
