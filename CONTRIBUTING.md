# Contributing to Vowena Docs

Thanks for helping improve the Vowena documentation. Clear docs are part of the product, not an afterthought, so we want contributions here to feel just as well supported as code contributions.

## Good contributions here

- Fixing incorrect or outdated instructions
- Expanding missing explanations
- Improving onboarding and quickstarts
- Clarifying API reference details
- Tightening copy, diagrams, or examples
- Improving navigation and information architecture

If you are unsure whether a change belongs here or in another repository, start with [SUPPORT.md](SUPPORT.md).

## Local setup

### Prerequisites

- Node.js 22 or later
- npm 10 or later

### Run locally

```bash
git clone https://github.com/vowena/docs.git
cd docs
npx mint dev
```

## Working with docs content

- Most pages are written in `.mdx`.
- Navigation, tabs, and site metadata live in `docs.json`.
- Keep headings descriptive and task-oriented.
- Prefer short examples that can actually be followed.
- When linking between pages, use stable routes and verify them with the broken-links check.

## Validation

Run both checks before pushing:

```bash
npx mint validate
npx mint broken-links --check-anchors --check-snippets
```

## Branch and commit conventions

Use focused branches such as:

- `docs/add-merchant-onboarding`
- `fix/sdk-installation-link`
- `docs/rewrite-protocol-overview`

Use [Conventional Commits](https://www.conventionalcommits.org/):

```text
docs: clarify keeper setup prerequisites
fix: correct protocol overview links
feat: add migration flow guide
```

## Pull requests

- Explain what changed and why.
- Link related issues when there are any.
- Mention navigation changes in `docs.json`.
- Include screenshots when layout or navigation changed.
- Keep one docs concern per PR whenever practical.

## Security

If a documentation issue could expose users to a real security problem, follow [SECURITY.md](SECURITY.md) instead of opening a public issue.

## Conduct

This repository follows [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).
