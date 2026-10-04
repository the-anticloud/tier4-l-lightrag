# Developer Cookbook — L_LIGHTRAG

> Anticloud sovereign integration guide. All commands run offline.
> Author: Lois-Kleinner Alpasan / Anticloud FZ LLE
> USPTO pending 2026.

---

## Prerequisites

```bash
# Python 3.11+
python --version

# AIOSS ledger CLI (build from source)
cd TIER_1_ANTICLOUD_CORE/AIOSS_FORMAT/src && cargo build --release
export PATH="$PATH:$(pwd)/target/release"
aioss --version

# Initialize your ledger
aioss init --ledger ./ledger/main.aioss
```

---

## Installation

```bash
pip install lightrag-hku
```

Verify:
```bash
python -c "import importlib; m = importlib.import_module('llightrag'); print('OK:', m)"
```

---

## Quickstart

```bash
python -c "from lightrag import LightRAG; rag = LightRAG(working_dir='./rag_data'); print('Ready')"
```

---

## Configuration

```yaml
# LightRAG config
working_dir: ./rag_data
llm_model_func: ollama/qwen2.5  # local Ollama
embedding_model: nomic-embed-text
chunk_size: 1200
chunk_overlap: 100
```

---

## Anticloud Integration Pattern

```python
from lightrag import LightRAG, QueryParam
from lightrag.utils import EmbeddingFunc
import asyncio

rag = LightRAG(
    working_dir="./rag_data",
    llm_model_func=ollama_model_func,  # your local LLM function
)

# Insert documents
with open("docs/report.txt") as f:
    asyncio.run(rag.ainsert(f.read()))

# Query with graph-aware retrieval
result = rag.query("What are the key findings?", param=QueryParam(mode="global"))
print(result)
```

---

## AIOSS Ledger Integration

Every significant L_LIGHTRAG operation should emit a ledger entry:

```python
import subprocess, json, hashlib

def aioss_append(ledger_path: str, event: dict):
    content = json.dumps(event, sort_keys=True)
    r = subprocess.run(
        ["aioss", "append", "--ledger", ledger_path, content],
        capture_output=True, text=True
    )
    if r.returncode != 0:
        print("[AIOSS] Warning:", r.stderr)
    return r.returncode == 0

# Usage
aioss_append("./ledger/main.aioss", {
    "project": "L_LIGHTRAG",
    "event": "run",
    "input_hash": hashlib.sha3_256(b"your_input").hexdigest(),
})
```

Verify the chain at any time:
```bash
aioss verify --ledger ./ledger/main.aioss
```

---

## Benchmarking

Run the Anticloud 3-seed benchmark:
```bash
python BENCHMARKS/ENVIRONMENT_LAB_RESULTS_TEMPLATE.py
# Results at: OFFICIAL_BENCHMARKS/Environment_Lab_Results/results.json
```

For GPU benchmarks (T4):
```
https://www.kaggle.com/code/loiskleinner/anticloud-real-benchmarks
```

---

## Docker

```bash
# Full stack
docker compose up anticloud-ledger anticloud-inference

# Benchmark runner
docker compose run anticloud-bench

# Check health
curl http://localhost:8080/health  # AIOSS ledger
curl http://localhost:8000/health  # vLLM inference
```

---

## Common Issues

**Knowledge graph empty:** Run insert before query. Check working_dir has write permissions.
**Slow graph build:** Expected on first insert. Subsequent inserts are incremental.

---

## Further Reading

- [RESEARCH_PAPERS/anticloud_l_lightrag_paper.md](../RESEARCH_PAPERS/anticloud_l_lightrag_paper.md) — technical paper with citations
- [OFFICIAL_BENCHMARKS/](../OFFICIAL_BENCHMARKS/) — benchmark results
- [ENTERPRISE_LICENSING/PRICING.md](../ENTERPRISE_LICENSING/PRICING.md) — commercial licensing
- [CONTRACTS/MSA/MASTER_SERVICE_AGREEMENT.md](../CONTRACTS/MSA/MASTER_SERVICE_AGREEMENT.md) — MSA template
