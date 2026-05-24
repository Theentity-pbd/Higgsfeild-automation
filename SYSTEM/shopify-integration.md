# Shopify Integration

This document describes the Shopify connection state for this repository, the local authentication flow, and the CLI setup used for store commands.

## Current Connected Store

- `fzb3tj-ts.myshopify.com`
- Connected via Shopify CLI auth using the current local machine session
- Verified with a successful GraphQL query:
  - `shop.name`: `PBD London`
  - `shop.myshopifyDomain`: `fzb3tj-ts.myshopify.com`

## Local config file

The repository stores the current Shopify connection metadata in a local file:

- `.shopify-store.json`

This file is intentionally ignored by git through `.gitignore`.

Example local config:

```json
{
  "store": "fzb3tj-ts.myshopify.com",
  "scopes": [
    "read_products",
    "read_orders",
    "read_themes"
  ],
  "connectedAt": "2026-05-24T00:45:47.508Z",
  "note": "Local Shopify CLI store connection config. This file is ignored by git to keep auth state local."
}
```

## Shopify CLI setup

The repository uses Shopify CLI commands via `npx`, so a global install is not required.

Install Shopify CLI locally with npm if needed:

```bash
npm install -g @shopify/cli
```

Verify the CLI is available:

```bash
npx --yes @shopify/cli version
```

## Authentication steps

1. In the repo root terminal, log in to Shopify account:

```bash
npx --yes @shopify/cli auth login
```

2. Follow the browser-based verification prompt.
   - The CLI opens a login page.
   - Enter the verification code shown in the terminal if required.

3. Authenticate the target store against the CLI app:

```bash
npx --yes @shopify/cli store auth -s fzb3tj-ts.myshopify.com --scopes read_products,read_orders,read_themes
```

4. Confirm the store connection with a GraphQL query:

```bash
npx --yes @shopify/cli store execute -s fzb3tj-ts.myshopify.com --query '{ shop { name myshopifyDomain email } }'
```

## Recommended scopes

The current connection uses safe read-only scopes:

- `read_products`
- `read_orders`
- `read_themes`

If the project later needs write access, request additional scopes intentionally and update this file accordingly.

## Reuse guide

To reuse the existing store connection in future development or monetization work:

- Keep `.shopify-store.json` in the repo root
- Do not commit it to source control
- Run CLI commands from the repo root using the verified store domain

Example:

```bash
npx --yes @shopify/cli store execute -s fzb3tj-ts.myshopify.com --query '{ shop { name myshopifyDomain } }'
```

## Monetization / future automation notes

- This repo currently has a local CLI-authenticated connection, not a shared API key file.
- For future monetization workflows, preserve the local auth metadata and use it as the source of truth for the active connected store.
- If you need a reusable automation setup later, create a dedicated Shopify app and store the resulting `API key` / `Admin API token` in a secure secret manager instead of in the repo.
