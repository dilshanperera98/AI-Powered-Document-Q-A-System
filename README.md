# AI-Powered-Document-Q-A-System
This project enables users to upload PDF documents and ask questions based on their content. Using LLMs and vector embeddings, the system retrieves relevant document sections and generates context-aware responses.

Technologies Used:
Hugging Face (Mistral-7B) – LLM for text generation
LangChain – Framework for building LLM applications
ChromaDB – Vector database for efficient document retrieval
Sentence-Transformers (all-mpnet-base-v2) – Text embedding model
PyPDFLoader – PDF text extraction
RecursiveCharacterTextSplitter – Splitting documents into manageable chunks

I'm setting up a local LLM-based retrieval-augmented generation (RAG) pipeline using Hugging Face models without relying on OpenAI's API. Here's a breakdown of what I'm doing:

Overview of My Approach
I'm using Hugging Face’s Mistral-7B as an LLM and MPNet (sentence-transformers/all-mpnet-base-v2) for embedding-based retrieval. The main goal is to extract relevant information from a PDF file and use it to answer user queries.

Detailed Breakdown of the Process
1. Installing Required Libraries
I'm installing essential libraries like:

torch (for deep learning computations)
transformers (for loading LLM models from Hugging Face)
numpy (for numerical computations)
langchain & langchain_community (for LLM chaining and integration)
langchain-chroma (for vector-based retrieval)
sentence_transformers (for embeddings)
pypdf (for extracting text from PDFs)
2. Initializing the Hugging Face LLM
I'm using Mistral-7B from Hugging Face via HuggingFaceHub().
Instead of OpenAI API keys, I'm using Google Colab's userdata.get() to securely retrieve my Hugging Face API token.
3. Creating Embeddings for Document Retrieval
I'm using MPNet-based sentence transformer embeddings to encode the PDF document content into vector representations.
This helps in efficiently searching for relevant chunks of text.
4. Loading and Splitting the PDF Document
I'm using PyPDFLoader() to extract text from a PDF file.
Then, with RecursiveCharacterTextSplitter(), I'm breaking the document into smaller text chunks (400 characters per chunk with a 50-character overlap).
5. Creating a Vector Store (Chroma)
I'm using ChromaDB to store vector representations of document chunks.
This allows fast and efficient retrieval based on semantic similarity.
6. Defining a Prompt for Querying the Model
I define a prompt template that provides a context-aware answer based on retrieved text from the vector database.
7. Creating a LangChain Retrieval Pipeline
My chain follows this workflow:
The retriever fetches relevant document chunks.
The prompt structures the retrieved text into a query format.
The LLM (Mistral-7B) generates a response based on the retrieved text.
The output parser extracts the final answer.
8. Running a Query
Finally, I test the pipeline with a query:
"Give me a product list nearby Bentota?"
The retriever finds relevant chunks, and the LLM generates an answer based on the document content.
Why This Approach?
No OpenAI API dependency → Uses Hugging Face models.
Efficient retrieval → Uses ChromaDB and sentence-transformers.
Scalable → Can process large PDFs and multiple queries.
Good for custom LLM use cases → Can be fine-tuned with different LLMs.
