# Thmenu MCP Server (`com.thmenu/thmenu`)

Official Model Context Protocol (MCP) remote Streamable HTTP server for [Thmenu](https://thmenu.com) — the QR menu, table ordering, reservations, and restaurant operations platform by [Synaltix LLC](https://synaltix.io).

- **Remote MCP Endpoint (`streamable-http`):** `https://mcp.thmenu.com/`
- **MCP Registry ID:** `com.thmenu/thmenu`
- **Server Card:** [`https://thmenu.com/.well-known/mcp/server-card.json`](https://thmenu.com/.well-known/mcp/server-card.json)
- **OAuth Protected Resource Metadata (RFC 9728):** [`https://mcp.thmenu.com/.well-known/oauth-protected-resource`](https://mcp.thmenu.com/.well-known/oauth-protected-resource)
- **OAuth Authorization Server Metadata:** [`https://thmenu.com/.well-known/oauth-authorization-server`](https://thmenu.com/.well-known/oauth-authorization-server)
- **LLMs Documentation:** [`https://thmenu.com/llms.txt`](https://thmenu.com/llms.txt)
- **Glama Connector:** [`glama.ai/mcp/connectors/com.thmenu/thmenu`](https://glama.ai/mcp/connectors/com.thmenu/thmenu)

## Connect via Streamable HTTP

No local installation is required. Point any MCP-compatible client to `https://mcp.thmenu.com/`:

### Generic / Claude Desktop / Claude Connectors

```json
{
  "mcpServers": {
    "thmenu": {
      "url": "https://mcp.thmenu.com/"
    }
  }
}
```

### Cursor (`~/.cursor/mcp.json`)

```json
{
  "mcpServers": {
    "mcp-thmenu": {
      "url": "https://mcp.thmenu.com/"
    }
  }
}
```

### Quick JSON-RPC Check

```bash
curl -s -X POST https://mcp.thmenu.com/ \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json, text/event-stream' \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/list","params":{}}'
```

## Available Tools (27)

### Public Read & Discovery Tools (Anonymous)
- `get_pricing` — Structured commercial model (`Free forever`, platform fee only on online payments processed through Thmenu)
- `get_faq` — Multilingual `/faq` entries across supported locales
- `list_public_menus` — Public restaurant directory
- `search_restaurants` — Search public restaurant venues
- `get_restaurant` — Public restaurant profile, hours, channels, and menu metadata
- `get_restaurant_menu` — Structured menu items and categories for a restaurant slug
- `search_products` — Search menu items across public restaurants

### Guest Order, Cart, Reservation & Loyalty Tools
- `create_cart` — Build a cart and return a guest confirmation link
- `get_cart` — Retrieve cart contents
- `start_order_session` — Start an order session
- `place_order` — Place an OAuth-scoped order
- `cancel_order` — Cancel an order
- `get_order_status` — Query order status
- `request_bill` — Request the bill
- `waiter_call` — Send a waiter call request
- `get_reservation_slots` — Check reservation availability slots
- `request_reservation` — Submit a reservation request with guest confirmation link
- `cancel_reservation` — Cancel a reservation request
- `check_loyalty` — Check loyalty balance
- `join_loyalty` — Join a venue loyalty program
- `apply_promo` — Preview a promo code

### Owner Drafting & Operations Tools (OAuth)
- `menu_audit` — Menu completeness audit
- `sales_summary` — 7-day and 30-day order summaries
- `reservation_summary` — Upcoming reservation summary
- `draft_product_description` — Draft product descriptions as owner change sets
- `draft_site_text` — Draft website text packs
- `draft_translation` — Draft menu translations

## Support & Contact

- Website: https://thmenu.com
- Parent Company: https://synaltix.io
- Contact: contact@synaltix.io
