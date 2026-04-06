# Vowena Docs

Product, protocol, dashboard, and SDK documentation for Vowena.

[![License](https://img.shields.io/badge/license-CC%20BY%204.0-lightgrey.svg)](LICENSE)
[![CI](https://github.com/vowena/docs/actions/workflows/ci.yml/badge.svg)](https://github.com/vowena/docs/actions/workflows/ci.yml)
[![Docs](https://img.shields.io/badge/docs-mintlify-blue.svg)](https://docs.vowena.xyz)

## What is this?

This repository contains the source for the Vowena documentation site. It covers protocol concepts, contract methods, dashboard guides, SDK guides, quickstarts, and operational documentation.

## Stack

- Mintlify
- MDX
- `docs.json` for navigation, metadata, and site configuration

## Local development

### Prerequisites

- Node.js 22 or later
- npm 10 or later

### Preview locally

```bash
git clone https://github.com/vowena/docs.git
cd docs
npx mint dev
```

Mintlify will print the local preview URL when the docs server starts.

## Quality checks

Run these before you open a PR:

```bash
npx mint validate
npx mint broken-links --check-anchors --check-snippets
```

## Repository structure

- `index.mdx`, `quickstart.mdx`, `faq.mdx`: top-level documentation pages
- `protocol/`: contract and billing concepts
- `sdk/`: SDK installation and API usage
- `dashboard/`: operator guides
- `api-reference/`: method-by-method references
- `docs.json`: navigation and site settings

## Contributing

Please read [CONTRIBUTING.md](CONTRIBUTING.md) before editing docs or navigation.

## License

Documentation in this repository is licensed under [CC BY 4.0](LICENSE).
