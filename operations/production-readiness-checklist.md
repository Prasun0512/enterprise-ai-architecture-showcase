# Production Readiness Checklist

## Engineering

- Unit and integration tests
- Dockerfile and docker-compose for local runs
- CI with linting and tests
- Typed config through environment variables
- No secrets in source control

## Observability

- Request IDs propagated across services
- Structured logs for ingestion, retrieval, generation, validation, and writes
- Metrics for latency, failures, review rate, token usage, and cost
- Alerts for DLQ growth and retrieval-quality regression

## Scalability

- Queue-based ingestion for burst control
- Stateless API layer
- Batch embedding jobs
- Index lifecycle and archival policy
- Retry budgets and dead-letter handling

## Cost Optimization

- Cache embeddings for unchanged documents
- Use smaller models for classification and routing
- Route only complex cases to premium LLMs
- Track token usage by workflow and tenant
