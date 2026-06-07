# Acko-AI-Policy-Chatbot
 An intelligent customer support assistant that answers insurance policy questions instantly — powered by RAG (Retrieval-Augmented Generation) using Google Gemini, ChromaDB, and LangChain.
What It Does
Customers can ask plain-language questions about Acko's insurance policies — motor, health, or travel — and get accurate, jargon-free answers in seconds. The chatbot reads directly from Acko's official policy PDFs, so every answer is grounded in real document content.
Example questions it handles:

"Does my bike insurance cover theft if I forgot to lock it?"
"What is the waiting period for Acko health insurance?"
"What add-ons are available for my car insurance?"
"How do I file a claim?"


How It Works
The system uses a two-phase RAG pipeline:
Offline (one-time setup)

Acko policy PDFs are loaded using LangChain Document Loaders
Documents are split into ~500-character chunks using RecursiveCharacterTextSplitter
Each chunk is converted into a vector using Google Generative AI Embeddings
Vectors are stored and indexed in ChromaDB

Online (every customer query)

Customer types a question in the Streamlit chat interface
The LangChain agent embeds the question and searches ChromaDB for the 3–5 most relevant policy chunks
Those chunks are passed as context to the Gemini API
Gemini generates a clear, friendly answer grounded in the retrieved content
The answer is displayed in the chat and the full Q&A is logged to PostgreSQL


Tech Stack
ComponentToolChat UIStreamlit (st.chat_input, st.chat_message)AI orchestrationLangChain / LangGraphLLMGoogle Gemini API (free tier)Vector storeChromaDBEmbeddingsGoogle Generative AI Embeddings / HuggingFace sentence-transformersPDF loading & chunkingLangChain Document Loaders + RecursiveCharacterTextSplitterConversation loggingPostgreSQL + SQLAlchemy ORM
