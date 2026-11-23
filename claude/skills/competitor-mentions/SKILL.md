---
name: competitor-mentions
description: Find which competitors customers mention on calls, how often, why they consider switching, and which customers are deciding right now, from QueSee data. Use when the user asks about competitors, who customers are switching to, competitive threats, price or offer comparisons customers raise, or which customers to win back from a competitor.
---

# Competitor mentions

Follow the `quesee-data` skill for query rules, links and privacy.

## Range

Default to the last 90 days, compared with the 90 days before, or use the user's period.

## Gather

1. **Who is named:** count customers grouped by `top_competitor`, and by `top_competitor` and `competitor_decision_stage`. Get the exact stage values from `quesee_values`.
2. **Trend:** count `subscriber_change` events where `change` is `competitor_first_mentioned`, grouped by `time:week`.
3. **Why:** when the plan has assessments, read `competitor` and `competitor_advantage` for the period and group the reasons. Otherwise, read up to 200 calls from customers with a `top_competitor`, with `summary`, `churn_risk_reason` and `quesee_url`, and group the reasons yourself.
4. **Deciding now:** read the customers at the latest decision stage, with `churn_risk_score`, `customer_value`, `last_contact_date` and `quesee_url`.

## Write

1. **Headline:** the competitor named most, how many customers named it, and the change from the prior period.
2. **Table:** competitor, customers, change, main reasons in the customers' own words, example call link.
3. **Deciding now:** the customers at the latest stage, ranked by value, each with a one-line reason and a link.
4. **What to answer:** for the top 1 or 2 reasons, what the team can offer or fix, based on the organization's own offers in the data.

Report what customers said, not opinions about the competitor. Don't invent prices or offers.
