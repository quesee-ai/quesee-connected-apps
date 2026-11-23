# QueSee fields most questions need

Confirm names and values with `quesee_schema` before you query, because organizations and plans differ.

## Calls

One record per scored call.

| Field | Meaning |
| - | - |
| `cdr_id` | Call id |
| `time_start` | When the call started |
| `agent_label` | The agent, shown as a label such as "Agent 07" |
| `department` | The department that took the call |
| `call_direction` | Inbound, Outbound or Internal |
| `call_type` | The organization's own call type |
| `score` | SOP score from 0 to 100. Null when the call is excluded or every criterion is not applicable |
| `sections` | Score per scorecard section (`section`, `score_pct`) |
| `criteria` | Result per criterion (`section`, `criterion`, `score`, `max_score`, `not_applicable`, `score_reasoning`) |
| `resolution_status` | Resolved, Escalated or Pending |
| `retention_outcome`, `sale_status` | Outcome values set by the organization |
| `issue_type` | Short free-text reason for the call. Not groupable, so read it in rows |
| `summary` | What happened on the call |
| `churn_risk`, `churn_risk_reason` | Churn risk from this call (0 to 1) and why |
| `areas_for_improvement`, `areas_of_excellence`, `action_items` | Coaching notes for the call |
| `smart_fields`, `active_flags` | Automatic flags and flags set by managers |
| `customer_id`, `crm_account_id` | The subscriber on the call |
| `quesee_url`, `customer_url` | Links to the call and the subscriber in QueSee |

Groupable call fields: `call_direction`, `call_type`, `department`, `agent_label`, `resolution_status`, `sale_status`, `retention_outcome`, `lead_source`, `save_offer`, `transaction_type`, `active_flags`, `smart_fields`, `sections`, `criteria`.

## Customers

One record per subscriber account.

| Field | Meaning |
| - | - |
| `customer_id`, `crm_account_id` | Subscriber ids |
| `status`, `lifecycle_stage` | Account status and stage |
| `churn_risk_level`, `churn_risk_score` | Risk tier and score (0 to 1) |
| `intervention_urgency`, `priority_level` | How soon to act and how much it matters |
| `should_flag_for_retention` | In the retention queue |
| `satisfaction_score`, `avg_experience_score`, `score_trend` | Experience measures and their direction |
| `call_count_30d`, `call_count_90d`, `last_contact_date` | Contact history |
| `customer_value` | Value of the account |
| `top_competitor`, `competitor_decision_stage` | Competitor named and how far the decision has gone |
| `churn_drivers`, `churn_reasoning`, `suggested_next_action` | Why they may leave and what to do (some plans only) |
| `quesee_url` | Link to the subscriber in QueSee |

Groupable customer fields: `crm_system`, `lifecycle_stage`, `status`, `churn_risk_level`, `intervention_urgency`, `priority_level`, `score_trend`, `should_flag_for_retention`, `network_healthy`, `top_competitor`, `competitor_decision_stage`, `churn_drivers`, `area`.

## Assessments

Each subscriber's latest QueSee read for a month or quarter (some plans only). Pass `period`. Counts are subscribers.

Fields: `risk_level`, `churn_risk_score`, `status`, `lifecycle_stage`, `cancellation_reason`, `exit_intent`, `intervention_urgency`, `save_probability`, `save_band`, `controllable`, `paying`, `cancelled_earlier`, `agent_handling_quality`, `customer_value`.

Lists: `churn_driver` (`category`, `sub_category`, `root_cause`, `controllable`, `severity`, `status`), `competitor`, `competitor_advantage`, `churn_indicator`, `retention_strength`, `area`. `churn_driver.root_cause` names what caused the risk and which team can fix it.

## Events

What happened to a subscriber over time. Pass `event_type` and `time_range`.

| `event_type` | Meaning |
| - | - |
| `subscriber_change` | A change in the subscriber's stance. `change` is one of `exit_intent_stated`, `exit_intent_withdrawn`, `competitor_first_mentioned`, `cancellation_reason_given`, `problem_came_back` |
| `commitment_created`, `commitment_resolved` | Something the team promised the subscriber, and when it was kept (`commitment_type`, `commitment_status`, `response_seconds`) |
| `retention_owner_changed` | Who owns the save |
| `customer_merged` | Two records joined |

Event rows carry `call_url` and `customer_url`.

## Metrics

Calls and customers take `count` (the default), `avg`, `min`, `max`, `sum`, `distinct`, `customers` and `rate` (a field and a value, such as the share of calls with `resolution_status` Escalated). `criterion_score_pct` needs `group_by` criteria, and `section_score_pct` needs `group_by` sections. Assessments take `customers`, `sum` and `avg`. Events return event counts, distinct customers and `avg_response_seconds`.
