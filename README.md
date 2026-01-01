## Production-ready RAG Agent from techwithtim

- Upload pdf to vector db - Qdrant

- Api call to openai api to answer question based on the uploaded files

- Inngest for observability, logging, retries, throttling and rate limiting (production-grade)

## Setting up

Install dependency

```
pip install fastapi inngest llama-index-core llama-index-readers-file python-dotenv qdrant-client uvicorn streamlit openai
```

Create a .env file and includes your OPENAI_API_KEY

## To run

Create qdrant database

```
docker run -d --name qdrantRagDb -p 6333:6333 -v "$./qdrant_storage:/qdrant/storage" qdrant/qdrant
```

Run fastapi on uvicorn server

```
uvicorn main:app
```

Run inngest server (on a new terminal)

```
npx inngest-cli@latest dev -u http://127.0.0.1:8000/api/inngest --no-discovery
```

Run streamlit frontend (on a new terminal)

```
sudo streamlit run ./streamlit_app.py
```
