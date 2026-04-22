<p align="center">
  <a href="https://docs.vowena.xyz">
    <img src="./.github/banner.svg" alt="Vowena Docs" width="100%" />
  </a>
</p>

<p align="center">
  The canonical reference for the Vowena protocol, SDK, and dashboard.
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-CC%20BY%204.0-6B4EFF.svg?style=flat-square&labelColor=0F0F16" alt="License: CC BY 4.0" /></a>
  <a href="https://github.com/vowena/docs/actions/workflows/ci.yml"><img src="https://img.shields.io/github/actions/workflow/status/vowena/docs/ci.yml?branch=main&style=flat-square&label=ci&labelColor=0F0F16&color=6B4EFF" alt="CI" /></a>
  <a href="https://mintlify.com"><img src="https://img.shields.io/badge/built%20with-Mintlify-6B4EFF.svg?style=flat-square&labelColor=0F0F16" alt="Built with Mintlify" /></a>
  <a href="https://docs.vowena.xyz"><img src="https://img.shields.io/badge/live-docs.vowena.xyz-6B4EFF.svg?style=flat-square&labelColor=0F0F16" alt="docs.vowena.xyz" /></a>
</p>

<p align="center">
  <a href="https://docs.vowena.xyz"><b>Live site</b></a>
  &nbsp;·&nbsp;
  <a href="#sections">Sections</a>
  &nbsp;·&nbsp;
  <a href="#local-development">Local development</a>
  &nbsp;·&nbsp;
  <a href="#writing-docs">Writing docs</a>
  &nbsp;·&nbsp;
  <a href="#related-projects">Related projects</a>
</p>

<br />

## What is this?

