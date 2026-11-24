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