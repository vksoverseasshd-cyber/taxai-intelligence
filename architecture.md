# TAXAI INTELLIGENCE — System Architecture

## 1. Overview

TAXAI INTELLIGENCE is an AI-powered Indian Income Tax document
intelligence application built using Retrieval-Augmented Generation (RAG).

The system retrieves relevant information from a curated tax knowledge
base and uses a Large Language Model (LLM) to generate contextual,
grounded responses.

The architecture is designed to be modular, maintainable,
scalable, and testable.

## 2. Architectural Layers

The application is divided into four major layers:

### 2.1 Presentation Layer

Technology: Streamlit

Responsibilities:

- User interaction
- Chat interface
- PDF upload
- Query submission
- Answer display
- Source reference display
- Conversation history interface

### 2.2 Application and Orchestration Layer

Responsibilities:

- Coordinate document processing workflows
- Coordinate query processing workflows
- Manage interactions between AI components
- Build context for LLM requests
- Control the end-to-end RAG pipeline

### 2.3 AI Processing Layer

Responsibilities:

- PDF text extraction
- Text cleaning
- Document chunking
- Metadata generation
- Embedding generation
- Semantic retrieval
- Context construction
- LLM response generation
- Response grounding and validation

### 2.4 Data and External Services Layer

Components:

- ChromaDB — vector storage and retrieval
- Document Storage — source document management
- DeepSeek API — LLM inference

Responsibilities:

- Persist document knowledge
- Store vector embeddings
- Retrieve relevant document chunks
- Connect to external LLM services

## 3. Architectural Principles

- Separation of concerns
- Modular design
- Loose coupling
- Reusability
- Testability
- Maintainability
- Knowledge base independence from application logic
- Grounded AI responses
- Source transparency
## 4. Data Flow Architecture

The application contains two primary workflows:

### 4.1 Document Ingestion Pipeline

The document ingestion pipeline transforms uploaded PDF documents
into searchable knowledge.

Workflow:

1. PDF Upload
2. Text Extraction
3. Text Cleaning
4. Text Chunking
5. Metadata Assignment
6. Embedding Generation
7. Storage in ChromaDB

The resulting knowledge base stores document chunks, embeddings,
and associated metadata for semantic retrieval.

### 4.2 Query Processing Pipeline

The query processing pipeline retrieves relevant knowledge and
generates a contextual response.

Workflow:

1. User submits a question.
2. The question is converted into an embedding.
3. ChromaDB retrieves relevant document chunks.
4. The retrieved information is passed to the Context Builder.
5. The Context Builder prepares context for the LLM.
6. DeepSeek generates a response using the question and context.
7. Response validation checks grounding and supporting evidence.
8. The response and available source references are returned to the user.

### 4.3 Component Responsibilities

- Embedding Model: Converts text into numerical vector representations.
- ChromaDB: Stores embeddings, chunks, and metadata and supports similarity retrieval.
- Retrieval Engine: Retrieves relevant knowledge based on the user's query.
- Context Builder: Organizes retrieved content into the LLM input.
- DeepSeek: Generates natural-language responses using the supplied context.
- Response Validator: Checks response grounding and evidence availability.

### 4.4 Knowledge Flow

Document ingestion and query processing are separate workflows.

The ingestion pipeline populates the knowledge base.

The query pipeline uses the knowledge base to retrieve relevant
information at runtime.

The knowledge base acts as the connection point between
document processing and query processing.
## 5. Retrieval Strategy

The system uses semantic search to identify relevant document chunks
based on the user's query.

Retrieval may be enhanced using metadata filters such as:

- Section number
- Financial year
- Document category
- Document source

When a user explicitly mentions a tax section, the system may use
section-aware metadata filtering to improve retrieval precision.

For queries involving multiple sections, retrieval should include
all explicitly requested sections.

For general queries, broad semantic retrieval should be used
without unnecessarily restricting the knowledge base.

## 6. Technology Stack

| Component | Technology |
|---|---|
| Programming Language | Python |
| User Interface | Streamlit |
| LLM | DeepSeek API |
| Embedding Model | all-MiniLM-L6-v2 |
| Vector Database | ChromaDB |
| PDF Processing | PDF text extraction library |
| Metadata Storage | Document metadata |
| Development Environment | VS Code |

## 7. Reliability and Grounding

The system is designed to generate responses grounded in retrieved
knowledge.

Reliability mechanisms include:

- Relevant document retrieval
- Source metadata
- Page-level references where available
- Context-aware prompt construction
- Insufficient-context handling
- Response validation
- Retrieval and answer evaluation

If relevant supporting information cannot be retrieved, the system
should avoid presenting unsupported claims as verified tax facts.

## 8. MVP 1 Limitations

MVP 1 is a document-based AI research assistant and is not a
professional tax advisory system.

Potential limitations include:

- Incorrect PDF text extraction
- Incomplete document coverage
- Retrieval errors
- Ambiguous queries
- Outdated source documents
- LLM-generated inaccuracies

The application should clearly communicate these limitations.

## 9. Future Enhancements

Potential future capabilities include:

- Improved hybrid retrieval
- Keyword and semantic search combination
- Reranking models
- Advanced metadata filtering
- Automated knowledge base updates
- Tax rule change detection
- Evaluation dashboards
- Document comparison
- AI-assisted impact analysis