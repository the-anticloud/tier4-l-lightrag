# Deploy Guide — L_LIGHTRAG
**Tier:** TIER_4_INFERENCE_AGENTS | **Stack:** Python 3.11, networkx, SQLite, sentence-transformers, PAX 27B, AIOSS_FORMAT
**Air-gap capable after initial setup.**

## Prerequisites
Python 3.11+, sentence-transformers, SQLite (stdlib), networkx 3.2+, PAX 27B.

## Environment
4GB RAM for lightweight index. CPU-only for retrieval. GPU for PAX synthesis.

## AIOSS Integration
```bash
aioss init --module L_LIGHTRAG --output ./l_lightrag.aioss
aioss append --chain ./l_lightrag.aioss --payload ./output.bin --module L_LIGHTRAG
aioss verify --chain ./l_lightrag.aioss
```

## Air-Gap Setup
```bash
pip download -r requirements.txt -d ./wheels/
pip install --no-index --find-links ./wheels/ -r requirements.txt
```

## PAX 27B Harness Wiring
```python
from anticloud_pax import PAXHarness
harness = PAXHarness(
    model_path="./pax-27b-q4.gguf",
    module="L_LIGHTRAG",
    aioss_chain="./L_LIGHTRAG.aioss",
    classification="L5_NARROW_L2_GENERAL"
)
result = harness.process(input_data)
```

## Verification
```bash
aioss verify --chain ./L_LIGHTRAG.aioss --verbose
python -m L_LIGHTRAG.tests.smoke
```
