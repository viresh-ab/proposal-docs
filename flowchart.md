```text
                             
                             ┌────────────────────────────────┐
                             │          FRONTEND UI           │
                             │   Next.js / React / Streamlit  │
                             │  Proposal Wizard + Editor UI   │
                             └───────────────┬────────────────┘
                                             │
                                             │ REST API
                                             ▼
                             ┌───────────────────────────────┐
                             │     PROPOSAL ORCHESTRATOR     │
                             │        FastAPI (Python)       │
                             │   Workflow + Session Control  │
                             └───────────────┬───────────────┘
                                             │
        ┌────────────────────────────────────┼────────────────────────────────────┐
        │                                    │                                    │
        ▼                                    ▼                                    ▼

┌──────────────────────────┐   ┌───────────────────────────────┐   ┌────────────────────────────┐
│      RFP PROCESSOR       │   │     KNOWLEDGE RETRIEVAL       │   │      LLM GENERATION        │
│  PyMuPDF / python-docx   │   │   LlamaIndex Retrieval Layer  │   │  OpenAI / Claude / Ollama  │
│   Optional Tesseract OCR │   │                               │   │  Prompt Builder + Sections │
└───────────────┬──────────┘   └───────────────┬───────────────┘   └──────────────┬─────────────┘
                │                              │                                  │
                ▼                              ▼                                  ▼

     ┌────────────────────────┐    ┌────────────────────────────┐    ┌────────────────────────────┐
     │ Structured RFP Output  │    │ Vector DB: Qdrant / Chroma │    │ Proposal JSON Store        │
     │ (requirements, scope)  │    │ Embeddings: BGE / E5 local │    │ PostgreSQL / JSON storage  │
     └────────────────────────┘    └──────────────┬─────────────┘    └──────────────┬─────────────┘
                                                  │
              ┌───────────────────────────────────┼──────────────────────────────────┐
              │                                   │                                  │
              ▼                                   ▼                                  ▼

   ┌────────────────────────────┐   ┌────────────────────────────┐   ┌────────────────────────────┐
   │ Methodology Templates DB   │   │ Previous Proposals DB      │   │ Reusable Sections DB       │
   │ PostgreSQL + embeddings    │   │ PostgreSQL + embeddings    │   │ PostgreSQL + embeddings    │
   └──────────────┬─────────────┘   └──────────────┬─────────────┘   └──────────────┬─────────────┘
                  │                                │                                 │
                  └───────────────┬────────────────┴───────────────┬────────────────┘
                                  ▼                                ▼
                         ┌────────────────────────────────────────────┐
                         │      CONTEXT BUNDLE BUILDER (RAG)          │
                         │   Selected templates + snippets packaged   │
                         └────────────────────────────┬───────────────┘
                                                      ▼
                             ┌────────────────────────────────────┐
                             │        VISUAL & FORMAT ENGINE      │
                             │ Mermaid / D2 / Chart.js / Plotly   │
                             │ Layout + Document Assembly         │
                             └────────────────────┬───────────────┘
                                                  ▼
                             ┌────────────────────────────────────┐
                             │          EXPORT SERVICE            │
                             │ python-docx / WeasyPrint / PPTX    │
                             │ Generates DOCX / PDF / PPT         │
                             └────────────────────────────────────┘

```
