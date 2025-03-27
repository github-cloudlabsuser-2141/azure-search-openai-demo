# Backend Application Documentation

## Overview

The `app/backend` directory contains the backend application for the RAG (Retrieval Augmented Generation) chat app. This backend is built using the [Quart](https://quart.palletsprojects.com/) framework and integrates with Azure services such as Azure OpenAI, Azure Cognitive Search, Azure Blob Storage, and Azure Speech Service. It provides APIs for chat, document ingestion, and other features.

## Features

- **Chat APIs**: Supports multi-turn conversations and single-turn Q&A using Azure OpenAI models.
- **Document Ingestion**: Allows users to upload documents for indexing and retrieval.
- **Speech Synthesis**: Converts text to speech using Azure Speech Service.
- **Authentication**: Supports authentication and access control using Azure AD.
- **Integration with Azure Services**:
  - Azure OpenAI for GPT models.
  - Azure Cognitive Search for document retrieval.
  - Azure Blob Storage for file storage.
  - Azure Speech Service for speech synthesis.

## Directory Structure

```
app/backend/
├── approaches/               # Contains different RAG approaches for chat and Q&A
├── static/                   # Static files served by the backend
├── templates/                # HTML templates (if any)
├── app.py                    # Main entry point for the backend application
├── config.py                 # Configuration constants
├── decorators.py             # Custom decorators for authentication
├── error.py                  # Error handling utilities
├── prepdocs.py               # Document ingestion and processing logic
├── requirements.txt          # Python dependencies
└── chat_history/             # Chat history storage implementations
```

## Getting Started

### Prerequisites

- Python 3.8 or higher
- Azure account with the following services:
  - Azure OpenAI
  - Azure Cognitive Search
  - Azure Blob Storage
  - Azure Speech Service

### Installation

1. Navigate to the `app/backend` directory:
   ```sh
   cd app/backend
   ```

2. Create a Python virtual environment:
   ```sh
   python -m venv .venv
   .venv\Scripts\activate  # On Windows
   ```

3. Install the required dependencies:
   ```sh
   pip install -r requirements.txt
   ```

### Running the Application

To start the backend server, run:

```sh
python app.py
```

The application will be accessible at `http://localhost:50505` by default.

### Environment Variables

The backend relies on several environment variables for configuration. Below are some key variables:

- `AZURE_STORAGE_ACCOUNT`: Azure Blob Storage account name.
- `AZURE_STORAGE_CONTAINER`: Azure Blob Storage container name.
- `AZURE_SEARCH_SERVICE`: Azure Cognitive Search service name.
- `AZURE_SEARCH_INDEX`: Azure Cognitive Search index name.
- `OPENAI_HOST`: Host for OpenAI API (e.g., `azure` or `local`).
- `AZURE_OPENAI_API_KEY`: API key for Azure OpenAI.
- `USE_USER_UPLOAD`: Enable user document upload feature (`true` or `false`).

Refer to the code in `app.py` for the full list of environment variables.

## API Endpoints

### `/`
Serves the static frontend.

### `/ask` (POST)
Handles single-turn Q&A using the configured RAG approach.

### `/chat` (POST)
Handles multi-turn conversations.

### `/chat/stream` (POST)
Streams chat responses for real-time updates.

### `/upload` (POST)
Allows users to upload documents for ingestion.

### `/list_uploaded` (GET)
Lists uploaded documents for the authenticated user.

### `/delete_uploaded` (POST)
Deletes a specific uploaded document.

### `/speech` (POST)
Converts text to speech using Azure Speech Service.

### `/config` (GET)
Returns the configuration options enabled in the backend.

## Requirements

The backend application depends on the following Python packages, as listed in `requirements.txt`:

```
azure-cognitiveservices-speech==1.40.0
azure-common==1.1.28
azure-core==1.30.2
azure-core-tracing-opentelemetry==1.0.0b11
azure-cosmos==4.9.0
azure-identity==1.17.1
azure-monitor-opentelemetry==1.6.1
azure-monitor-opentelemetry-exporter==1.0.0b32
azure-search-documents==11.6.0b9
azure-storage-blob==12.22.0
azure-storage-file-datalake==12.16.0
beautifulsoup4==4.12.3
blinker==1.8.2
certifi==2024.7.4
cffi==1.17.0
charset-normalizer==3.3.2
```

## Contributing

Contributions are welcome! Please refer to the [CONTRIBUTING.md](../../CONTRIBUTING.md) file for guidelines.

## License

This project is licensed under the terms of the [LICENSE](../../LICENSE) file.