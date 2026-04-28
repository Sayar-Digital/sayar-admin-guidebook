# 9. Troubleshooting

## Common Cases

## "Merchant stuck in onboarding"

- Check missing requirements list
- Complete in required sequence
- Recompute and refresh state

## "Needs attention not clearing"

- Confirm root trigger still exists (payments/expiry/messaging/structural)
- Run allowed retries
- Refresh queue and merchant health

## "Payment provider shows unhealthy"

- Confirm environment webhook URL
- Confirm credentials status
- Run readiness check

## "Template retry keeps failing"

- Confirm merchant WhatsApp credentials
- Confirm template definition is correct
- Check last error and retry only after fixing root cause

## Where To Click

1. Use `Operations` for provider/health diagnostics.
2. Use `Security` for access-control or account safety checks.
3. Use merchant profile diagnostics for merchant-level incidents.

![Operations diagnostics](./screenshots/07-operations.png)
![Security page](./screenshots/08-security.png)
