# Model and Runtime Recommendations

These are starting points, not guaranteed optimal values. Msty controls vary by version and by Local AI backend. Apply only settings exposed by the selected backend.

## Model assignment

| Task | Preferred model | Notes |
|---|---|---|
| Explain a function / small code lookup | Qwen2.5-Coder 3B | Quick, narrow tasks |
| Read a small group of related files | Qwen2.5-Coder 7B | Ask for evidence from file paths |
| PHP / JavaScript implementation | Qwen2.5-Coder 7B | Keep tasks bounded |
| SQL review / schema reasoning | Qwen2.5-Coder 7B | Verify against actual schema |
| Documentation edits | 3B for small edits; 7B for multi-file reconciliation | Never invent undocumented behavior |
| Architecture and security review | 7B as an assistant | Treat output as hypotheses; human review required |
| Large cross-module refactor | Neither as an unsupervised agent | Split into small, reviewed tasks |

## Conservative starting parameters

If the backend exposes these controls:
- Context: start at 8K or 16K; try 24K only if stable and useful. Do not set the model's advertised maximum just because it is available.
- Temperature: 0.1–0.2 for code changes and structured analysis.
- Top-p: leave backend default initially; change only if you have a repeatable evaluation.
- GPU offload: use the maximum stable offload that does not cause memory pressure or system instability.
- Parallel requests: 1.
- Keep-alive: use backend default unless model reload latency is a problem.
- Output length: allow enough room for a complete diff explanation, but avoid excessively large generations.

The exact Q4_K_M memory requirement includes more than weight files: runtime buffers, context/KV cache, and GPU/CPU allocation also matter. A 4 GB GPU does not mean the whole 7B model and its context will fit in VRAM. CPU/RAM offload is acceptable if latency remains usable.

## Tool-use reliability test

Do not assume that a model can reliably call tools just because it can chat. In a new Agent Session, ask it to:
1. List the top-level project folders.
2. Read the project entry point and explain how a request is handled.
3. Identify one relevant PHP file and quote the function name and path.
4. Make no changes.

If the agent cannot consistently select/read files or reports invented paths, treat it as a chat model rather than a dependable tool-using agent for that workflow.

## Practical recommendation

Use 7B as the default assistant model if it is stable. Use 3B only for lightweight tasks. If 7B struggles with long context, reduce the task scope and provide specific files rather than immediately increasing context size.
