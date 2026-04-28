# 11. Audit and Controls

## Why This Matters

Admin actions can materially affect merchant operations. Every sensitive action must be traceable.

## Minimum Audit Fields

- actor type
- actor id
- merchant id
- action
- before state
- after state
- reason (required for overrides/manual interventions)
- source
- idempotency key

## Operator Policy

- Never perform silent changes
- Always include a reason for corrective actions
- Prefer idempotent operations and verify post-write state
