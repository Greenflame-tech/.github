# AIOS — Artificial Intelligence Operating System

AIOS is an **epistemic operating system for AI reasoning**.  
It is designed to ingest unstructured data, extract claims, track provenance, detect contradictions, and manage multiple “worlds” of belief without collapsing uncertainty into premature truth.

AIOS is not a chatbot framework.  
It is infrastructure for **thinking systems**.

---

## Core Principles

- **Claims are not facts**  
  All extracted claims begin as *unverified* and reside in a liminal epistemic state until promoted.

- **Truth is procedural**  
  Truth emerges through evidence, contradiction analysis, and world separation — not assertion.

- **Separation of concerns**
  - SQL → persistence & provenance
  - Vector search → similarity & discovery
  - RDF → asserted knowledge only

---

## Architecture Overview

### 1. Ingestion & Provenance
- Raw inputs are ingested into a DAG (`dag_node`, `dag_edge`)
- Content is normalized into `document_section`
- All downstream reasoning links back to original sources

### 2. Claim Extraction
- Sections are split into sentences
- Claims are extracted using linguistic heuristics (SPO when possible)
- Stored in `claim_candidate`
- All claims are:
  - status = `pending`
  - world = `liminal`

### 3. Vector Reasoning (RAG)
- Claims are embedded into **isolated Qdrant collections**
- Embeddings are versioned and model-aware
- No vector store is treated as authoritative memory

### 4. Reasoning Graphs (SQL)
AIOS stores reasoning artifacts explicitly:
- `claim_similarity_edge`
- `claim_contradiction_candidate`
- `world_split_candidate`

These are **records of inference**, not truth.

### 5. RDF Promotion
- Only promoted claims enter RDF
- RDF represents *asserted knowledge*, not hypotheses
- Promotion is logged and reversible

---

## Worlds & Epistemics

AIOS supports multiple concurrent epistemic worlds:
- `liminal` — unverified observations
- asserted worlds — curated, defended knowledge spaces
- split worlds — contradiction-driven divergence

Worlds are first-class, queryable, and isolated.

---

## What AIOS Is For

- Long-term AI memory
- Contradiction-aware reasoning
- Multi-world simulations
- Knowledge curation pipelines
- Epistemic hygiene in AI systems

---

## What AIOS Is Not

- A chatbot UI
- A knowledge graph toy
- A vector database wrapper
- A truth oracle

---

## Status

AIOS is under active development.
Expect rapid iteration, schema evolution, and experimental reasoning modules.

---

## License

Project licensing will be published as the system stabilizes.
