# 🌑 Shadownet Protocol

**The Internet for Personal AI Agents.**

[![Status: v0.1 Implementation](https://img.shields.io/badge/Status-v0.1_Implementation-blue)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-green)](#)

AI agents are getting smarter every month — but they're brilliant hermits. Your Shadow doesn't know my Shadow exists. Calendars don't talk to each other, inboxes don't coordinate, and humans still do all the social glue: group chats, scheduling threads, swiping.

**Shadownet is the missing connective tissue.** A local-first, privacy-preserving protocol that lets personal AI agents discover each other, verify they represent real humans, and negotiate on their owners' behalf — without leaking private context to a central server.

---

## 🧭 Core Tenets

- **Coordination over capability** — we don't build LLMs and we don't build agents; we build the infrastructure that lets them find each other and collaborate.
- **Local-first privacy** — your agent's memory and context never leave your machine.
- **Decentralized identity** — agents are bound to humans via DIDs, blocking Sybil attacks without a central authority.
- **Human-in-the-loop** — every agent ↔ human exchange flows through MCP, fully auditable.

---

## 🏗️ Architecture (TL;DR)

- **Sidecar** — the per-user node. Holds the Subject's keys, contacts, and message history; exposes MCP tools to the host agent (Hermes, OpenClaw, Claude Desktop, …).
- **SNS (Shadow Name Service)** — DNS-style name resolution. `mahdi@sh4dow.org` → endpoint + public key.
- **SCA (Shadow Certificate Authority)** — issues Verifiable Credentials proving a Shadow represents a unique human (or an organization). Multi-issuer by design; verifiers run their own trust stores.
- **A2A profile** — agents communicate over Google's [Agent-to-Agent](https://google.github.io/A2A/) protocol; Shadownet adds a thin handshake on top to exchange credentials.

*Hubs (themed stranger-matching for Dating, Hiring, Roommates, …) are out of v0.1 scope.*

For the full design, start with the [protocol overview RFC](https://github.com/shadownet-protocol/shadownet-specs/blob/main/rfcs/0001-overview.md).

---

## 📦 Repositories

| Repo | Status | What it is |
|------|--------|------------|
| [`shadownet-specs`](https://github.com/shadownet-protocol/shadownet-specs) | 🟢 Active | RFCs, JSON Schemas, worked examples — the protocol itself. |
| [`shadownet`](https://github.com/shadownet-protocol/shadownet) | 🟢 Active | Monorepo: Go SDK + reference SCA / SNS / CLI (`core/`), Python SDK (`python-sdk/`), wire-level conformance suite (`conformance/`), and host-agent plugins (`integrations/`). A TypeScript SDK is planned as an additional subtree. |
| [`hermes-social`](https://github.com/meghancampbel9/hermes-social) | 🟢 Active | Sidecar reference implementation. Drop-in for any A2A-capable agent runtime. |

The Go SDK, Python SDK, and conformance suite previously lived in their own repos (`shadownet-go`, `shadownet-py`, `shadownet-conformance`). They are now subtrees of the [`shadownet`](https://github.com/shadownet-protocol/shadownet) monorepo and release independently under `core/vX.Y.Z`, `python-sdk/vX.Y.Z`, and `conformance/vX.Y.Z` tag schemes.

---

## 🚦 Project Status

The v0.1 protocol is drafted across seven RFCs in [`shadownet-specs`](https://github.com/shadownet-protocol/shadownet-specs/tree/main/rfcs): Overview, Identity, Credentials, SCA, SNS, A2A Profile, and MCP Tools. The Go and Python SDKs ship the full v0.1 surface; the cross-impl wire-level conformance suite ships too. Canonical domain is `sh4dow.org`. A TypeScript SDK is next. No public deployment yet.

If you're a systems architect, cryptography practitioner, or AI infrastructure engineer, the RFCs are the place to weigh in.

---

*Built for the post-browser internet.*
