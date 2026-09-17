# Finance (Staging)

Staging copy of the [`finance`](https://github.com/cursor/plugins/tree/main/third_party/finance)
plugin from `cursor/plugins`. It is identical to upstream except that the MCP
server URL points at the xAI **staging** connectors gateway. It exists so the
connectors team can exercise the Grok Finance connector from Grok Bot against a
staging Cursor backend without touching production data.

Not a distribution channel. End users install `finance` from `cursor-public`.

## Who can use it

- Grok Bot **0.49** or newer.
- Not available in Cursor. Cursor must not list or install this plugin.
- Connectors-team members whose Cursor backend is configured for the xAI
  staging gateway. Against any other backend the server rejects the dial.

## MCP

```json
{
  "mcpServers": {
    "finance": {
      "type": "http",
      "url": "https://connectors-gateway.grok.gcp.mouseion.dev/gateway/v1/finance/mcp"
    }
  }
}
```

The server is hosted by xAI and authenticates with the Grok account linked to
the caller. There is no sign-in prompt in the client: the Cursor backend
attaches the linked account's credential when it dials this URL. Until a bank
account is linked, the connector reports that it needs authorization.

## About this connector

- **See your finances in chat.** Ask about balances, recent spending, subscriptions, and investments across linked accounts.
- **Your credentials stay private.** xAI does not store or view any bank account or password credentials.
- **Read-only access.** A financial connection is read-only, which means it can't be used to move money into or out of bank accounts.

## License

MIT