This repository is the source of truth for [docs.vowena.xyz](https://docs.vowena.xyz), the official Vowena documentation site. Every protocol concept, contract method, SDK helper, dashboard guide, and operational runbook lives here as MDX. The site is built with [Mintlify](https://mintlify.com) and deploys automatically on push to `main`.

If you are integrating Vowena, start at the [live docs](https://docs.vowena.xyz). If you want to fix a typo, clarify a paragraph, or contribute a new guide, you are in the right place.

> **Live at** [docs.vowena.xyz](https://docs.vowena.xyz)

## Sections

| Section | First-level pages |
| --- | --- |
| **Getting Started** | [Introduction](index.mdx) · [Quickstart](quickstart.mdx) · [Concepts](concepts.mdx) |
| **How It Works** | [End-to-end flow](how-it-works.mdx) |
| **FAQ** | [Frequently asked questions](faq.mdx) |
| **Protocol** | [Overview](protocol/overview.mdx) · [Projects](protocol/projects.mdx) · [Plans](protocol/plans.mdx) · [Subscriptions](protocol/subscriptions.mdx) · [Billing](protocol/billing.mdx) · [Migrations](protocol/migrations.mdx) · [Refunds](protocol/refunds.mdx) · [Security](protocol/security.mdx) · [Deployment](protocol/deployment.mdx) |
| **SDK** | [Installation](sdk/installation.mdx) · [Client](sdk/client.mdx) · [Embed](sdk/embed.mdx) · [Amounts](sdk/amounts.mdx) · [Events](sdk/events.mdx) · [Keeper](sdk/keeper.mdx) |
| **API Reference** | [Introduction](api-reference/introduction.mdx) · [`initialize`](api-reference/initialize.mdx) · [`create_project`](api-reference/create-project.mdx) · [`create_plan`](api-reference/create-plan.mdx) · [`subscribe`](api-reference/subscribe.mdx) · [`charge`](api-reference/charge.mdx) · [`cancel`](api-reference/cancel.mdx) · [`refund`](api-reference/refund.mdx) · [`update_plan_amount`](api-reference/update-plan-amount.mdx) · [`reactivate`](api-reference/reactivate.mdx) · [`request_migration`](api-reference/request-migration.mdx) · [`accept_migration`](api-reference/accept-migration.mdx) · [`reject_migration`](api-reference/reject-migration.mdx) · [`extend_ttl`](api-reference/extend-ttl.mdx) · [`get_*` read-only methods](api-reference/get-plan.mdx) |
| **Dashboard** | [Overview](dashboard/overview.mdx) · [Merchant guide](dashboard/merchant-guide.mdx) · [Subscriber guide](dashboard/subscriber-guide.mdx) · [Keeper setup](dashboard/keeper-setup.mdx) |

Tab order, groups, and page ordering are defined in [`docs.json`](docs.json).

## Local development

### Prerequisites

| Tool | Version |
| --- | --- |
| Node.js | 22 or later |
| npm | 10 or later |

### Run the docs site

```bash
git clone https://github.com/vowena/docs.git
cd docs
npx mint dev
```

The Mintlify CLI prints a local preview URL (typically [http://localhost:3000](http://localhost:3000)) and hot-reloads on every save. The first run installs `mint` on demand; subsequent runs are instant.

### Validate before opening a PR

```bash
npx mint validate
npx mint broken-links --check-anchors --check-snippets
```

CI runs the same checks on every pull request and blocks merge on failure.

## Writing docs

### File structure

Every page is an MDX file colocated by section. The path on disk maps directly to the URL: `protocol/billing.mdx` becomes `/protocol/billing` on the live site.

```
.
├── index.mdx              Top-level landing
├── quickstart.mdx         Five-minute integration
├── concepts.mdx           Core mental model
├── how-it-works.mdx       End-to-end flow
├── faq.mdx                Frequently asked questions
├── protocol/              Smart contract concepts
├── sdk/                   TypeScript SDK guides
├── api-reference/         One file per contract method
├── dashboard/             Merchant, subscriber, keeper guides
├── logo/                  Mintlify-served brand marks
├── favicon.svg            Browser tab icon
└── docs.json              Site config and navigation
```

### Frontmatter

Every page begins with YAML frontmatter. Keep titles short and descriptions one sentence.

```mdx
---
title: "Subscriptions"
description: "How recurring billing works at the contract level."
---
```

### Navigation

To add or reorder pages, edit the `navigation.tabs` array in [`docs.json`](docs.json). Pages are referenced without the `.mdx` extension and are grouped under labelled sections.

```json
{
  "group": "Architecture",
  "pages": [
    "protocol/overview",
    "protocol/projects",
    "protocol/plans"
  ]
}
```

### Mintlify components

Reach for a component when it makes the page clearer, not for decoration. The ones used most in this repo:

| Component | Use it for |
| --- | --- |
| `<Note>`, `<Tip>`, `<Warning>` | Inline callouts |
| `<Steps>` | Multi-step procedures |
| `<CodeGroup>` | The same example across multiple languages |
| `<Card>`, `<CardGroup>` | Visual entry points on landing pages |
| `<Accordion>`, `<AccordionGroup>` | Long FAQs and collapsible details |
| `<Tabs>` | Mutually exclusive content variants |
| `<ParamField>`, `<ResponseField>` | API reference parameter tables |

### Code samples

- Default to TypeScript for SDK examples; default to Rust for protocol-level snippets.
- Use `bash` for shell commands and `json` for config snippets.
- Strings, addresses, and contract IDs go in monospace inline code (\`like this\`).
- Real-looking placeholder values are preferred over `<your-value-here>` style. Use `C...` for contract IDs and `G...` for Stellar addresses.
- Prefix shell commands with `$` only when output is shown on the next line.
- Code blocks may be titled with `title="..."` and highlighted with `{lines}`.

### Voice

Vowena docs are technical, restrained, and direct. The full guide lives in [BRAND.md](https://github.com/vowena/dashboard/blob/main/BRAND.md). In short:

- **Confident, not arrogant.** "The first subscription protocol on Stellar," not "revolutionary game-changing platform."
- **Technical, not jargon-heavy.** "Authorize recurring USDC transfers," not "leverage blockchain-powered payment automation."
- **Actionable, not descriptive.** Button label "Create plan," not "Get started with plan creation."

## Related projects

| Repository | What it is |
| --- | --- |
| [vowena/protocol](https://github.com/vowena/protocol) | Soroban smart contract source |
| [vowena/sdk](https://github.com/vowena/sdk) | TypeScript SDK published to npm as `@vowena/sdk` |
| [vowena/dashboard](https://github.com/vowena/dashboard) | Merchant and subscriber dashboard at `dashboard.vowena.xyz` |
| [vowena/site](https://github.com/vowena/site) | Marketing site at `vowena.xyz` |

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request. Documentation issues, typo fixes, and clarifications are all welcome. Security reports go through [SECURITY.md](SECURITY.md).

## License

Documentation in this repository is licensed under [CC BY 4.0](LICENSE). You may share and adapt the material for any purpose, with attribution.

<br />

<p align="center">
  <sub>Built by the Vowena team. <a href="https://vowena.xyz">vowena.xyz</a></sub>
</p>
