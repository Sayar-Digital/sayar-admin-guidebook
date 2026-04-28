# 5. Needs Attention Queue

## What This Queue Is

A triage list for merchants with operational or structural risk signals.

## What Can Put a Merchant Here

- Failed payments in window
- Expired checkouts in window
- Elevated messaging failures
- WhatsApp structural blockers
- Latest flow provisioning failure

## WhatsApp Elevated Threshold

Messaging is elevated when either condition is true:

- Failed WhatsApp events `>= 5`, or
- Failed rate `>= 10%` with at least `20` total events

## What Does Not Directly Trigger This Queue Today

- Template issues alone (missing/failed/stale templates are handled in template health/retry flows)

## How To Read Score, Risk, and Age

- `Score`: Priority weight for that merchant row. Higher score means handle sooner.
- `Risk`: Estimated revenue risk based on recent failed/expired checkout activity and failed WhatsApp events.
- `Age`: How long since the latest recorded incident on that row.

### Why You May See `Score: 0`, `Risk: ₦0`, `Age: —`

- This usually means the row is a structural blocker (for example WhatsApp setup not ready), not a recent transaction/event failure burst.
- `Age: —` means no latest incident timestamp is recorded for that row yet.

## Triage Workflow

1. Open row details
2. Confirm primary blocker
3. Execute safe retry/fix
4. Refresh state
5. Escalate if still failing

## Where To Click

1. Open `Needs attention` from sidebar.
2. Start from highest severity rows.
3. Open merchant profile from row action and resolve blocker.

![Needs attention page](./screenshots/04-needs-attention.png)
