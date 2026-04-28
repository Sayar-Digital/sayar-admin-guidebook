# 6. Merchant Health

## What Health Score Means

A quick risk summary out of 100.

## Score Bands

- `85-100`: healthy
- `55-84`: needs attention
- `0-54`: critical

## Current Penalty Model

Start at `100`, deduct fixed penalties for:

- Incomplete onboarding
- Unverified email
- Flow not ready
- Elevated messaging
- Any open issue count > 0
- Payment success rate below 85%

Reference note:

- [merchant-health-score-onboarding-note.md](merchant-health-score-onboarding-note.md)

## Open Issue Definition (Operational)

Open issues combine:

- failed checkouts
- expired checkouts
- failed WhatsApp events
- plus 1 when WhatsApp connection/verification/subscription is unhealthy
