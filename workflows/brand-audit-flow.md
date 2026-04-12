---
type: workflow
id: brand-audit-flow
title: Brand Audit Flow
description: "Competitive analysis, brand voice review, and positioning recommendations"
tags: [Production, Communication, Competitive]
connections:
  - target: competitive-analysis
    type: uses
  - target: brand-voice-matching
    type: uses
  - target: llm-service
    type: runs_on
  - target: audience-segmentation
    type: uses
metadata:
  estimated_duration: "15-30 minutes"
  trigger: manual
execution:
  - skill: "competitive-analysis"
    step_type: "synthesis"
  - skill: "brand-voice-matching"
    step_type: "content"
    input_from: "competitive-analysis"
  - skill: "audience-segmentation"
    step_type: "synthesis"
    input_from: "brand-voice-matching"
---

## Overview

This workflow conducts a thorough brand audit by analysing competitor positioning, reviewing brand voice consistency, and producing actionable recommendations for differentiation. It's designed for strategic planning sessions or periodic brand health checks.

## Pipeline Stages

### Stage 1: Competitive Analysis

**Input:** Competitor list, their public marketing materials, market context

Invoke the **competitive-analysis** skill to benchmark competitor positioning, messaging, channels, and content strategy. Identify gaps and opportunities in the competitive landscape.

**Output:** Competitive matrix with positioning map and opportunity identification.

### Stage 2: Brand Voice Review

**Input:** Recent brand content across channels + brand voice guidelines

Invoke the **brand-voice-matching** skill to audit current content for consistency with brand guidelines. Identify deviations, channel-specific adaptations, and areas where the brand voice has drifted.

**Output:** Brand voice consistency report with specific examples and recommended corrections.

### Stage 3: Competitor Report

**Input:** Competitive analysis from Stage 1 + performance benchmarks

Invoke the **competitor-report** prompt to produce a structured report covering each competitor's positioning, messaging themes, channel presence, strengths, weaknesses, and recent activity. Concludes with white space opportunities and differentiation strategy.

**Output:** Detailed competitive analysis report with strategic recommendations.

## Error Handling

- If competitor information is insufficient, supplement with publicly available marketing materials
- If brand voice has drifted significantly, flag for a brand strategy workshop rather than just correcting copy
- If competitive landscape reveals a major positioning conflict, escalate to leadership before finalising recommendations

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.competitor_list}}` | Yes | Competitor list | `Paste the relevant brief, notes, source material, or dataset here.` |
| `{{input.their_public_marketing_materials}}` | Yes | their public marketing materials | `Paste the relevant brief, notes, source material, or dataset here.` |
| `{{input.market_context}}` | Yes | market context | `Paste a short brief describing the goal, audience, and constraints.` |
| `{{input.recent_brand_content_across}}` | No | Recent brand content across channels + brand voice guidelines | `Paste the relevant brief, notes, source material, or dataset here.` |

## Outputs

| Name | Description |
|------|-------------|
| Competitive matrix | Competitive matrix with positioning map and opportunity identification |
| Brand voice consistency report | Brand voice consistency report with specific examples and recommended corrections |
| Detailed competitive analysis report | Detailed competitive analysis report with strategic recommendations |

## Setup

Before running this workflow:

1. No external services required — paste your content directly and provide any supporting context as inputs or source nodes.
2. Review the included documents, assets, or source nodes and customise them to match your team, brand, or domain conventions where needed.
3. No specific AI provider or API key is required beyond your configured skrptiq LLM provider.

## Provider Notes

- Most stages work with any capable model; stronger models usually improve synthesis, judgement, and writing quality.
- Extraction, classification, and formatting steps generally run well on smaller or faster models.
- Because there are no vendor-specific integrations here, provider choice is mostly a trade-off between speed, quality, and cost.

## Example Input

To test this workflow immediately after import:

```
Competitor List: "Paste the relevant brief, notes, source material, or dataset here."
Their Public Marketing Materials: "Paste the relevant brief, notes, source material, or dataset here."
Market Context: "Paste a short brief describing the goal, audience, and constraints."
Recent Brand Content Across: "Paste the relevant brief, notes, source material, or dataset here."
```

