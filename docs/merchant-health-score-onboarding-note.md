# Merchant Health Score (Team Onboarding Note)

This is the exact scoring used by Admin Merchant Health today.

## Formula

Start from `100`, then subtract penalties:

- `-25` if onboarding is incomplete
- `-20` if email is unverified
- `-15` if flow status is not `ready`
- `-15` if messaging is elevated
- `-10` if `open_issue_count > 0`
- `-15` if payment success rate (24h) is below `85%`

Final score is clamped between `0` and `100`.

Health state bands:

- `healthy`: `85-100`
- `needs_attention`: `55-84`
- `critical`: `0-54`

## Payment Success Rate (24h)

Payment success rate is:

- `paid / (paid + failed + expired)`

Important:

- This is merchant-scoped (only that merchant's attempts)
- If there are zero attempts, rate is `0` (UI should show "No payment attempts in the last 24h")

## What Counts as an Open Issue

`open_issue_count` is built from:

- failed checkouts (24h)
- expired checkouts (24h)
- failed WhatsApp events (24h)
- plus `+1` if WhatsApp setup is not healthy:
  - connection is not connected, or
  - verification is not verified, or
  - webhook subscription is not subscribed

## Important Intricacies

- Open-issue penalty is binary: any value above `0` gives the same `-10` score hit.
- Messaging-elevated is threshold based (not gradual):
  - short window: failed events `>= 5`, or
  - failure rate `>= 10%` when total events `>= 20`.

## Needs Attention: WhatsApp + Templates

- **How many failed WhatsApp events put a merchant in Needs Attention?**
  - In the 24h queue window, messaging is treated as elevated when:
    - failed WhatsApp events are `>= 5`, or
    - failed rate is `>= 10%` with at least `20` total WhatsApp events.
  - Elevated messaging can place the merchant in Needs Attention.

- **Do template issues put a merchant in Needs Attention today?**
  - Not directly.
  - Template status (missing/failed/stale/pending/ready) is tracked in template health surfaces and retry flows.
  - Current Needs Attention queue is driven by structural blockers + operational incidents (payments/expiry/messaging), not template rows directly.

## Source of Truth in Code

- `/sayar-internal/admin/pipes/dashboard.pipe.go`
  - `computeMerchantHealthScoreState`
  - `computeMerchantPaymentSuccessRate`
  - `queryPaymentOutcomeCountsForMerchant`
  - `isMessagingElevatedForWindow`
