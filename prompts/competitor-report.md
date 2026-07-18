---
type: prompt
id: competitor-report
title: Competitor Report
description: "Produces a structured competitive analysis report"
tags: [Production, Competitive, Communication]
inputs:
  market_context:
    label: "Market Context"
    description: "Market information including target segments, competitors, and positioning"
    example: "Enterprise project management tools. Main competitors: Asana, Monday, Jira."
    required: true
    type: text
  competitor_list:
    label: "Competitor List"
    description: "List of competitors to analyze"
    example: "Notion, Coda, Slite, Craft, Obsidian"
    required: true
    type: text
context_params:
  competitor_analysis:
    label: "Competitor Analysis"
    description: "Upstream competitor analysis — positioning, messaging, channels, and opportunities."
    required: false
  voice_match:
    label: "Brand Voice Match"
    description: "Upstream brand-voice consistency review — deviations and recommended corrections."
    required: false
  audience_segments:
    label: "Audience Segments"
    description: "Upstream audience segments — target segments feeding positioning."
    required: false
connections:
  - target: competitive-analysis
    type: derived_from
  - target: llm-service
    type: runs_on
  - target: campaign-performance-benchmarks
    type: references
---

### Inputs

- **Competitor analysis:** {{step.context.competitor_analysis}}
- **Brand voice match:** {{step.context.voice_match}}
- **Audience segments:** {{step.context.audience_segments}}
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
