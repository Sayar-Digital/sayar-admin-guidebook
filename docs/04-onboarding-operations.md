# 4. Onboarding Operations

## Goal

Complete merchant onboarding using the same requirement engine used for merchant self-service.

## Operator Flow

1. Open merchant profile
2. Click `Complete onboarding` (when visible)
3. Follow requirement order exactly
4. Save each section
5. Recompute/refresh and verify updated state

## Rules

- No waivers in V1
- All required steps must be completed through real checks
- Use retries where supported; do not bypass with fake data

## Common Requirement Groups

- Business details
- WhatsApp connection
- Meta catalog mapping
- Payment details
- Fulfillment option setup

## Operational Good State

- No missing required requirements
- Onboarding completion at expected final state
- Merchant can proceed to activation checks
