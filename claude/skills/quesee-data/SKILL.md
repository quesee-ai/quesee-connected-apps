---
name: quesee-data
description: How to answer questions from QueSee data with the QueSee connector tools (quesee_schema, quesee_values, quesee_query). Use whenever the user asks about their customer calls, call scores, SOP compliance, agents, subscribers, churn risk, retention, cancellations or competitors, and the QueSee connector is connected.
---

# Answering from QueSee data

QueSee scores every customer call against the organization's own standard (its SOP) and keeps one record per subscriber with churn risk, reasons and history. The QueSee connector gives read-only access to that data through three tools:

- `quesee_schema`: the fields, this organization's exact values, the dates covered, the user's access scope and the query limits
- `quesee_values`: the values a field takes, with counts
- `quesee_query`: rows or aggregates over calls, customers, assessments or events

## Before the first query

1. Call `quesee_schema` once per conversation. Fields and values differ by organization and by plan, and some entities (assessments, some customer fields) exist only on some plans. Use the field names and values it returns, not guesses.
2. When you need an exact value to filter on (a call type, a department, a retention outcome), get it from `quesee_values` instead of typing it from the user's words.
3. `references/fields.md` lists the fields most questions need. Read it when you plan a query.

## Counting and reading

- **Count with aggregate mode.** Aggregate mode covers every record in the range. Never estimate a total from a page of rows.
- **Read with rows mode.** Use rows for examples, reasons and quotes. Rows come up to 200 per page, so use `cursor` to read further pages when the question needs more than one.
- **Respect the date limits.** The rows window is up to 92 days and the aggregate window up to 366 days. For a longer period, split it.
- **Group by at most 2 fields**, or by `time:day`, `time:week` or `time:month` for a trend.
- **Compare like with like.** A week is compared with the week before, and a month with the month before.

## What to show

- Lead with the answer and the numbers, then the table, then what to do next.
- State the date range you used.
- Give the call or customer id and its `quesee_url` link for every call or subscriber you cite, so the user can open it in QueSee and check it.
- If a result says it came from cache, say so.

## Privacy and scope

- Names, phone numbers, emails and addresses are replaced before data leaves QueSee. Agents appear as labels such as "Agent 07". Report ids and labels as they come, and don't try to work out who a person is.
- The user sees only the departments and flags they can see in QueSee.
- The connector covers calls, customers, assessments and events. Chats and tickets aren't available through it.
- It is read-only. If the user asks to change a scorecard, a flag or a setting, tell them where to do it in the QueSee app.

## When something fails

- **"Connected apps are not enabled for your organization"**: QueSee turns Connected apps on for the organization, and an admin then picks who gets access in QueSee under Settings > Connections > Connected apps. Access is for managers and admins.
- **A field or value is rejected**: the error lists the valid options. Retry with one of them.
- **A query times out**: shorten the time range or ask for fewer fields.
