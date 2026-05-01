This project presents a Generative AI-powered system designed to help physicians understand insurance claim denials through plain-language explanations, structured summaries, and actionable next steps.

The system combines:

Large Language Models (LLMs)
Retrieval-Augmented Generation (RAG)
Agentic AI with tool integration

to bridge the gap between complex healthcare claim data and clinical decision-making.

🚀 Key Features

🔍 Retrieve claim-specific information using Claim ID

🧾 Generate:
Denial reason (plain language)
Claim summary

Recommended next steps

📊 Perform accurate numerical analysis using custom tools

🤖 Agent automatically selects tools based on query intent

⚡ Eliminates LLM hallucination in calculations using Python functions

🏗️ System Architecture
1. Retrieval-Augmented Generation (RAG)
Uses FAISS vector database for efficient similarity search
Embeds text chunks using HuggingFace embeddings
Retrieves relevant claim documents before LLM response generation
2. Agentic AI (LangGraph / LangChain)
Reactive agent decides:
When to use LLM
When to call tools
Enables hybrid reasoning (LLM + deterministic computation)
3. Tool Integration

Custom tools handle structured queries like:

Min / Max Payment Amount
Highest / Lowest payer
Data validation checks

📂 Datasets

🔹 Unstructured Data
Denied claim .txt files
Includes:
Claim ID
CPT / ICD codes
Denial reason
Payment details

🔹 Structured Data
Excel dataset (.xlsx)
Columns include:
Payment_Amount
Payer
Claim ID
Appeal status
Documentation notes

🛠️ Tech Stack & Python Skills

🔹 Core Libraries
LangChain
Prompt engineering (PromptTemplate)
Chains and pipelines
LangGraph
Reactive agent (create_react_agent)
OpenAI
ChatOpenAI (GPT-3.5 Turbo)

🔹 Vector Database
FAISS
FAISS.from_documents()
Vector similarity search

🔹 Embeddings
HuggingFaceEmbeddings
sentence-transformers/all-mpnet-base-v2

🔹 Text Processing
RecursiveCharacterTextSplitter
Chunking large documents
Overlap handling for context preservation

🔹 Data Handling
pandas
Data cleaning (to_numeric, dropna)
Aggregations (min(), max())
Index-based queries (idxmax(), idxmin())

🔹 OS & File Handling
os module for file management

🔄 Workflow
User inputs query (e.g., Claim ID or question)
System:
Retrieves relevant documents (RAG)
Injects into prompt template
LLM generates:
Denial explanation
Summary
Next steps
If query is numerical:
Agent calls appropriate Python tool
Final response returned in natural language

📈 Results & Impact
✅ Accurate claim retrieval and summarization
✅ Reliable tool-based numerical outputs
✅ Reduced hallucination in calculations
✅ Improved interpretability for physicians
✅ Faster decision-making

📌 AI systems like this can reduce denial rates by 15–40% and improve workflow efficiency

👩‍💻 Author

Krishna Parekh

Master’s in Health Informatics

Rutgers School of Health Professions
