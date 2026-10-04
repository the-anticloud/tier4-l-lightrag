# Ledger Status

**Project:** `L_LIGHTRAG`  
**Tier:** TIER_4_INFERENCE_AGENTS  
**Identity:** Upstream `HKUDS/LightRAG` @ `453dce83d6d0` (MIT)

## Chain state

| Fact | Value |
| --- | --- |
| Upstream | `HKUDS/LightRAG` |
| Commit | `453dce83d6d0354a06e46c8d4029a0895c4e054b` |
| Upstream licence | MIT |
| Licence class | permissive |
| Clone size | 26.71 MB |
| Ledger | 0 blocks, chain verified |
| Current TRL | NOT YET MEASURED |
| Post-optimisation TRL | NOT YET MEASURED |
| II budget cap | 1000.0 IIU |
| Verified upstream edits | 1 |

- Blocks: **0**
- Head digest: `None`
- Chain verification: **verified**

## Independent verification

The chain is verifiable without trusting this project's tooling:

```
anticloud ledger verify
anticloud ledger export > ledger.jsonl
```

Each block carries the previous block's digest, so removing or reordering an
entry invalidates every block after it. That property is the reason the
ledger can stand in for a claim of what happened.
