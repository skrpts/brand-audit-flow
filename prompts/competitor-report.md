---
type: prompt
id: competitor-report
title: Competitor Report
description: "Produces a structured competitive analysis report"
tags: [Production]
connections:
  - target: llm-service
    type: runs_on
  - target: campaign-performance-benchmarks
    type: references
---

### Inputs

- **Competitive analysis:** {{steps.competitive-analysis.output}}
- **Market context:** {{input.market_context}}
- **Competitor list:** {{input.competitor_list}}

Produce a competitive analysis report covering the following competitors in the {{input.market_context}} space.

Using the competitive analysis above, evaluate each competitor across:
- Positioning and value proposition
- Key messaging themes
- Channel presence and estimated spend
- Strengths and weaknesses
- Recent campaign activity

Conclude with:
- Competitive positioning map
- White space opportunities
- Recommended differentiation strategy

## Competitors
{{input.competitor_list}}
