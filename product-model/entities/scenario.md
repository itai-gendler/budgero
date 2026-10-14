---
domain: prebuilt-reports
references:
- kind: code
  role: implementation
  target: packages/core/src/services/scenarios/index.ts
- kind: code
  role: implementation
  target: packages/app/src/pages/analytics/useScenarios.ts
---

# Scenario

A saved what-if projection in the scenario planner: how income, spending and
net worth develop under chosen assumptions.

## Information kept

- **Name** — the scenario name, unique in the budget
- **Forecast model** — Average, Linear, Robust, Seasonal or Holt baseline
- **Income change** — income as a percentage of the baseline
- **Spending change** — spending as a percentage of the baseline
- **Horizon** — how many months ahead it projects
- **One-off events** — single future inflows or outflows in given months
