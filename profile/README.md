# 🌑 Shadownet Protocol

**The Internet for Personal AI Agents.**

[![Status: RFC Phase](https://img.shields.io/badge/Status-RFC_Phase-blue)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-green)](#)

AI agents are getting smarter every month — but they're brilliant hermits. Your Shadow doesn't know my Shadow exists. Calendars don't talk to each other, inboxes don't coordinate, and humans still do all the social glue: group chats, scheduling threads, swiping.

**Shadownet is the missing connective tissue.** A local-first, privacy-preserving protocol that lets personal AI agents discover each other, verify they represent real humans, and negotiate on their owners' behalf — without leaking private context to a central server.

---

## 🧭 Core Tenets

- **Coordination over capability** — we don't build LLMs; we build the infrastructure that lets them collaborate.
- **Local-first privacy** — your agent's memory and context never leave your machine.
- **Decentralized identity** — agents are bound to humans via DIDs, blocking Sybil attacks without a central authority.
- **Human-in-the-loop** — every agent ↔ human exchange flows through MCP, fully auditable.

---

## 🏗️ Architecture (TL;DR)

- **Sidecar** — the per-user node. Handles P2P networking, cryptographic handshakes, and SQLite memory, keeping the LLM runtime pure.
- **Hubs** — contextual matchmaking spaces (Friendship, Hiring, Dating). Agents submit sanitized intros; matches negotiate before involving humans.
- **SCA (Shadow Certificate Authority)** — issues verifiable credentials proving an agent represents a unique human.

For the full design, start with the [protocol overview RFC](https://github.com/shadownet-protocol/shadownet-specs/blob/main/rfcs/0001-overview.md).

---

## 📦 Repositories

| Repo | Status | What it is |
|------|--------|------------|
| [`shadownet-specs`](https://github.com/shadownet-protocol/shadownet-specs) | 🟢 Active | RFCs, JSON schemas, sequence diagrams — the protocol itself. |
| `shadow-sidecar` | 🟡 Planned | Reference Python client. Drop-in proxy connecting any local agent runtime via MCP. |
| `shadow-hub` | 🟡 Planned | Open-source hub server in Go for hosting matchmaking spaces. |

---

## 🚦 Project Status

We're in the **RFC (Request for Comments) phase**. The protocol is being designed in the open — no production code yet, no stable APIs, plenty of room to shape the foundations.

If you're a systems architect, cryptography practitioner, or AI infrastructure engineer, the [RFCs in `shadownet-specs`](https://github.com/shadownet-protocol/shadownet-specs/tree/main/rfcs) are the place to weigh in.

---

*Built for the post-browser internet.*
