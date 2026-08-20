# Agility CMS MCP Server

The official MCP server for [Agility CMS](https://agilitycms.com): a hosted, remote server that gives
your AI tools real-time access to the content, models, pages and media in the Agility instances you
already have access to — through conversation, not APIs.

![Official Agility CMS server](https://img.shields.io/badge/Agility%20CMS-official%20MCP%20server-5B21B6?style=flat-square)
![Hosted — nothing to install](https://img.shields.io/badge/hosted-nothing%20to%20install-0EA5E9?style=flat-square)
![Transport: streamable HTTP](https://img.shields.io/badge/transport-streamable%20HTTP-111827?style=flat-square)
![Auth: OAuth 2.0](https://img.shields.io/badge/auth-OAuth%202.0-16A34A?style=flat-square)
![32 tools](https://img.shields.io/badge/tools-32-F59E0B?style=flat-square)
[![License: Apache 2.0](https://img.shields.io/badge/license-Apache%202.0-64748B?style=flat-square)](LICENSE)

[Connect your client](#connect-your-client) · [What you can ask for](#what-you-can-ask-for) ·
[Tools](#available-mcp-tools) · [Data and security](#data-and-security) ·
[Troubleshooting](#troubleshooting) · [Support](#support-and-feedback)

**There is nothing to install.** Point your client at `https://mcp.agilitycms.com/api/mcp`, sign in
with your Agility account, and your assistant can work with the instances you already have access to.

- **Endpoint:** `https://mcp.agilitycms.com/api/mcp` (streamable HTTP)
- **Auth:** OAuth 2.0 against your Agility organization — your Agility permissions are the authority
- **Tools:** 32, covering content, models, components, containers, pages, sitemaps and media
- **Setup guide with screenshots:** [mcp.agilitycms.com/instructions](https://mcp.agilitycms.com/instructions)
- **Live tool catalog:** [mcp.agilitycms.com/tools](https://mcp.agilitycms.com/tools)

---

## Connect your client

### One click

[![Install in VS Code](https://img.shields.io/badge/Install%20in-VS%20Code-007ACC?style=for-the-badge&logo=visual-studio-code&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=agility-cms&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.agilitycms.com%2Fapi%2Fmcp%22%7D)
[![Install in VS Code Insiders](https://img.shields.io/badge/Install%20in-VS%20Code%20Insiders-24B47E?style=for-the-badge&logo=visual-studio-code&logoColor=white)](https://insiders.vscode.dev/redirect/mcp/install?name=agility-cms&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp.agilitycms.com%2Fapi%2Fmcp%22%7D&quality=insiders)
[![Install in Cursor](https://img.shields.io/badge/Install%20in-Cursor-000000?style=for-the-badge&logo=cursor&logoColor=white)](https://cursor.com/en/install-mcp?name=agility-cms&config=eyJ1cmwiOiJodHRwczovL21jcC5hZ2lsaXR5Y21zLmNvbS9hcGkvbWNwIn0%3D)
[![Install in LM Studio](https://img.shields.io/badge/Install%20in-LM%20Studio-4F46E5?style=for-the-badge)](https://lmstudio.ai/install-mcp?name=agility-cms&config=eyJ1cmwiOiJodHRwczovL21jcC5hZ2lsaXR5Y21zLmNvbS9hcGkvbWNwIn0%3D)

### Every supported client

| Client | How to add it |
|---|---|
| **VS Code** (GitHub Copilot) | One-click badge above, or Command Palette → **MCP: Add Server** → **HTTP** |
| **Cursor** | One-click badge above, or Settings → **MCP** → **Add new MCP server** → **HTTP** |
| **LM Studio** | One-click badge above |
| **Claude Code** | `claude mcp add --transport http "Agility-CMS" https://mcp.agilitycms.com/api/mcp` |
| **Claude** (desktop & web) | Settings → **Connectors** → **Add custom connector** → paste the endpoint |
| **Windsurf** | Settings → **Cascade** → **MCP servers** → add the endpoint |
| **Gemini CLI** | `gemini mcp add --transport http agility-cms https://mcp.agilitycms.com/api/mcp` |
| **ChatGPT** | Settings → **Apps & Connectors** → **Advanced → Developer mode** → add a connector |
| **Anything else** | Any client that speaks streamable HTTP — or bridge a stdio-only client with [`mcp-remote`](#anything-else) |

Full walkthroughs with screenshots are at
[mcp.agilitycms.com/instructions](https://mcp.agilitycms.com/instructions). To wire anything up by
hand, the only value you need is the endpoint. Details per client follow.


### Claude Code

```bash
claude mcp add --transport http "Agility-CMS" https://mcp.agilitycms.com/api/mcp
```

### Claude (desktop & web)

Settings → Connectors → **Add custom connector**, then paste the endpoint:

```
https://mcp.agilitycms.com/api/mcp
```

### VS Code (GitHub Copilot)

Command Palette → **MCP: Add Server** → **HTTP**, then paste the endpoint. Or add to your MCP config:

```json
{
  "servers": {
    "agility-cms": {
      "type": "http",
      "url": "https://mcp.agilitycms.com/api/mcp"
    }
  }
}
```

### Cursor

Settings → **MCP** → **Add new MCP server** → type **HTTP**, URL as above. Or in `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "agility-cms": {
      "url": "https://mcp.agilitycms.com/api/mcp"
    }
  }
}
```

### LM Studio

Use the one-click badge above, or add the endpoint under **Program → Install → Edit mcp.json**:

```json
{
  "mcpServers": {
    "agility-cms": {
      "url": "https://mcp.agilitycms.com/api/mcp"
    }
  }
}
```

### Windsurf

Settings → **Cascade** → **MCP servers** → add a server with the endpoint above.

### Gemini CLI

```bash
gemini mcp add --transport http agility-cms https://mcp.agilitycms.com/api/mcp
```

Or in `~/.gemini/settings.json`:

```json
{
  "mcpServers": {
    "agility-cms": {
      "httpUrl": "https://mcp.agilitycms.com/api/mcp"
    }
  }
}
```

### ChatGPT

Settings → **Apps & Connectors** → **Advanced → Developer mode**, then add a connector with the
endpoint above.

### Anything else

Any client that speaks streamable HTTP works. Give it the endpoint and let it run the OAuth flow —
there is no API key to paste and nothing to keep in a config file.

If a client only supports local (stdio) servers, bridge to it with
[`mcp-remote`](https://www.npmjs.com/package/mcp-remote):

```json
{
  "mcpServers": {
    "agility-cms": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.agilitycms.com/api/mcp"]
    }
  }
}
```

That bridge is a general-purpose client-side shim, not an Agility package. **There is no
`agility-mcp-server` npm package and there won't be one** — a hosted HTTP server has nothing to
install, so if you find a config telling you to `npx` something Agility-named, it's wrong.

---

## What you can ask for

Once it's connected, talk to your assistant about your content — it will pick the tools. Most tools
take an `instanceGuid` (which Agility instance) and, for content, a `locale`; ask it to list your
instances first and it will use the right one from then on.

- *"List the Agility instances I can access, then show me the content models in the marketing site."*
- *"Add a `Subtitle` text field to the Blog Post model, under the existing SEO tab."*
- *"Build a Team Member model — name, photo, bio, and a link to their posts — and a container for it."*
- *"Create a blog post in `en-us` from this outline and give me the editor link."*
- *"Which pages in the main channel are still unpublished?"*
- *"Publish the three posts I just created."*

---

## Data and security

**Authentication is OAuth 2.0** against your Agility organization, over HTTPS. There is no API key to
paste and nothing to keep in a config file — tokens are held by your MCP client, not by this repo's
configuration or any file you edit.

**Your Agility permissions are the ceiling.** Every call runs as you: the Management API refuses
anything you personally can't do, so the server cannot exceed the access you already have. It follows
that the practical way to limit what an assistant can reach is to sign in as an Agility user that only
has the access you're willing to give it.

**Destructive actions are marked and prompted.** The `delete_*`, `unpublish_content` and
`unpublish_page` tools carry `destructiveHint: true`, so interactive clients ask before running them.
Non-interactive clients don't prompt at all — they require each write tool to be allow-listed instead.

**Treat content as untrusted input.** This is structural to MCP, not specific to Agility: an assistant
reads content items, page text and field descriptions, and any of that can contain text that reads like
an instruction (prompt injection). A client that acts on it does so with your permissions. Use clients
you trust, leave confirmation prompts on for destructive tools, and don't hand a broadly-privileged
Agility account to an unattended agent.

**What gets logged.** The hosted server records operational telemetry to Agility's Application
Insights: the tool or API method called, duration, success or failure, the Agility instance GUID and
your Agility user ID. Request and response payloads are recorded in truncated form for debugging
(capped, 2 KB by default), so small content values can appear in those logs. There is no client-side
opt-out on the hosted server; self-host without `APP_INSIGHTS_CONNECTION_STRING` to collect nothing.

---

## Available MCP Tools

The Agility CMS MCP Server provides **32 powerful tools** organized into categories:

### 🔍 Discovery Tools
- `get_available_instances` - List all Agility CMS instances you have access to
- `get_current_user` - Identify the user the current token authenticates as (read-only whoami)
- `get_containers` - Access content containers organized by category

### 📋 Model Listing Tools
- `get_content_models` - Retrieve all content models for an instance
- `get_component_models` - Access page component models

### 🔍 Detail Tools
- `get_content_model_details` - Get detailed field definitions for a content model
- `get_component_model_details` - Get detailed field definitions for a component model

### 📝 Content Management Tools
- `get_locales` - Retrieve available locales for multilingual content
- `get_content_items` - Fetch multiple content items with filtering and pagination
- `get_content_item` - Retrieve a single content item by ID
- `save_content_items` - Create or update content items (returns an editor URL per item)
- `publish_content` - Publish one or more content items
- `unpublish_content` - Unpublish (take offline) one or more content items *(destructive)*
- `manage_content_workflow` - Approve, decline, or request approval for content items
- `delete_content_item` - Delete content items *(destructive)*

### 📄 Page Management Tools
- `get_sitemaps` - List all digital channels (sitemaps)
- `get_sitemap` - Retrieve complete page hierarchy for a channel
- `get_page` - Retrieve a page by ID
- `get_page_models` - List available page models (templates)
- `save_page_model` - Create or update a page model (template) and its content zones
- `save_page` - Create or update a page
- `reorder_page_modules` - Reorder modules within a page zone
- `publish_page` - Publish one or more pages
- `unpublish_page` - Unpublish (take offline) one or more pages *(destructive)*
- `manage_page_workflow` - Approve, decline, or request approval for pages
- `delete_page` - Delete pages *(destructive)*

### 🖼️ Media & Asset Tools
- `initialize_media_upload` - Get signed upload URLs for media files
- `list_media` - List media library assets (paged)
- `delete_media` - Delete a media asset by ID *(destructive)*

### ⚡ Model Creation & Management Tools
- `save_content_model` - Create or update content models
- `save_component_model` - Create or update component models
- `save_container` - Create and configure content containers

> **🔒 Destructive actions are marked.** The `delete_*` tools and the `unpublish_content` / `unpublish_page` tools carry `destructiveHint: true`, so interactive MCP clients prompt before running them ("Allow this tool to run?" — choosing **"always allow"** opts out). Publish and the approval workflow are additive/reversible and are **not** flagged destructive. See [Data and security](#data-and-security) for how permissions and prompting work, and the [documentation](https://mcp.agilitycms.com/tools) for the per-tool detail.

**📚 Full tool documentation and examples:** [mcp.agilitycms.com/tools](https://mcp.agilitycms.com/tools)

## Supported Field Types

The Agility CMS MCP Server supports **20+ field types** for building comprehensive content models:

- **📝 Basic Fields**: Text, Long Text, HTML, Boolean, Integer, Decimal, Date
- **🎯 Selection Fields**: Dropdown List, Link, Search Listbox, Checkboxes
- **🎨 Media Fields**: Image Attachment, File Attachment
- **🔗 Content Relationships**: Shared Grid/Link, Nested Grid/Link
- **📂 Organization**: Tab Field, Custom Section
- **⚡ Advanced**: Complex Object Fields, Custom Field Types, Rich Text Editor

**📚 Complete field type documentation:** [mcp.agilitycms.com/tools](https://mcp.agilitycms.com/tools)

---

## Troubleshooting

| Symptom | Usually means |
|---|---|
| An instance is missing from `get_available_instances` | Your Agility user doesn't have access to it, or it isn't on the production Agility tenant this server talks to. |
| Calls start failing with an authorization error | The OAuth token expired or was revoked — reconnect the server in your client. |
| The assistant says it can't write, or silently only reads | Non-interactive clients require each write tool to be allow-listed by name. Check your client's tool permissions. |
| A one-click install link does nothing | The editor wasn't running, or it blocked the handoff — add the endpoint by hand instead. |
| A tool rejects a field setting | Agility validates model changes server-side; the error text is passed through verbatim. Linked-content fields, for example, have no `required`, `unique` or `copyAcrossAllLanguages` setting. |

Still stuck: [support@agilitycms.com](mailto:support@agilitycms.com) or
[our Slack community](https://agilitycms.com/join-slack).

---

## Support and feedback

- 🌐 **Website**: [mcp.agilitycms.com](https://mcp.agilitycms.com)
- 📖 **Setup Instructions**: [mcp.agilitycms.com/instructions](https://mcp.agilitycms.com/instructions)
- 🛠️ **Tool Catalog**: [mcp.agilitycms.com/tools](https://mcp.agilitycms.com/tools)
- 📚 **Agility CMS Docs**: [agilitycms.com/docs](https://agilitycms.com/docs)
- 💬 **Support**: [support@agilitycms.com](mailto:support@agilitycms.com)
- 👥 **Community**: [Join our Slack](https://agilitycms.com/join-slack)

## About this repository

This repository is the public home of the **Agility CMS MCP Server** — the documentation, the licence
and the security policy for the hosted service at `https://mcp.agilitycms.com`.

The server is a hosted, remote MCP server: there is nothing to install and no package to pull, so
there is no build to reproduce here. Its source is maintained by Agility CMS and is not currently
published. Everything you need in order to *use* the server is above.

## License

The documentation in this repository is licensed under the [Apache License 2.0](LICENSE).

Two things that licence deliberately does **not** cover:

- **The hosted service.** `https://mcp.agilitycms.com` is operated by Agility CMS under Agility's own
  terms of service. Your use of the service, and of the Agility CMS Management API behind it, is
  governed by those terms and your Agility subscription.
- **The Agility name and marks.** Apache 2.0 §6 grants no trademark rights. See [NOTICE](NOTICE).

Security reports: [SECURITY.md](SECURITY.md).

---

**Built with ❤️ by [Agility CMS](https://agilitycms.com)** — The fastest headless CMS for developers and marketers
