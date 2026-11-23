# QueSee for Claude

Ask Claude about every scored customer call, every agent and every subscriber at risk of leaving, using your own QueSee data.

QueSee joins every customer call, account and network signal into one record per customer, scores each call against your own SOP, and flags who is about to leave, why, and what to do next. This plugin brings that record into Claude: the QueSee connector gives Claude read-only access, and the skills teach Claude how your team uses it.

## What you can ask

- "Give me the weekly CX brief for last week." (`cx-weekly-brief`)
- "Which agents need coaching this month, and on which SOP steps?" (`agent-coaching`)
- "Who might cancel this week, and what should we do for each one?" (`save-list`)
- "What drove calls this month, and what changed from last month?" (`call-drivers`)
- Any other question about your calls, scores, agents or subscribers. The `quesee-data` skill sets the query rules: count with aggregates over 100% of records, never estimate from a sample, and link every call and subscriber back to QueSee.

## What's included

| Component | What it does |
| - | - |
| QueSee connector (`.mcp.json`) | Connects Claude to `https://api.quesee.ai/mcp` with three read-only tools: `quesee_schema`, `quesee_values` and `quesee_query` |
| `quesee-data` skill | How to query QueSee correctly: fields, limits, links, privacy and errors |
| `cx-weekly-brief` skill | A one-screen weekly brief with changes from last week |
| `agent-coaching` skill | Coaching plans per agent, with the criteria they miss and calls to review |
| `save-list` skill | A ranked list of at-risk subscribers, with reasons, open promises and next steps |
| `call-drivers` skill | Why customers call, what changed, and the fixes by team |

The plugin contains only Markdown and JSON. It runs no code on your computer.

## Before you start

- You need a QueSee account with a manager or admin role.
- Connected apps are off by default. QueSee turns them on for your organization, and your admin picks who gets access in QueSee under **Settings > Connections > Connected apps**. To turn them on, [contact QueSee](https://www.quesee.ai/contact).

## Set up

1. Add the QueSee plugin from the Claude directory.
2. Open the plugin's **Connectors** tab and connect QueSee.
3. Sign in to QueSee when asked, and select **Allow**.
4. Ask a question, such as "Which agents scored lowest last week?"

## Data and privacy

- **Read-only:** the connector can't change anything in QueSee.
- **What is sent:** Claude sends structured queries (fields, filters and date ranges) to `api.quesee.ai` over HTTPS, with OAuth sign-in. QueSee returns the matching results.
- **What is redacted:** names, phone numbers, emails and addresses are replaced before results leave QueSee. Agents appear as labels such as "Agent 07". A name typed only inside a free-text note, with no matching customer or agent record, can come through.
- **Never sent:** recordings and transcripts.
- **Same view as in QueSee:** each person sees only the departments and flags they can see in QueSee.
- **Access you control:** access is turned on per person, can be turned off at any time, and ends after 90 days.
- **No other destinations:** the plugin sends data nowhere except QueSee and stores nothing itself.

[Connected Apps](https://www.quesee.ai/connected-apps) · [Privacy policy](https://www.quesee.ai/legal/privacy) · [Terms](https://www.quesee.ai/legal/terms) · [Security](https://www.quesee.ai/security)

## Limits

- The connector covers calls, customers, assessments and events. Chats and tickets aren't available through it.
- Rows come back up to 200 per page. The rows window is up to 92 days, and the aggregate window up to 366 days.
- Some fields and entities, such as assessments, exist only on some QueSee plans.

## Support

Questions or problems: [quesee.ai/contact](https://www.quesee.ai/contact).

## License

MIT. See [LICENSE](LICENSE).
