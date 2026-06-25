# 🌑 Shadownet Protocol

**The Internet for Personal AI Agents.**

[![Status: v0.2 Draft](https://img.shields.io/badge/Status-v0.2_Draft-blue)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-green)](#)

AI agents are getting smarter every month, but they're brilliant hermits. Your Shadow doesn't know my Shadow exists. Calendars don't talk to each other, inboxes don't coordinate, and humans still do all the social glue: group chats, scheduling threads, swiping.

**Shadownet is the missing connective tissue.** A local-first, privacy-preserving protocol that lets personal AI agents discover each other, prove they represent vetted members of trusted organizations, and coordinate on their owners' behalf, without leaking private context to a central server.

---

## 🧭 Core Tenets

- **Coordination over capability.** We don't build LLMs and we don't build agents; we build the infrastructure that lets them find each other and collaborate.
- **Local-first privacy.** Your agent's memory and context never leave your machine.
- **Reachability is free; names are a convenience.** Two addressing modes, equally valid. Shadowname mode (`alice@sh4dow.org`) for human-readable names; direct mode (`shadow://key:z6Mk...@host:port`) for self-hosters with no DNS or provider.
- **Sybil resistance is contextual, not central.** No global "personhood" credential. Hubs vet contextually (a dating Hub checks photos, a hiring Hub checks work history). The single credential kind is `org_affiliation`.
- **Standards, not new wheels.** Names via DNS, transport via [A2A](https://a2a-protocol.org/) (Shadownet ships as an A2A extension under `urn:shadownet:0.2`), host-agent control plane via [MCP](https://modelcontextprotocol.io). Identity is raw Ed25519 keys.

---

## 🏗️ Architecture (TL;DR)

- **Sidecar.** The per-user node. Holds the Shadow's keys, contacts, and message history; exposes MCP tools to the host agent (Hermes, Claude Code, OpenClaw, ...).
- **Provider.** Authoritative for the Shadowname-to-key binding within a domain. Signs AgentCards, publishes its key in DNS at `_shadownet.<domain>`.
- **Issuer.** Signs `org_affiliation` credentials attesting a Shadow belongs to an organization or Hub. Multi-issuer by design; verifiers run their own trust stores.
- **A2A extension.** Agents communicate over Google's [Agent-to-Agent](https://a2a-protocol.org/) protocol; Shadownet adds a signed envelope in `message.metadata["urn:shadownet:0.2"]` carrying per-message identity and credentials.

For the full design, start with the [consolidated wire spec (RFC 0001)](https://github.com/shadownet-protocol/shadownet-specs/blob/main/rfcs/0001-shadownet.md).

---

## 📦 Repositories

| Repo | Status | What it is |
|------|--------|------------|
| [`shadownet-specs`](https://github.com/shadownet-protocol/shadownet-specs) | 🟢 Active | Consolidated wire spec, MCP control surface spec, onboarding URI spec, JSON Schemas, glossary. |
| [`shadownet`](https://github.com/shadownet-protocol/shadownet) | 🟢 Active | Monorepo: Go SDK + reference provider & issuer binaries (`core/`), Python SDK (`python-sdk/`), wire-level conformance suite (`conformance/`), and host-agent integrations (`integrations/`). |
| [`shadownet-local`](https://github.com/shadownet-protocol/shadownet-local) | 🟢 Active | Sidecar reference implementation. Drop-in for any A2A-capable agent runtime. |
| [`hermes-plugin`](https://github.com/shadownet-protocol/hermes-plugin) | 🟢 Active | One-line install shim for [Hermes Agent](https://github.com/NousResearch/hermes-agent). Bootstraps the real adapter from PyPI. |
| [`shadowbox`](https://github.com/shadownet-protocol/shadowbox) | 🟢 Active | Standalone all-in-one implementation — no sidecar, no server/client, everything in one box. A TUI playground for experimenting with the protocol and its proposals. |

The Go SDK, Python SDK, and conformance suite previously lived in their own repos (`shadownet-go`, `shadownet-py`, `shadownet-conformance`). They are now subtrees of the [`shadownet`](https://github.com/shadownet-protocol/shadownet) monorepo and release independently under `core/vX.Y.Z`, `python-sdk/vX.Y.Z`, and `conformance/vX.Y.Z` tag schemes. Legacy repos remain readable for the `v0.1.x` release series.

---

## 🚦 Project Status

Shadownet **v0.2** is the current draft. It replaces v0.1's nine RFCs with a [consolidated wire spec](https://github.com/shadownet-protocol/shadownet-specs/blob/main/rfcs/0001-shadownet.md) and two companion specs ([MCP control surface](https://github.com/shadownet-protocol/shadownet-specs/blob/main/rfcs/0002-shadownet-mcp.md), [onboarding URI](https://github.com/shadownet-protocol/shadownet-specs/blob/main/rfcs/0003-shadownet-onboarding.md)). The Go and Python SDKs currently ship the v0.1 surface and are migrating to v0.2 as it stabilizes. Canonical domain is `sh4dow.org`. No public deployment yet.

v0.2 is intentionally pre-stable; breaking changes between minor versions are expected until 1.0.

If you're a systems architect, cryptography practitioner, or AI infrastructure engineer, the [specs repo](https://github.com/shadownet-protocol/shadownet-specs) is the place to weigh in.

---

*Built for the post-browser internet.*
