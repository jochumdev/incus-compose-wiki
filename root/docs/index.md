---
tags: []
leafwiki_id: -X6_3lBvR
leafwiki_title: Docs
leafwiki_created_at: "2026-07-05T03:53:58.899190577Z"
leafwiki_updated_at: "2026-07-05T04:11:03.966788866Z"
leafwiki_creator_id: vOmfrlBDg
leafwiki_last_author_id: vOmfrlBDg
---
# Docs

## Using incus-compose

- [Getting Started](/docs/v1/getting-started) - Install and run your first compose project
- [Terminology](/docs/v1/terminology) - Compose vs Incus vs incus-compose terms (service vs instance, ...)
- [CLI Reference](/docs/v1/cli-reference) - All commands and options
- [Compose Compatibility](/docs/v1/compose-compatibility) - Supported features and differences
- [Builds](/docs/v1/builds) - Build service images from Compose `build:` definitions
- [Health Checking](/docs/v1/healthd) - Healthchecks, restart policies, and `service_healthy` dependencies via the ic-healthd sidecar (a core component; includes [debugging](/docs/v1/healthd#debugging-ic-healthd))
- [Environment Variables](/docs/v1/environment-variables) - How env vars and interpolation work
- [Why Incus?](/docs/v1/why-incus) - Benefits over Docker

## Contributing and Internals

- [Contributing](https://github.com/lxc/incus-compose/blob/main/CONTRIBUTING.md) - Coding, style, and workflow rules
- [Architecture](/docs/v1/architecture) - Resource-first design, layers, x-incus extensions
- [Client Package](/docs/v1/architecture/client) - Resources, Stack, WorkerPool, hooks
- [Testing](/docs/v1/architecture/testing) - just commands, test patterns, fixtures
- [GitHub Actions Runner](/docs/v1/github-runner) - Set up a self-hosted runner for the test suite
