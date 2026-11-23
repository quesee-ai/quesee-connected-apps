---
name: team-coaching
description: Coach the whole team from QueSee scores against your own SOP - the steps the team misses most, the calls worth reviewing with a coaching note on each, and training topics. Use when the user asks how to coach or train the team, which SOP or procedure steps get missed, whether the team or the after-hours desk follows the process, which calls to review this week, what to cover in team training, or for coaching notes on a specific call.
---

# Team coaching

Follow the `quesee-data` skill for query rules, links and privacy.

This skill works at two levels only: the whole team (or a department), and one call at a time. It never scores, ranks or compares individual employees. If the user asks for a ranking or score per agent, explain that you can show team-level gaps and the calls worth reviewing, and offer that instead.

## Range

Default to the last 30 days, compared with the 30 days before, or use the user's period. If the user names a department or call type, filter to it.

## Gather

1. **Team picture:** the team's average `score`, and `section_score_pct` grouped by `sections`, for both periods.
2. **Steps the team misses:** `criterion_score_pct` grouped by `criteria` for both periods. Keep the 3 to 5 criteria with the lowest rate or the biggest drop.
3. **Calls worth reviewing:** for each of those criteria, read 2 or 3 recent calls where it scored low, with `criteria` (`score_reasoning`), `summary`, `areas_for_improvement`, `areas_of_excellence` and `quesee_url`. Don't request or group by `agent_label`.

## Write

1. **Headline:** the team's average and its change, and the step missed most often.
2. **Table:** SOP step, team pass rate this period, last period, change.
3. **Calls to review:** for each step, the calls with a one-line coaching note each: what happened, what doing it right sounds like (from the scorecard's reasoning), and the link. A coaching note is about the call, not the person.
4. **Training topics:** at most 3, each tied to a step the team misses, with the calls to use as examples.

Keep the tone factual and constructive. This is for coaching and training, not for rating people.
