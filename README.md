# grok-connector-plugins-staging

Staging Cursor plugin marketplace for the Grok connector plugins that were
ported into [`cursor/plugins`](https://github.com/cursor/plugins). It exists so
the connectors team can install these plugins from a team- or user-scoped
marketplace on the production Cursor backend before, or right after, they land
in the public `cursor-public` marketplace.

This is not a distribution channel. Once a plugin is merged and listed
publicly, install it from `cursor-public` instead.

## Plugins

| Plugin | Upstream PR | Upstream state |
|---|---|---|
| `gamma` | cursor/plugins#347 | merged 2026-09-10 |
| `webull` | cursor/plugins#348 | merged 2026-09-10 |
| `sp-global` | cursor/plugins#349 | merged 2026-09-10 |
| `interactive-brokers` | cursor/plugins#350 | merged 2026-09-10 |
| `meltwater` | cursor/plugins#351 | merged 2026-09-10 |
| `daloopa` | cursor/plugins#352 | merged 2026-09-10 |
| `excalidraw` | cursor/plugins#353 | merged 2026-09-10 |
| `coinbase` | cursor/plugins#354 | open |
| `google-cloud-bigquery` | cursor/plugins#355 | merged 2026-09-12 |

Plugin folders are verbatim copies of the upstream `third_party/<name>/`
directories at the commit noted above. Re-copy from upstream when a PR changes.

## Using it

1. Cursor dashboard → Plugins → Marketplaces → import from repository, URL
   `https://github.com/minupalaniappan/grok-connector-plugins-staging`.
   Registering it for a team requires team admin (or the team's
   "allow third-party plugin imports" setting); registering it as a personal
   marketplace needs no special role.
2. Cursor Settings → Plugins → pick the plugin from this marketplace → install
   → complete the vendor sign-in.
3. `coinbase` needs `CLIENT_ID` / `CLIENT_SECRET` set under Dashboard → Plugins
   → Configure (Coinbase has no dynamic client registration).
4. `google-cloud-bigquery` sign-in depends on the Cursor backend running
   everysphere `d394e3cfc` or later (the `bigquery.googleapis.com` OAuth policy).

## Validation

```
npm install --no-save ajv ajv-formats
node scripts/validate-plugins.mjs
```
