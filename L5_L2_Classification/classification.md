# L5 Narrow / L2 General Classification — L_LIGHTRAG
**Platform:** Anticloud | **Tier:** TIER_4_INFERENCE_AGENTS | **PAX:** 27B
**IP:** USPTO pending 2026, Anticloud FZ LLE, 0-1.gg | **License:** Apache-2.0

## L5 Narrow
L_LIGHTRAG is a lightweight, low-latency alternative to full GraphRAG. It uses a simplified graph index (entity co-occurrence rather than full KG) for sub-100ms retrieval. Narrow scope: Anticloud corpus retrieval for real-time inference pipelines where K_GRAPHRAG latency is too high.

## L2 General
L2 General: L_LIGHTRAG is the fast-path retrieval for any tier's latency-sensitive inference. TIER_9 robotics real-time planning (50ms budget) and TIER_8 RF anomaly detection use L_LIGHTRAG where K_GRAPHRAG is too slow.

## PAX 27B Integration
PAX 27B synthesis is called after L_LIGHTRAG retrieval. The lightweight graph index reduces retrieval from K_GRAPHRAG's ~500ms to <100ms, leaving more latency budget for PAX generation.

## AIOSS Audit Chain
Every retrieval + generation event (query hash + retrieved context hash + synthesis hash + latency_ms) is chained: H_n = SHA3-256(H_{n-1} || entry_hash_n || timestamp_n).
Offline-verifiable, tamper-evident, zero cloud dependency.

## Regulatory / Compliance
GDPR Art. 25 (local retrieval). ISO/IEC 42001 (AI system transparency).
