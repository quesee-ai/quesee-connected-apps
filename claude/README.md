# QueSee: Customer Experience, Churn Risk & Quality Scoring

Find out why customers call, chat, open tickets and cancel, which agents need coaching, and which customers are about to leave, by asking Claude about 100% of your customer interactions.

Most contact centers review fewer than 5% of their conversations by hand. QueSee joins every call, chat, ticket, order, bill and network signal into one record per customer, scores conversations against your own SOP, and flags who is about to leave, why in the customer's own words, and what to do next. This plugin brings that record into Claude: the QueSee connector gives Claude read-only access, and the skills turn it into the reports your team already needs.

**Built for:** contact center, customer support, quality assurance, CX and retention teams at broadband, telecom and other service providers.

## What you can ask

| You want to know | Ask Claude | Skill |
| - | - | - |
| How last week went | "Give me the weekly CX report for last week." | `cx-weekly-brief` |
| Who needs coaching, and on what | "Which agents skip the verification step in our SOP, and which calls should I review with them?" | `agent-coaching` |
| Who is about to cancel | "Which customers are at risk of churning this week, and what should we do for each one?" | `save-list` |
| Why customers call | "What are the top reasons customers called this month, and what changed from last month?" | `call-drivers` |
| Who customers are switching to | "Which competitors do customers mention, and why?" | `competitor-mentions` |
| Anything else | "How many calls were escalated last month, by department?" | `quesee-data` |

The `quesee-data` skill sets the rules for every answer: count over 100% of records, never estimate from a sample, and link every call and customer back to QueSee so you can check it.

## What's included

| Component | What it does |
| - | - |
| QueSee connector (`.mcp.json`) | Connects Claude to `https://api.quesee.ai/mcp` with three read-only tools: `quesee_schema`, `quesee_values` and `quesee_query` |
| `quesee-data` skill | How to query QueSee correctly: fields, limits, links, privacy and errors |
| `cx-weekly-brief` skill | A one-screen weekly customer experience report, with changes from last week |
| `agent-coaching` skill | Coaching plans per agent: the SOP steps they miss and the calls to review |
| `save-list` skill | A ranked list of customers at risk of churning, with reasons, open promises and next steps |
| `call-drivers` skill | Top call reasons and complaints, what changed, and the fix each team owns |
| `competitor-mentions` skill | Which competitors customers name, why, and who is deciding now |

The plugin contains only Markdown and JSON. It runs no code on your computer.

## Before you start

- You need a QueSee account with a manager or admin role.
- Connected apps are off by default. QueSee turns them on for your organization, and your admin picks who gets access in QueSee under **Settings > Connections > Connected apps**. To turn them on, or to start with QueSee, [contact QueSee](https://www.quesee.ai/contact).

## Set up

1. Add the QueSee plugin from the Claude directory.
2. Open the plugin's **Connectors** tab and connect QueSee.
3. Sign in to QueSee when asked, and select **Allow**.
4. Ask a question, such as "Which agents scored lowest last week?"

## Data and privacy

- **Read-only:** the connector can't change anything in QueSee.
- **What is sent:** Claude sends structured queries (fields, filters and date ranges) to `api.quesee.ai` over HTTPS, with OAuth sign-in. QueSee returns the matching results.
- **Redacted:** names, phone numbers, emails and addresses are replaced before results leave QueSee, and agents appear as labels such as "Agent 07". A name typed only inside a free-text note, with no matching customer or agent record, can come through.
- **Never sent:** recordings and transcripts.
- **Same view as in QueSee:** each person sees only the departments and flags they can see in QueSee.
- **Access you control:** access is turned on per person, can be turned off at any time, and ends after 90 days.
- **No other destinations:** the plugin sends data nowhere except QueSee and stores nothing itself.

[Connected Apps](https://www.quesee.ai/connected-apps) · [Privacy policy](https://www.quesee.ai/legal/privacy) · [Terms](https://www.quesee.ai/legal/terms) · [Security](https://www.quesee.ai/security)

## Limits

- Through this connector, Claude reads scored calls, customer records, assessments and events. Customer records reflect every source your organization connects to QueSee (calls, chats, tickets, billing, network). Individual chat and ticket scores aren't available through the connector yet.
- Rows come back up to 200 per page. The rows window is up to 92 days, and the aggregate window up to 366 days.
- Some fields and entities, such as assessments, exist only on some QueSee plans.

## Support

Questions or problems: [quesee.ai/contact](https://www.quesee.ai/contact).

## License

MIT. See [LICENSE](LICENSE).
