---
type: prompt
id: competitor-report
title: Competitor Report
description: "Produces a structured competitive analysis report"
tags: []
connections:
  - target: openai-gpt4
    type: runs_on
  - target: campaign-performance-benchmarks
    type: references
---

Produce a competitive analysis report covering the following competitors in the {{industry}} space.

For each competitor:
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
{{competitor_list}}
