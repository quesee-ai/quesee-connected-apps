# QueSee Connected Apps

Ask your AI assistant why customers call, chat and cancel, and which subscribers are at risk of leaving, using your own QueSee data.

QueSee joins every customer call, account and network signal into one record per customer, scores each call against your own SOP, and flags who is about to leave, why, and what to do next. Connected Apps brings that record into the assistant your team already uses, through one read-only connector.

## Connector

| | |
| - | - |
| URL | `https://api.quesee.ai/mcp` |
| Protocol | Remote MCP over HTTPS |
| Sign-in | OAuth with your QueSee account |
| Access | Read-only |
| Tools | `quesee_schema`, `quesee_values`, `quesee_query` |

## By assistant

| Assistant | What's here |
| - | - |
| Claude | [`claude/`](claude): a plugin that bundles the connector with skills for weekly CX briefs, team coaching, save lists, call drivers and competitor mentions |
| Other assistants that support MCP connectors with sign-in | Add `https://api.quesee.ai/mcp` as a custom connector, sign in to QueSee, and select **Allow** |

## Before you start

- You need a QueSee account with a manager or admin role.
- Connected apps are off by default. QueSee turns them on for your organization, and your admin picks who gets access in QueSee under **Settings > Connections > Connected apps**. To turn them on, [contact QueSee](https://www.quesee.ai/contact).

## Data and privacy

- **Read-only:** the connector can't change anything in QueSee.
- **What is redacted:** names, phone numbers, emails and addresses are replaced before results leave QueSee. Agents appear as labels such as "Agent 07".
- **Never sent:** recordings and transcripts.
- **Same view as in QueSee:** each person sees only the departments and flags they can see in QueSee.
- **Access you control:** access is turned on per person, can be turned off at any time, and ends after 90 days.

[Connected Apps](https://www.quesee.ai/connected-apps) · [Privacy policy](https://www.quesee.ai/legal/privacy) · [Terms](https://www.quesee.ai/legal/terms) · [Security](https://www.quesee.ai/security) · [Contact](https://www.quesee.ai/contact)

## License

MIT. See [LICENSE](LICENSE).
