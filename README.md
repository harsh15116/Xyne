# Xyne: Google Workspace RAG Application

This project implements a TypeScript application that retrieves content from Google Workspace (Docs, Sheets, Calendar), processes it for RAG (Retrieval Augmented Generation), and indexes it in Vespa for search and chat.

## Video

[Click here to see demo video](https://drive.google.com/file/d/1PPMRcgWBvZQ9ZXM6MKEZCvo5OH15zo9z/view)

## Screenshots
![Screenshot 2025-05-25 203424](https://github.com/user-attachments/assets/f4c2047a-c474-4c8b-bb26-0bf9edeb73cb)
![Screenshot 2025-05-25 203445](https://github.com/user-attachments/assets/e1d4edb9-36df-4ca3-b5c4-545f9a0cadf9)
![Screenshot 2025-05-25 203531](https://github.com/user-attachments/assets/7f5b33aa-0ad9-4975-b44a-3c891b502517)



## Features

- **Google OAuth 2.0 Integration**: Secure authentication for accessing Google Workspace content
- **Content Processing**: Extract, chunk, and embed content from Google Docs, Sheets, and Calendar
- **Vespa Integration**: Multi-vector indexing with hybrid search capabilities
- **Chat Interface**: Interactive chat with source attribution from indexed content
- **TypeScript Implementation**: Strongly typed codebase with clean architecture

## Architecture
[Check out complete architecture here](https://github.com/harsh15116/Xyne/blob/master/architecture.md)

### 1. Authentication Flow

The application uses Google OAuth 2.0 to authenticate users and access their Google Workspace content:

- OAuth consent screen requests appropriate scopes for Docs, Sheets, and Calendar
- Access tokens are securely stored and refreshed as needed
- All API requests to Google services use these tokens

### 2. Content Processing Pipeline

Content is processed through a pipeline:

1. **Content Retrieval**: Extract text from Google Docs, Sheets, and Calendar
2. **Chunking**: Break content into semantic chunks with configurable size and overlap
3. **Embedding Generation**: Generate embeddings for each chunk using Gemini's embedding-001 model
4. **Metadata Association**: Maintain relationships between chunks and source documents

### 3. Vespa Schema and Indexing

The application uses Vespa for vector search with:

- Multi-vector indexing to maintain document-chunk relationships
- Hybrid search combining lexical (BM25) and semantic vector search
- HNSW index for efficient approximate nearest neighbor search
- Custom ranking profiles for different search scenarios

### 4. Chat Interface

The chat interface:

- Embeds user queries and searches for relevant content
- Provides source attribution for all responses
- Uses the AI SDK with Gemini's gemini-2.0-flash model for natural language generation

## Setup Instructions

### Prerequisites

1. Node.js 18+ and npm/yarn
2. Vespa instance (cloud)
3. Google Cloud Project with OAuth credentials
4. Gemini API key

