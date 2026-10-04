# Developer Cookbook — L_LIGHTRAG
**Stack:** Python 3.11, networkx, SQLite, sentence-transformers, PAX 27B, AIOSS_FORMAT
**Domain:** LightRAG: lightweight graph-aware RAG for fast context retrieval in inference pipelines

## Fast RAG query
```python
from l_lightrag import LightRAG

rag = LightRAG(
    index_path="./lightrag_index/",
    pax_model="./pax-27b-q4.gguf",
    aioss_chain="./lightrag.aioss"
)

result = rag.query("ROS2 Nav2 obstacle avoidance parameters", max_tokens=128)
print(result.answer, f"({result.latency_ms:.0f}ms)")
print(f"Chain: {result.chain_hash}")
```

## Build index
```python
rag.build_index(
    source_dir="E:/fenta/Downloads/The Anticloud",
    extensions=[".py", ".md"]
)
```

## Benchmark vs K_GRAPHRAG
```python
bench = rag.benchmark_vs_graphrag(test_queries="./bench.jsonl")
print(f"LightRAG P99: {bench.lightrag_p99:.0f}ms | GraphRAG P99: {bench.graphrag_p99:.0f}ms")
print(f"LightRAG accuracy: {bench.lightrag_acc:.2f} | GraphRAG: {bench.graphrag_acc:.2f}")
```

## AIOSS Chain Append
```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()
```
