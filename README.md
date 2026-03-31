<div align="center">

# Rasepi

**Documentation you _and AI_ can actually trust.**

Multilingual-first collaborative documentation platform with freshness scoring, forced expiry, and a plugin-first architecture.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![.NET](https://img.shields.io/badge/.NET-10.0-purple)](https://dotnet.microsoft.com/)
[![Vue](https://img.shields.io/badge/Vue-3-brightgreen)](https://vuejs.org/)
[![Status](https://img.shields.io/badge/Status-Beta%20(Invite%20Only)-orange)](#-beta-notice)

</div>

---

> [!IMPORTANT]
> **Rasepi is currently in closed beta.** Access is invite-only. To get early access, sign up at **[rasepi.com/signup](https://rasepi.com/signup)**. We're onboarding users in waves — early signups get priority and a free extended trial at launch.

---

## Why Rasepi?

Your team writes great docs. But six months later, nobody knows if they're still correct — and your AI tools don't know either. They just serve whatever they find.

Rasepi fixes that:

- **Freshness scoring** — Every document earns a live trust score and gets flagged when it goes stale
- **Forced expiry** — Entries _must_ have an expiration date. Expired docs are hidden from search and AI until reviewed
- **Multilingual-first** — Block-level translation system that publishes to 40+ languages with 94% cost savings on partial updates
- **Plugin architecture** — Core handles docs and collaboration; everything else is a plugin

## Features

### 🌍 Block-Level Translation

Unlike full-page translation, Rasepi translates at the paragraph level. When you edit one paragraph, only that block is retranslated — not the entire document. A SHA256 content hash on each block detects staleness automatically.

### ⏰ Freshness & Expiry

Every entry has a configurable expiry (6 months, 1 year, etc.). Expired entries are hidden from search, moved to an "Expired" section, and require manual review before republication.

### ✏️ Real-Time Collaboration

Google Docs-style co-editing powered by SignalR, with per-language editing sessions so translators never conflict with original authors.

### 🔌 Plugin System

Build your own translation providers, export formats, integrations, and more:

```csharp
public interface ITranslationProviderPlugin : IRasepiPlugin
{
    Task<string> TranslateAsync(string content, string fromLang, string toLang);
    IEnumerable<string> SupportedLanguages { get; }
}
```

## Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | Vue 3, TypeScript, Vuetify 3, TipTap, Pinia |
| **Backend** | .NET 10, ASP.NET Core, Entity Framework Core |
| **Real-time** | SignalR |
| **Database** | SQL Server (prod) / InMemory (dev) |
| **Background Jobs** | Hangfire |
| **Auth** | OpenIddict (OpenID Connect) |
| **Logging** | Serilog + Seq |

## Getting Started

### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) & Docker Compose

### Quick Start

```bash
git clone https://github.com/RasepiHQ/rasepi.git
cd rasepi
docker compose up
```

This starts:

| Service | URL |
|---|---|
| **API** | `http://localhost:5000` |
| **Swagger** | `http://localhost:5000/swagger` |
| **Frontend** | `http://localhost:5173` |
| **SQL Server** | `localhost:1433` |
| **Redis** | `localhost:6379` |

> **Note:** SQL Server takes ~30s to initialize on first run. The API will auto-restart if it connects before the database is ready.

### Without Docker

**Backend:**

```bash
cd backend/Rasepi.Api
dotnet run
```

**Frontend:**

```bash
cd frontend
npm install
npm run dev
```

## Project Structure

```
rasepi/
├── backend/
│   ├── Rasepi.Api/            # ASP.NET Core Web API
│   ├── Rasepi.Shared/         # Shared models and DTOs
│   └── Rasepi.Plugins.SDK/    # Plugin development SDK
├── frontend/
│   └── src/
│       ├── components/        # Vue components
│       ├── extensions/        # TipTap editor extensions
│       ├── stores/            # Pinia state management
│       └── views/             # Page views
├── developers/                # Developer documentation site
├── docs/                      # Architecture docs & ADRs
└── docker-compose.yml         # Local dev environment
```

## Contributing

We welcome contributions! Since Rasepi is in closed beta, please [sign up at rasepi.com/signup](https://rasepi.com/signup) first to get context on the roadmap and coordinate with the team.

When working on the block system or translations, keep these rules in mind:

- Never break block-to-translation relationships
- Always maintain `blockId` UUIDs across edits
- Soft-delete blocks when translations exist — never hard-delete

## License

[MIT](LICENSE) © Rasepi Contributors

---

<div align="center">

**[Website](https://rasepi.com)** · **[Developer Docs](https://developers.rasepi.com)** · **[Sign Up for Beta](https://rasepi.com/signup)**

</div>
