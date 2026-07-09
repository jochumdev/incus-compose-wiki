---
date: 2026-07-05T01:27:16.661Z
dateCreated: 2026-07-05T01:03:24.052Z
description: null
editor: markdown
published: true
tags: []
title: Why Incus?
leafwiki_id: GDzu3_fDR
leafwiki_title: Why Incus?
leafwiki_created_at: "2026-07-05T03:54:00.356119734Z"
leafwiki_updated_at: "2026-07-09T01:12:08.407275897Z"
leafwiki_creator_id: vOmfrlBDg
leafwiki_last_author_id: vOmfrlBDg
---

# Why Incus?

Incus excels at running system containers and VMs, but most tooling today assumes
OCI engines. `incus-compose` bridges that gap efficiently.

## Drive It From Any Desktop

Incus is client/server. The daemon is Linux-only, but the `incus` client (and
`incus-compose`) is a cross-platform Go binary. From a Windows or macOS desktop
you connect to a remote Linux host over HTTPS and manage **OCI app containers,
LXC system containers, and full VMs** - all without Docker Desktop, WSL, or a
local Linux VM.

Docker Desktop cannot do this: on Windows and macOS it runs a hidden Linux VM to
host the engine. With Incus the workload lives on real Linux infrastructure and
your laptop is just a thin client.

See [Installing on Windows](/getting-started/windows) for the client setup.

## The Problem

Running OCI engines inside Incus containers is a common pattern, but it's wasteful:

```
┌─────────────────────────────┐
│    Incus Container          │
│  ┌──────────────────────┐   │
│  │   OCI Engine Daemon  │   │
│  │  ┌────────────────┐  │   │
│  │  │  Your App      │  │   │
│  │  └────────────────┘  │   │
│  └──────────────────────┘   │
└─────────────────────────────┘
```

**Problems with this approach:**

- Double overhead (two container runtimes)
- Nested namespaces add complexity
- Security concerns with privileged nested containers
- Storage inefficiency from layered filesystems

## The Solution

Run OCI images directly on Incus with `incus-compose`:

```
┌─────────────────────────────┐
│          Incus              │
│  ┌────────────────┐         │
│  │   Your App     │         │
│  └────────────────┘         │
└─────────────────────────────┘
```

**Benefits:**

- Single layer of containerization
- Native Incus efficiency and security
- Same compose files you already use
- No wasted resources

## Key Advantages

| Feature        | OCI Engines               | Incus                                |
| -------------- | ------------------------- | ------------------------------------ |
| Container type | Application (PID 1 = app) | System (full init)                   |
| Isolation      | Namespaces only           | LXC namespaces + cgroups             |
| Security       | Varying models            | VM-like isolation                    |
| Networking     | Port mapping via iptables | Real IPs and port proxies            |
| Storage        | Overlay filesystem        | ZFS/Btrfs with instant snapshots     |
| Image caching  | Per-engine cache          | Global blob cache, per-project alias |

## Scale Beyond a Single Host

**[Incus clustering](https://linuxcontainers.org/incus/docs/main/explanation/clustering/):**

- Scale from 1 to 100+ bare metal hosts
- Single API endpoint for the entire cluster
- Automatic instance placement and load balancing
- Live migration between hosts
- No complex orchestration layer needed

**[IncusOS](https://linuxcontainers.org/incus-os/):**

- Immutable OS purpose-built for Incus
- Safe, predictable updates
- Minimal attack surface
- Production-ready out of the box

## When to Use Incus

**Choose Incus when:**

- You need to shell into containers for debugging
- You want true RW volumes (not Kubernetes volume limitations)
- You need real network addresses (no port conflicts)
- You want VM-like isolation without VM overhead
- You need ZFS/Btrfs snapshots and clones
- You're running apps that expect a full OS environment
- Security and multi-tenancy are priorities
- You're already using Incus for infrastructure
- You need to scale from dev laptop to production cluster seamlessly

**Stick with OCI engines when:**

- You're targeting Kubernetes deployment
- You need the absolute broadest ecosystem compatibility

## See Also

- [Getting Started](/getting-started) - install and run your first project
- [Compose Compatibility](/compose-compatibility) - what works and what does not
