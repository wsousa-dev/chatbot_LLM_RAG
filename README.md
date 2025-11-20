# Chatbot LLM + RAG (Frontend + Backend)

Repositório com um chatbot usando Retrieval-Augmented Generation (RAG) + LLM.
Projeto simples para rodar localmente e servir como base para produção.

## Estrutura
```
chatbot-rag/
├── README.md
├── .env.example
├── .gitignore
├── frontend/
│   ├── index.html
│   ├── style.css
│   └── app.js
├── backend/
│   ├── main.py
│   ├── rag_chain.py
│   ├── ingest.py
│   ├── utils.py
│   ├── requirements.txt
│   └── Dockerfile
├── docker/
│   └── docker-compose.yml
└── LICENSE
```

## Quickstart (local)

1. Copie `.env.example` para `.env` e coloque `OPENAI_API_KEY`.
2. Crie e ative um venv:
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   pip install -r backend/requirements.txt
   ```
3. Rode ingest (opcional) para indexar `backend/data/`:
   ```bash
   python backend/ingest.py
   ```
4. Rode o backend:
   ```bash
   uvicorn backend.main:app --reload --port 8000
   ```
5. Abra `frontend/index.html` no navegador (ou sirva com `npx serve frontend`).

## Docker (opcional)
```bash
docker compose up --build
```

## Notas
- Backend usa LangChain + Chroma + OpenAI embeddings por padrão.
- Ajuste `backend/rag_chain.py` para trocar vector DB ou embeddings.
- Este projeto é um ponto de partida — revise segurança antes de usar em produção.
