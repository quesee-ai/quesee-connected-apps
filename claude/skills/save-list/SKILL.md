---
name: save-list
description: Build a ranked list of customers at risk of cancelling from QueSee data, with why each one is at risk in their own words, what was promised to them and the next step to keep them. Use when the user asks why customers or subscribers are cancelling or disconnecting, who might cancel or churn, which customers are at risk, who to call today, what customers said before they disconnected, which accounts with repeat trouble tickets may leave, who mentioned switching to a competitor, or how to reduce churn.
---

# Save list

Follow the `quesee-data` skill for query rules, links and privacy.

## Gather

1. **Who:** read customers where `should_flag_for_retention` is true, or `churn_risk_level` is the organization's high tier (check the exact value with `quesee_values`). Read `churn_risk_score`, `intervention_urgency`, `priority_level`, `customer_value`, `last_contact_date`, `top_competitor`, `competitor_decision_stage`, `quesee_url`, and `churn_reasoning` and `suggested_next_action` when the plan has them.
2. **Rank:** by `intervention_urgency` first, then `churn_risk_score`, then `customer_value`. Default to the top 15, or the number the user asks for.
3. **Why, in their words:** for each subscriber on the list, read their most recent calls, filtered by `customer_id`, with `churn_risk_reason`, `summary`, `resolution_status`, `retention_outcome` and `quesee_url`.
4. **What changed:** read `subscriber_change` events for the last 30 days for these subscribers, especially `exit_intent_stated`, `competitor_first_mentioned` and `problem_came_back`.
5. **Promises:** read `commitment_created` events still open for these subscribers. A promise not yet kept is often the first thing to fix.

## Write

A ranked table with these columns: rank, subscriber id, risk, why (one line from the call, not a guess), last contact, open promise, next step, link.

For the next step:

- Ground it in the data: keep the open promise, fix the problem that came back, answer the competitor they named, or call back on the unresolved issue.
- Use the organization's own `save_offer` values when the data has them. Don't invent offers, prices or credits.
- If the data doesn't support a clear step, write "review the call" and link it.

After the table, add 2 or 3 lines on patterns across the list, such as a competitor named repeatedly, one area, or one repeat problem, and who should own each.
