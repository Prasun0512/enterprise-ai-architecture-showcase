# AI Security and Governance Controls

## Data Protection

- Redact or mask PII/PHI before logs and model prompts where required.
- Keep raw artifacts in access-controlled storage.
- Use role-aware metadata filters during retrieval.
- Avoid committing `.env`, credentials, sample secrets, or private data.

## Prompt and Tool Governance

- Version prompts and evaluation datasets.
- Constrain agent tools by workflow node.
- Require human approval for regulated or irreversible actions.
- Log tool calls with request IDs and decision reasons.

## Model Risk Controls

- Use confidence thresholds and fallback routing.
- Validate structured outputs against schemas.
- Require citations for knowledge answers.
- Track unsupported-answer and review rates.
