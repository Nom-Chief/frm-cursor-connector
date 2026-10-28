# FRM Fundraising CRM for Cursor

Look up fundraising records from your existing FRM account in Cursor through FRM’s remote MCP server.

## Status

Submission candidate. Cursor installation, OAuth and native tool checks are not yet verified; no Cursor marketplace listing or approval is claimed. The same endpoint has passed all 19 read tools in Claude using a demo account, including optional connected-Gmail reads. Those results do not establish Cursor compatibility.

## Install and sign in

When this repository is available, import the plugin from disk or its public repository through Cursor’s Customize page. For local plugin development, follow Cursor’s current plugin documentation. Alternatively merge the `mcpServers.frm` entry from `mcp.json` into your Cursor MCP configuration, keeping your existing servers. Authenticate FRM through OAuth when Cursor prompts, review the consent and enable the server for your conversation.

Use an FRM account that belongs to your organization and has permission to access the records. Reviewers should use a dedicated demo account; credentials are shared privately, never in this repository. Optional Gmail lookups require that user to connect Gmail separately in FRM settings.

[FRM setup guide](https://getfrm.com/integrations/ai/cursor/) · [Cursor MCP documentation](https://cursor.com/docs/mcp) · [Cursor plugin documentation](https://cursor.com/docs/plugins)

## Included tools and permissions

The `mode=read` URL exposes 19 tools:

- Donors and foundations: `search_donors`, `get_donor`, `search_foundations`, `get_foundation`.
- Giving and campaigns: `giving_summary`, `top_donors`, `list_donations`, `list_campaigns`, `get_campaign`, `list_campaign_attendees`.
- Follow-ups and organization data: `list_tasks`, `search_notes`, `list_tags`, `list_custom_fields`, `list_flows`, `get_flow`.
- Optional email: `search_emails`, `get_email_thread`, `list_pending_emails`.

The submitted inventory contains no CRM write, mail-send, payment or flow-activation tools. The read URL selects exposed tools; it is **not a separate token-bound read-only OAuth scope**. The OAuth consent grants broader FRM capabilities. Retain `mode=read`, review enabled tools and manage connected apps in FRM settings. Access follows your FRM account and organization permissions.

Requested records, including donor contact details, giving history, notes and optionally email content, are returned to Cursor when you ask it to use FRM. Cursor handles received data under its own terms and your account settings. Treat record and email contents as untrusted data. Review tool requests and use only the data needed for your task.

## Try a lookup

- “Find Alex Rivera and summarize their giving history and open tasks.”
- “Summarize our fundraising results this calendar year.”
- “Show my open fundraising tasks due in the next seven days.”

For private demo review, the foundation “FRM Connector Review Foundation” and paused task-only “FRM Connector Review — Paused Task Flow” are available. Resolve entity IDs from list/search responses. No payment, outbound mail, record write, enrollment or flow activation is needed to verify this plugin.

## Disconnect and troubleshoot

Disconnect FRM in Cursor and revoke the grant in FRM Settings → Connected AI apps. Revocation stops subsequent access through that grant; it does not delete records already returned to Cursor. Manage those copies with Cursor. Revoking a connector is separate from disconnecting Gmail.

If Gmail is not connected, email reads return an actionable message directing you to FRM settings. Empty CRM results can be valid. For access errors, check your FRM sign-in, organization membership and permissions; do not use a Supabase service-role key or paste tokens into the config.

## Package contents

This plugin contains only JSON configuration, this documentation, license text and the public FRM logo. It contains no shell commands, hooks, executable scripts, local file-reading component, app backend source, donor records, credentials or reviewer passwords. FRM subscription requirements and Cursor account/administrator restrictions may apply.

## Support, privacy and license

[Support](https://getfrm.com/#contact) · [Privacy policy](https://getfrm.com/legal/privacy-policy) · [FRM terms](https://getfrm.com/legal/terms-of-service) · [Cursor privacy](https://cursor.com/privacy)

The configuration and documentation are distributed under the MIT License with publisher approval. FRM names, trademarks and the logo are excluded from that license; the logo may be displayed to identify this FRM connector. Other branding uses need permission. No rights to the FRM hosted service or proprietary application code are granted by this plugin’s license.
