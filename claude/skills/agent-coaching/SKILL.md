---
name: agent-coaching
description: Build agent coaching plans from QueSee call scores, covering which agents score lowest, which SOP criteria they miss, example calls to review and a coaching note per agent. Use when the user asks who needs coaching, why an agent's scores dropped, which agents miss a step in the SOP, or to prepare one-on-ones.
---

# Agent coaching

Follow the `quesee-data` skill for query rules, links and privacy.

## Range and fairness

- Default to the last 30 days, or use the user's period.
- Leave out agents with fewer than 10 scored calls in the range, and list them separately as "too few calls to judge".
- Compare each agent with the team average for the same calls. If the user names a department or call type, filter both the agent and the team to it.

## Gather

1. **Team picture:** get the call count and average `score` grouped by `agent_label`, and the team's average `score`.
2. **Who to coach:** take the agents furthest below the team average (default 3, or the number the user asks for). If the user named an agent, coach that agent.
3. **What they miss:** for each agent, get `criterion_score_pct` grouped by `criteria`, filtered to that agent, and compare it with the team's `criterion_score_pct` for the same criteria. Keep the 2 or 3 criteria with the largest gap.
4. **Example calls:** for each of those criteria, read 2 or 3 of the agent's calls where it scored low, with `score`, `criteria` (`score_reasoning`), `summary`, `areas_for_improvement` and `quesee_url`.
5. **Strengths:** read `areas_of_excellence` from the agent's best calls in the range.

## Write

For each agent:

- **Score:** the agent's average against the team's, and the number of calls.
- **Strength:** one strength, in a line.
- **Gap:** the 2 or 3 criteria they miss, each with the agent's rate against the team's rate.
- **Calls to review together:** links, each with what to listen for, in one line.
- **One behavior to change:** what doing it right sounds like, based on the scorecard's reasoning.

End with any team-wide pattern, such as a criterion most agents miss, which points to a training or process fix rather than one person.

Keep the tone factual and fair. This is for the manager's coaching conversation, not a ranking to share with the team.
