# Agility CMS plugin for Claude

Work with your Agility CMS content from Claude: find and edit content, write articles in your brand
voice, build pages, publish when you say so, audit SEO, migrate content in, and wire up a front end.

## What it includes

- **The Agility CMS MCP server** at `https://mcp.agilitycms.com/api/mcp`, Agility's official hosted
  server. You sign in with your Agility account (OAuth). Every call runs with your own Agility
  permissions, so the plugin can do only what your account can do in the Agility Content Manager.
- **The Agility Knowledgebase MCP server** at `https://docs.agilitycms.com/docs/api/mcp`, a public,
  read-only search of the Agility documentation, so answers about how Agility works come from the docs.
  It needs no sign-in.
- **Skills** that teach Claude how to use those tools safely and well:

| Skill | Use it to |
|---|---|
| `get-started` | Connect, pick an instance and locale, and see what's in it |
| `edit-content` | Find, create, update and translate content items |
| `write-article` | Write a blog post or article end to end, with author, tags, image and SEO |
| `brand-voice` | Write or review copy against your brand guidelines |
| `publish-and-workflow` | Publish, unpublish, approve or delete, only when you ask |
| `build-pages` | Explore the page tree, create pages and place components |
| `content-modeling` | Explain or change content models, components and containers |
| `go-live-check` | Find out why content or a page isn't showing on the live site |
| `build-frontend` | Fetch and render Agility content in a website, with preview and live editing |

## How to use it

Install the plugin, connect Agility CMS when Claude asks, then ask in plain language, for example
"draft a blog post about our spring launch" or "explain how the Product model is structured".

## What it sends and where

The skills are instructions only; the plugin runs no scripts and installs nothing. Claude sends your
requests to the Agility CMS MCP server, which calls the Agility Management API on your behalf, and sends
documentation search queries to the Agility Knowledgebase MCP server. No data goes anywhere else. Saving creates drafts; nothing is published, unpublished or deleted unless you ask.

## Support

- Documentation: https://mcp.agilitycms.com
- Support: https://agilitycms.com/docs/support
- Privacy policy: https://agilitycms.com/privacy-policy

This plugin is published from [agility/mcp-server](https://github.com/agility/mcp-server). It is
generated from Agility's source repository, so changes made directly in that repository are
overwritten on the next release.

Licensed under Apache-2.0.
