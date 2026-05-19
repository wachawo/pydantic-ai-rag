# pydantic-ai-rag

This project is included in [pydantic-ai-toolbox](https://github.com/wachawo/pydantic-ai-toolbox/blob/main/docs/RAG.md).

## Install

```bash
pip install "pydantic-ai-toolbox[rag]"
```

## Usage

```python
from pydantic_ai import Agent
from pydantic_ai_toolbox import RAGToolset

rag = RAGToolset(
    embedder=my_embedder,
    chunk_size=1000,
    chunk_overlap=100,
    storage_path="./index",
    distance="cosine",
    max_results=20,
    namespace="default",
)
rag.add_text("The sky is green.", doc_id="d-sky")

agent = Agent("openai:gpt-4o", toolsets=[rag])
agent.run_sync("What color is the sky?")
```

`embedder` is any callable mapping `list[str] -> list[list[float]]` (OpenAI, a local model, or a stub for tests).

Full reference and a runnable example: [RAG.md](https://github.com/wachawo/pydantic-ai-toolbox/blob/main/docs/RAG.md).
