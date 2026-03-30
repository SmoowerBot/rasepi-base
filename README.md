<div align="center">

Rasepi
Documentation you and AI can actually trust.

Multilingual-first collaborative documentation platform with freshness scoring, forced expiry, and a plugin-first architecture.

<img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License: MIT">

<img src="https://img.shields.io/badge/.NET-10.0-purple" alt=".NET">

<img src="https://img.shields.io/badge/Vue-3-brightgreen" alt="Vue">

<img src="https://img.shields.io/badge/Status-Beta (Invite Only)-orange" alt="Status">

</div>

[!IMPORTANT]
Rasepi is currently in closed beta. Access is invite-only. To get early access, sign up at rasepi.com/signup. We're onboarding users in waves — early signups get priority and a free extended trial at launch.

Why Rasepi?
Your team writes great docs. But six months later, nobody knows if they're still correct — and your AI tools don't know either. They just serve whatever they find.

Rasepi fixes that:

Freshness scoring — Every document earns a live trust score and gets flagged when it goes stale
Forced expiry — Entries must have an expiration date. Expired docs are hidden from search and AI until reviewed
Multilingual-first — Block-level translation system that publishes to 40+ languages with 94% cost savings on partial updates
Plugin architecture — Core handles docs and collaboration; everything else is a plugin
Features
Block-Level Translation
Unlike full-page translation, Rasepi translates at the paragraph level. When you edit one paragraph, only that block is retranslated — not the entire document. A SHA256 content hash on each block detects staleness automatically.

Freshness & Expiry
Every entry has a configurable expiry (6 months, 1 year, etc.). Expired entries are hidden from search, moved to an "Expired" section, and require manual review before republication.

Real-Time Collaboration
Google Docs-style co-editing powered by SignalR, with per-language editing sessions so translators never conflict with original authors.

Plugin System
Build your own translation providers, export formats, integrations, and more:

Tech Stack
Layer	Technology
Frontend	Vue 3, TypeScript, Vuetify 3, TipTap, Pinia
Backend	.NET 10, ASP.NET Core, Entity Framework Core
Real-time	SignalR
Database	SQL Server (prod) / InMemory (dev)
Background Jobs	Hangfire
Auth	OpenIddict (OpenID Connect)
Logging	Serilog + Seq
Getting Started
Prerequisites
Docker & Docker Compose
Quick Start
This starts:

SQL Server on localhost:1433
Redis on localhost:6379
API on http://localhost:5000 (with Swagger at /swagger)
Frontend on http://localhost:5173
SQL Server takes ~30s to initialize on first run. The API will auto-restart if it connects before the database is ready.

Without Docker
Backend:

Frontend:

Project Structure
API Documentation
Swagger UI is available at http://localhost:5000/swagger when running the backend.

Contributing
We welcome contributions! Since Rasepi is in closed beta, please sign up first to get context on the roadmap and coordinate with the team.

When working on the block system or translations, keep these rules in mind:

Never break block-to-translation relationships
Always maintain blockId UUIDs across edits
Soft-delete blocks when translations exist — never hard-delete
License
MIT © Rasepi Contributors

<div align="center">

Website · Developer Docs · Sign Up for Beta

</div>

