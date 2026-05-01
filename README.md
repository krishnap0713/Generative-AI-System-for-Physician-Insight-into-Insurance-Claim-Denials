This project presents a Generative AI-powered system designed to help physicians understand insurance claim denials through plain-language explanations, structured summaries, and actionable next steps.

The system combines:

Large Language Models (LLMs)
Retrieval-Augmented Generation (RAG)
Agentic AI with tool integration

# 🧠 Generative AI System for Insurance Claim Denial Analysis  

## 📌 Overview  
This project is a **Generative AI + RAG + Agent-based system** designed to analyze healthcare insurance claim denials using both:  

- Unstructured claim documents (text files)  
- Structured claims dataset (Excel)  

The system enables **natural language querying** to retrieve denial explanations, summarize claims, and compute financial insights.

---

## 🔍 Unstructured Claims (Text Files) – RAG Pipeline  

- Loaded multiple `.txt` denied claim documents  
- Applied **RecursiveCharacterTextSplitter** for chunking large text  
- Generated embeddings using **HuggingFaceEmbeddings** (`sentence-transformers/all-mpnet-base-v2`)  
- Stored embeddings as vectors in **FAISS vector database**  
- Created a retriever using:  
  `vectorstore.as_retriever()` for similarity-based search  

### Prompt Engineering  
- Designed **PromptTemplate** to:  
  - Extract claim by Claim ID  
  - Generate denial reason  
  - Summarize claim details  
  - Suggest next steps  

### LLM Integration  
- Used **ChatOpenAI (GPT-3.5 Turbo via OpenAI API)**  
- Controlled outputs using:  
  - Low temperature (`0.1`)  
  - Structured prompting  

---

## 📊 Structured Claims Dataset (Excel) – Tool-Based Querying  

- Loaded `.xlsx` dataset using **pandas**  

### Data Processing  
- Cleaned and processed data using:  
  - `to_numeric()`  
  - `dropna()`  

### Custom Computation Functions  
- Created functions for:  
  - Min / Max `Payment_Amount`  
  - Payer with highest / lowest payment (`idxmax()`, `idxmin()`)  
  - Retrieval of claim-level attributes:  
    - Payer  
    - CPT codes  
    - ICD codes  
    - Denial reason  
    - Documentation notes  

### Tool Integration  
- Converted functions into tools using **LangChain `@tool` decorator**  
- Ensured accurate numerical computation outside the LLM  

---

## 🤖 Agentic Workflow (LangChain + LangGraph)  

- Built agent using `create_react_agent` (LangGraph)  

### Integrated Components  
- Retriever (for unstructured text)  
- Tools (for structured data)  

### Agent Capabilities  
- Dynamically decides:  
  - When to call retriever  
  - When to invoke tool  
- Supports natural language queries like:  
  - “Why was this claim denied?”  
  - “Which payer paid the most?”  
  - “What is the max payment amount?”  

---

## ⚙️ Core Tech Stack  

- **OpenAI API** → ChatOpenAI (GPT-3.5 Turbo)  
- **LangChain** → PromptTemplate, tool decorator, chains  
- **LangGraph** → Agent creation and reasoning workflow  
- **FAISS** → Vector storage and similarity-based retrieval  
- **Hugging Face** → Embeddings model  
- **Python (pandas)** → Data processing and tool functions  

---

## 🧠 Key System Design  

- Combined:  
  - Embeddings + vectors + retriever (RAG)  
  - PromptTemplate-driven LLM responses  
  - Tool-based deterministic computation  

- Reduced reliance on raw LLM reasoning for structured queries  
- Built hybrid pipeline:  
  **LLM + Retrieval + Programmatic Tools**

---

## 📌 Features  

- Claim-level retrieval using Claim ID  
- Denial explanation in plain language  
- Structured dataset querying  
- Accurate computation using Python tools  
- Agent-based dynamic reasoning  

---

## ⚠️ Limitations  

- Uses synthetic datasets  
- Not production-scaled  
- Local execution (API key-based)  

---

## 🚀 Future Improvements  

- Integration with real-world claims datasets  
- Scalable RAG pipeline (metadata filtering)  
- Expanded analytics (denial trends, payer insights)  
- Cloud deployment (AWS / Databricks)  

---

## 👩‍💻 Author  

**Krishna Parekh**  
Master’s in Health Informatics  
Rutgers School of Health Professions  
