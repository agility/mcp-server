# Security policy

## Reporting a vulnerability

Please report security issues privately — in this repository's **Security → Report a
vulnerability** tab if it is enabled, otherwise by email to
[support@agilitycms.com](mailto:support@agilitycms.com) with `SECURITY` in the subject.

Please don't open a public issue for anything exploitable, and please don't test against
an Agility instance you don't own.

Include what you did, what happened, and what you expected. If it involves the hosted
server, the approximate time of the request helps us find it in our logs.

## What's in scope

- The source in this repository.
- The hosted server at `https://mcp.agilitycms.com` (endpoint `/api/mcp`).

The Agility CMS Management API and the Agility application itself are separate products;
report issues in those the same way and we'll route them.

## How the security model works

Worth knowing before you report, because these are deliberate:

- **Your Agility account permissions are the ceiling.** Every call runs as the
  authenticated user, and the Management API refuses anything that user can't do. The
  server holds no elevated credentials it can act with on your behalf.
- **Tokens live in your MCP client, not here.** Authentication is OAuth 2.0 against your
  Agility organization; this repository's configuration stores no customer tokens.
- **An MCP client can act with your permissions, and content is untrusted input.** Content
  items and field descriptions can contain text that reads like an instruction (prompt
  injection). That's structural to MCP. Reports showing a *privilege boundary* being
  crossed — one user reaching another's data, or a call succeeding that the Management API
  should have refused — are the ones we treat as vulnerabilities.

## Disclosure

Tell us before you tell anyone else, and give us a chance to ship a fix. We'll confirm
receipt, keep you posted, and credit you when the fix ships if you'd like us to.
