# LLD: Email-to-Case GenAI Automation Sequence

```mermaid
sequenceDiagram
  participant Graph as Microsoft Graph
  participant Fn as Azure Function
  participant Blob as Blob Storage
  participant Bus as Service Bus
  participant OCR as Document Intelligence
  participant LLM as Azure OpenAI
  participant Review as Review Queue
  participant Case as Case API

  Graph->>Fn: New email notification
  Fn->>Blob: Store raw email and attachments
  Fn->>Bus: Publish message with artifact URI
  Bus->>OCR: Extract text and layout
  OCR->>LLM: Send normalized redacted context
  LLM->>Fn: Structured fields + confidence
  Fn->>Fn: Validate schema and thresholds
  alt Low confidence or high risk
    Fn->>Review: Create review task
  else Validated
    Fn->>Case: Create case payload
  end
```

## Implementation Notes

- Use idempotency keys from message IDs.
- Keep source artifact links for audit.
- Redact sensitive data before logging.
- Send failed events to DLQ with retry metadata.
