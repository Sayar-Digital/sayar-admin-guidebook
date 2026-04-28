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

## Triage Workflow

1. Open row details
2. Confirm primary blocker
3. Execute safe retry/fix
4. Refresh state
5. Escalate if still failing
