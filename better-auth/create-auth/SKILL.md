---
name: create-auth
description: Create or integrate Better Auth for TypeScript/JavaScript apps.
---

# Create an auth layer for TypeScript/JavaScript apps

## Overview

Use this skill when a user wants authentication and authorization in a new or existing TypeScript/JavaScript app.

## When to use

- The app has no auth and needs a fresh Better Auth setup
- The app has auth but needs fixes, upgrades, or new flows
- The user wants guidance on choosing framework, database, or auth strategy

## Inputs to gather

- Project type: new or existing
- Framework: React, Next.js, Express, etc.
- Database: PostgreSQL, MySQL, SQLite, MongoDB, etc.
- Auth needs: email/password, OAuth, magic links, orgs, admin roles, JWT, etc.
- Deployment base URL and environment constraints

## Steps

1. Determine if the project is new or existing.
2. If new, scaffold the project and select framework + database.
3. If existing, review current auth and identify gaps.
4. Configure Better Auth using the appropriate adapter and plugins.
5. Implement server auth config and client auth client.
6. Validate the flows (login, logout, session, provider callbacks).

## Example: Next.js app with Better Auth

Reference implementation:
- https://github.com/better-auth/examples/tree/main/nextjs-mcp

Key files:

```ts
import { betterAuth } from "better-auth";
import Database from "better-sqlite3";

export const auth = betterAuth({
  database: new Database("./auth.db"),
  baseURL: "http://localhost:3000",
  plugins: [],
  emailAndPassword: {
    enabled: true,
  },
});
```

```ts
import { createAuthClient } from "better-auth/react";

export const authClient = createAuthClient();
```

Add plugins via `better-auth/plugins`, and ensure client-side plugins are also configured.

## Dependencies

Install if missing:

```bash
npm install better-auth
```

## References

- https://www.better-auth.com/docs/concepts/plugins
- https://www.better-auth.com/docs/concepts/cli
- https://github.com/better-auth/examples
