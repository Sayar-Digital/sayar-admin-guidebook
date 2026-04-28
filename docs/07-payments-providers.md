# 7. Payments Providers

## Purpose

Show supported providers, readiness/connection state, and operational controls.

## Operating Model

- Providers are integrated at system level first
- Merchant-level usage depends on system support + merchant setup

## What to Check

1. Provider is enabled for environment
2. Credentials are present and valid
3. Webhook URL is correct for environment
4. Runtime state is healthy

## Environment Webhook Reminder

Use the correct route per environment to avoid false failures.

- Local: `http://localhost:<api-port>/webhook/payment/paystack`
- Staging: `https://staging-api.usesayar.com/webhook/payment/paystack`
- Production: `https://prod-api.usesayar.com/webhook/payment/paystack`
