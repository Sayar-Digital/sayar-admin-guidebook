# 10. Runbooks

## Incident Severity

- `P1`: Active payment/checkout outage or broad merchant impact
- `P2`: Major degradation with workaround
- `P3`: Localized failure or non-blocking issue

## Standard Runbook Format

1. Symptom
2. Scope
3. Immediate containment
4. Root-cause checks
5. Safe recovery steps
6. Validation
7. Audit log and handoff

## Recommended First Runbooks to Author

1. Paystack webhook misconfiguration
2. Checkout flow failures spike
3. Template provisioning failures
4. WhatsApp messaging elevated incidents
