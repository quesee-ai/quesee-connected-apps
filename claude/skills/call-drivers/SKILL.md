---
name: call-drivers
description: Find why customers call and what changed, using QueSee data, covering top call reasons and contact drivers, customer complaints, repeat problems, escalations and the root cause each team can fix. Use when the user asks why customers call, what they complain about, what drove calls this week or month, why call volume went up, what causes repeat calls, escalations or cancellations, or how to reduce call volume.
---

# Call drivers

Follow the `quesee-data` skill for query rules, links and privacy.

## Range

Default to the last 30 days, compared with the 30 days before, or use the user's period.

## Gather

1. **Volume by type:** count calls grouped by `call_type` for both periods, then by `call_type` and `time:week` for the trend. Rank call types by their change in calls.
2. **How they end:** for each top call type, get the share with `resolution_status` Escalated or Pending, and the average `score`.
3. **Reasons:** for the 3 call types that grew most, and any the user names, read up to 200 calls each with `issue_type`, `summary`, `churn_risk_reason` and `quesee_url`. Group them into a few plain reasons and count the calls in each. `issue_type` is free text, so do the grouping yourself and say the counts come from the calls you read.
4. **Repeat problems:** count `subscriber_change` events where `change` is `problem_came_back` in the range.
5. **Root cause:** when the plan has assessments, group subscribers by `churn_driver` `category` and read `root_cause` and `controllable`. Otherwise, say the root cause is inferred from the call summaries.

## Write

1. **Headline:** 2 or 3 lines on what drove calls and what changed.
2. **Table:** driver, calls this period, change, share escalated, main reasons, team that can fix it, example call link.
3. **Top 3 fixes:** each with the driver it removes, how many calls it touches and who owns it (billing, field service, network, support).

Only state counts that came from aggregate queries or from the calls you read. Mark anything inferred as inferred.
