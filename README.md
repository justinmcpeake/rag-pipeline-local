# Local RAG Pipeline — ChromaDB + LlamaIndex + Ollama

A retrieval-augmented generation pipeline that runs entirely on local hardware. No OpenAI API. No cloud inference. Designed for privacy-sensitive document workloads.

## What it does

1. Ingests documents (PDF, DOCX, TXT)
2. Chunks and embeds using Nomic-Embed-Text (via Ollama)
3. Stores vectors in ChromaDB
4. At query time: retrieves relevant chunks, passes to Llama 3 for response generation
5. Returns grounded answer with source citations

## Why local?

Built as part of Fortress — a private AI platform for professional clients who cannot use cloud AI due to legal privilege, confidentiality obligations, or data sovereignty requirements. Everything runs on the client's own hardware.

## Stack

- **LLM:** Ollama (Llama 3 8B / 70B)
- **Embeddings:** Nomic-Embed-Text via Ollama
- **Vector DB:** ChromaDB
- **Document indexing:** LlamaIndex
- **Language:** Python 3.11+

## Architecture

```
Document ingestion
      ↓
  LlamaIndex (chunking + indexing)
      ↓
  Nomic-Embed-Text (embedding via Ollama)
      ↓
  ChromaDB (vector storage)
      ↑
  Query → embed → retrieve → rerank
      ↓
  Llama 3 (local inference via Ollama)
      ↓
  Grounded response + source citations
```

## Status

**Architecture documented.** Implementation in progress as part of Fortress. Code will be published here as components are extracted and cleaned for public release.

## Author

Justin McPeake — [LinkedIn](https://www.linkedin.com/in/justin-mcpeake-85492140b)
Part of the [Fortress](https://github.com/justinmcpeake/fortress-architecture) private AI platform.
