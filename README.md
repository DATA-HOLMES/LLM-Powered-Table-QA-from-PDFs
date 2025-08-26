# 📑 LLM-Powered Table QA from PDFs

An end-to-end pipeline that extracts **tabular data from institutional PDFs** (scanned + digital), segments them by headings, and enables **zero-shot question answering** on the tables using **NVIDIA’s Nemotron-253B LLM** via an OpenAI-compatible API.

---

## 🚀 Project Overview
Institutional reports (like **NIRF submissions**) often come as **large, messy PDFs** with both scanned and digital content. Extracting structured tabular data from them is challenging.  

This project combines:
1. **Rule-based PDF parsing + OCR** → Detect headings, chunk PDFs into structured dictionaries.  
2. **LLM-powered QA** → Query tables directly with natural language (e.g., *“How many regular faculty does the institution have?”*).  
3. **Zero-shot inference** → No fine-tuning or embeddings; answers are extracted via carefully designed prompts.  

---

## 🏗️ Architecture & Workflow
```mermaid
flowchart TD
    A[Input PDF] --> B[PDF Text Extraction - PyMuPDF + OCR]
    B --> C[Heading Detection - Font/Size/Bold Rules]
    C --> D[Chunking into Table Dictionary]
    D --> E[Stringify Tables for LLM]
    E --> F[ZeroShotLLM Wrapper - Nemotron 253B API]
    F --> G[Clean Answer]
