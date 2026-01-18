#

## Purpose

This Jupyter notebook creates a **fully local, retrieval-augmented generation (RAG) system** that lets you ask natural-language questions about the King James Version (KJV) Bible and get accurate, cited answers based solely on the exact biblical text.

It combines:
- A clean, structured KJV Bible dataset (31,102 verses)
- Semantic search over every verse
- Local LLM generation (Llama 3.2 3B via Ollama)
- Persistent vector storage for fast reuse

No fine-tuning, no cloud APIs — everything runs locally.


## llamda3.2

```sh
ollama pull llama3.2:latest
```

- 3B parameter instruction-tuned variant
- Context window: 128K tokens (plenty for stuffing retrieved Bible verses)
- Optimized for dialogue, summarization, and agentic/retrieval tasks → aligns nicely with RAG/Q&A over documents

Compared to alternatives:

- Phi-3.5-mini (~3.8B): Slightly smarter on reasoning in some tests, but often similar or a bit slower on laptop GPUs.
- Llama-3.1-8B: Noticeably smarter/more accurate, but ~5 GB quantized → uses more VRAM, slower inference (~30–50 t/s), higher chance of hitting memory limits if you retrieve many verses.
- Gemma-2-2B/9B or Qwen2.5-3B: Also excellent small options, similar speed/quality to Llama 3.2 3B.


## Get/Prep KJV Data Set

For this example we will use a pre-structured KJV dataset from https://huggingface.co/datasets

(The notebook will retrieve this and cache it to ~/.cache/huggingface/datasets)


## RAG

```sh
uv python pin 3.12
uv venv
source .venv/bin/activate
uv pip install llama-index llama-index-llms-ollama llama-index-embeddings-huggingface chromadb
uv pip install llama-index-vector-stores-chroma
uv pip install jupyterlab datasets
```

Now, enable the Jupyter notebook kernel and run the notebook.


## Upgrade Later

Upgrade to Llama-3.1-8B or Phi-4-mini later (easy to swap in Ollama).


