# HF_Leaderboard_Lab_Results

**Project:** `L_LIGHTRAG`  
**Tier:** `TIER_4_INFERENCE_AGENTS`  
**Slug:** `HKUDS/LightRAG`  
**Commit:** `453dce83d6d0`  
**Run:** `2026-09-30T15:07:07.146295+00:00`  

## Isolation Environment

| Field | Value |
| ----- | ----- |
| Platform | `win32` |
| Python | `3.12.10` |
| HF model | `distilbert-base-uncased` |
| HF load time | `4.42s` |
| Inference device | `cpu` |

## Results

**Framework:** [HuggingFace Open LLM Leaderboard (proxy via distilbert-base-uncased)](https://huggingface.co/docs/leaderboards/en/open_llm_leaderboard/archive)

**Model used:** `distilbert-base-uncased`

### Inference Latency (Classification)

| Metric | Value |
| ------ | ----- |
| Avg latency | **55.67 ms** |
| Min latency | 46.69 ms |
| Max latency | 61.08 ms |
| Samples | 5 |

### Real Tokenization Results

| Field | Value |
| ----- | ----- |
| Token count | **35** |
| Tokenization latency | 1.0 ms |
| Classification label | `LABEL_0` |
| Classification score | 0.5906 |
| Classification latency | 75.47 ms |
| Status | **PASS** |

**Input text tokenized:**
```
L_LIGHTRAG (HKUDS/LightRAG) — 1329 files, 450562 source lines, licence MIT, primary language ['Python']
```

**First 20 tokens:**
```
['[CLS]', 'l', '_', 'light', '##rag', '(', 'hk', '##ud', '##s', '/', 'light', '##rag', ')', '—', '132', '##9', 'files', ',', '450', '##56']
```

> Full MMLU/HellaSwag/TruthfulQA/ARC/Winogrande/GSM8K require dedicated GPU.
> These results are CPU inference proxy metrics using distilbert-base-uncased.

---
_Anticloud Benchmark Suite — isolation log — 2026-09-30T15:07:07.146295+00:00_