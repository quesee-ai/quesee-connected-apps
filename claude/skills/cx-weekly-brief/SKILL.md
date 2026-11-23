---
name: cx-weekly-brief
description: Write a weekly customer experience brief from QueSee data for a CX, support or retention leader, covering call volume, SOP scores, escalations, subscribers at risk and what changed since last week. Use when the user asks how last week went, for a Monday brief, a weekly summary, or a report for their team or leadership.
---

# Weekly CX brief

Follow the `quesee-data` skill for query rules, links and privacy.

## Range

Use the last full week, Monday to Sunday, in the user's time zone, and compare it with the week before. If the user names another period, use that period and the equal period before it.

## Gather

1. **Volume:** count calls this week and last week, grouped by `call_direction`. Then group by `call_type` to find the 3 call types that changed most.
2. **Quality:** get the average `score` for both weeks, `section_score_pct` grouped by `sections` for both weeks, and the share of calls with `resolution_status` Escalated or Pending.
3. **Risk:** count customers with `should_flag_for_retention` true. Then read the top 5 by `intervention_urgency` and `churn_risk_score`, with `churn_risk_level`, `last_contact_date`, `top_competitor` and `quesee_url`.
4. **Subscriber changes:** count `subscriber_change` events by `change` for both weeks. The ones that matter most are `exit_intent_stated`, `competitor_first_mentioned` and `problem_came_back`.
5. **Commitments:** count `commitment_created` and `commitment_resolved` this week, and note any commitments still open.

Skip any step whose entity or field `quesee_schema` says this organization doesn't have, and say which part is missing.

## Write

Keep it to one screen:

1. **Headline:** 3 to 5 lines, each a number with its change from last week, such as "Avg SOP score 81.4, up 2.1 points".
2. **Table:** metric, this week, last week, change.
3. **At risk now:** the top 5 subscribers, each with its id, one-line reason, last contact and link.
4. **What moved:** the call types and scorecard sections that changed most, and one likely reason for each from the call summaries. Say when a reason is inferred.
5. **Next actions:** at most 3, each with who should own it (team or role) and why.

Write for a busy operator: plain words, numbers first, no filler.
