# Exaltry Engineering Case Study

Exaltry is a small hosting operation used to develop practical experience in infrastructure automation, billing workflows, deployment safety, and customer-facing reliability.

This repository is a sanitized case study. It contains no credentials, customer information, private source code, origin addresses, server identifiers, or production configuration.

## Problems addressed

- connect checkout events to a guarded provisioning workflow
- validate configuration before production changes
- make deployment and rollback procedures reproducible
- prevent secrets and internal network details from entering public artifacts
- document customer handoff, backups, billing lifecycle states, and incident checks
- keep irreversible or customer-impacting actions behind explicit approval gates

## Engineering approach

The system uses small, composable checks rather than one opaque deployment command. Preflight scripts validate secrets hygiene, configuration shape, customer-facing links, billing mode, and launch readiness. Operational runbooks separate dry-run verification from production application.

Certificate renewal and service reload behavior are treated as an end-to-end reliability concern: a renewed file is insufficient if the long-running service still presents an expired certificate. The workflow therefore verifies the served certificate and expected authenticated response after reload.

## What this demonstrates

- Linux service operations and reverse-proxy configuration
- defensive PowerShell, Python, and JavaScript automation
- Stripe-style webhook and subscription lifecycle reasoning
- Cloudflare Worker and static-site deployment workflows
- TLS diagnosis, renewal hooks, and post-change verification
- written runbooks, go/no-go criteria, rollback steps, and evidence boundaries

See [architecture and safety boundaries](docs/architecture.md).

