## API Reference

Interactive docs available at `http://localhost:8000/docs` when the backend is running.

### `POST /api/v1/auth/login`
```json
Request:  { "username": "bob_eng", "password": "eng123" }
Response: { "access_token": "<jwt>", "token_type": "bearer",
            "role": "engineering", "departments_allowed": ["engineering"] }
```

### `POST /api/v1/ingest` *(admin only)*
```
Content-Type: multipart/form-data
  file:     <PDF or TXT file>
  metadata: '{"department":"hr","category":"policy","version":"1.0",
              "doc_date":"2024-06-01","chunking_strategy":"fixed"}'

Response 202:
  { "job_id": "<uuid>", "status": "processing", "doc_id": "<uuid>" }
```

### `POST /api/v1/chat`
```json
Request:
{
  "query": "What is the annual leave policy?",
  "filters": { "department": "hr", "category": "policy" },
  "retrieval_mode": "hybrid",
  "session_id": "optional-existing-session-id"
}

Response:
{
  "answer": "Employees are entitled to...",
  "sources": [
    {
      "doc_id": "...", "doc_name": "HR Leave Policy v1.0",
      "department": "hr", "chunk_text": "...(200 chars)...",
      "chunk_id": "...", "score": 0.89, "page": null
    }
  ],
  "retrieval_mode_used": "hybrid",
  "confidence": "high",
  "session_id": "..."
}
```

### `GET /api/v1/documents`
```
Query params: department?, category?, page=1, page_size=20
Response: { "documents": [...], "total": 42, "page": 1 }
```

### `POST /api/v1/feedback`
```json
Request:  { "session_id": "...", "query": "...", "helpful": true, "comment": "Good answer" }
Response: { "status": "recorded" }
```

---
