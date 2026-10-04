# Pylint_Quality_Lab_Results
**Project:** `L_LIGHTRAG` | **Status:** `PASS` | **Run:** `2026-09-30T17:14:20.030944+00:00`

**Framework:** [Pylint — Python Code Quality Analyzer](https://pylint.readthedocs.io/)

## Key Metrics

- **files_analyzed:** `5`
- **pylint_score:** `7.25`
- **pylint_score_max:** `10.0`

## Raw Output (first 50 lines)
```
************* Module setup
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG\UPSTREAM\setup.py:1:0: C0114: Missing module docstring (missing-module-docstring)
************* Module generate_query
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG\UPSTREAM\examples\generate_query.py:1:0: C0114: Missing module docstring (missing-module-docstring)
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG\UPSTREAM\examples\generate_query.py:1:0: E0401: Unable to import 'openai' (import-error)
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG\UPSTREAM\examples\generate_query.py:6:0: C0116: Missing function or method docstring (missing-function-docstring)
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG\UPSTREAM\examples\generate_query.py:6:0: W0102: Dangerous default value [] as argument (dangerous-default-value)
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG\UPSTREAM\examples\generate_query.py:7:25: W0621: Redefining name 'prompt' from outer scope (line 27) (redefined-outer-name)
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG\UPSTREAM\examples\generate_query.py:54:9: W1514: Using open without explicitly specifying an encoding (unspecified-encoding)
************* Module graph_visual_with_html
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG\UPSTREAM\examples\graph_visual_with_html.py:1:0: C0114: Missing module docstring (missing-module-docstring)
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG\UPSTREAM\examples\graph_visual_with_html.py:1:0: E0401: Unable to import 'pipmaster' (import-error)
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG\UPSTREAM\examples\graph_visual_with_html.py:9:0: E0401: Unable to import 'pyvis.network' (import-error)
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG\UPSTREAM\examples\graph_visual_with_html.py:24:20: C0209: Formatting a regular string which could be an f-string (consider-using-f-string)
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG\UPSTREAM\examples\graph_visual_with_html.py:10:0: C0411: standard import "random" should be placed before third party imports "pipmaster", "networkx", "pyvis.network.Network" (wrong-import-order)
************* Module graph_visual_with_neo4j
TIER_4_INFERENCE_AGENTS\L_LIGHTRAG
```

---
_Anticloud Independent Benchmark — 2026-09-30T17:14:20.030944+00:00_