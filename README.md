```text
                     ┌────────────────────────────┐
                     │          Clients           │
                     │ (OpenAI, Claude, LocalLLM) │
                     └─────────────┬──────────────┘
                                   │
                                   ▼
                 ┌──────────────────────────────────┐
                 │        PiMCP Gateway Layer        │
                 │ (FastAPI + Redis Pub/Sub + JWT)   │
                 └────────────────┬──────────────────┘
                                  │
     ┌────────────────────────────┴────────────────────────────┐
     │                                                         │
┌───────────────┐                                     ┌───────────────┐
│  MCP Node A   │                                     │  MCP Node B   │
│  (Tokyo Edge) │                                     │  (SF Cloud)   │
│ - local tools │                                     │ - GCP tools   │
│ - log agent   │                                     │ - DB adapter  │
│ - vector db   │◀───── Redis / etcd Context Sync ───▶│ - shell exec  │
└───────────────┘                                     └───────────────┘
     │                                                         │
     ▼                                                         ▼
 Local Tools: Shell, FS, AI Inference              Cloud Tools: SQL, API, Storage
```
