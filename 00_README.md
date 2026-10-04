# Anticloud × LIGHTRAG
> Local-first RAG — knowledge retrieval that never phones home.

**Part of:** Inference Agents · Anticloud FZ LLE · 0-1.gg
**Upstream:** HKUDS/LightRAG (MIT)
**License:** Apache-2.0 OR LicenseRef-Anticommons-Enterprise-1.0
**IP:** USPTO pending · Lois-Kleinner Alpasan · 2026

Graph + LLM for semantic retrieval. We remove OpenAI dependency and add tamper-evident citation hashing.

```bash
from lightrag_anticloud import LightRAG

rag = LightRAG(
    working_dir="./rag_workspace",
    embedding_model="nomic-embed-text",  # local, no API
    ledger_path="./pax_ledger.aioss",
)

answer = rag.query("What is Poseidon hash?")
# Every citation: [source, k5_hash, ledger_block_id]
```

**Plays well with:** K-GRAPHRAG, K-AIOSS, K-NEURO (for symbolic reasoning layer)
