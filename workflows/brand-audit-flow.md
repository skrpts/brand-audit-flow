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
  - target: competitor-reporting
    type: uses
  - target: language-polish
    type: uses
  - target: consistency-check
    type: uses
  - target: llm-service
    type: runs_on
  - target: audience-segmentation
    type: uses
metadata:
  estimated_duration: "15-30 minutes"
  trigger: manual
output_step: "language-polish"
composite_steps:
  - "competitive-analysis"
  - "brand-voice-matching"
  - "audience-segmentation"
  - "competitor-reporting"
execution:
  - skill: "competitive-analysis"
    prompt: "analyse-competitors"
    step_type: "synthesis"
    output: { name: "competitor_analysis", type: "text" }
    context:
      your_product: "Not specified"
  - skill: "brand-voice-matching"
    prompt: "match-brand-voice"
    step_type: "content"
    output: { name: "voice_match", type: "text" }
    context:
      brand_guidelines: "No specific brand guidelines"
  - skill: "audience-segmentation"
    prompt: "segment-audience"
    step_type: "synthesis"
    output: { name: "audience_segments", type: "list" }
    context:
      market_context: "No additional market context"
  - skill: "consistency-check"
    step_type: "review"
    prompt: "check-consistency"
    output: { name: "consistency_verdict", type: "decision" }
    context:
      voice_profile: "Neutral professional tone"
      consistency_strictness: "Standard"
  - skill: "competitor-reporting"
    prompt: "competitor-report"
    step_type: "content"
    output: { name: "audit_report", type: "text" }
    bindings:
      competitor_analysis:
        from_step: "Competitive Analysis"
        field: output
      voice_match:
        from_step: "Brand Voice Matching"
        field: output
      audience_segments:
        from_step: "Audience Segmentation"
        field: output
  - skill: "language-polish"
    step_type: "content"
    prompt: "polish-language"
    output: { name: "polished_audit", type: "text" }
    context:
      voice_profile: "Neutral professional tone"
      grammar_strictness: "Professional"
    bindings:
      source:
        from_step: "Competitor Report Builder"
        field: output
---

## Overview

This workflow conducts a thorough brand audit by analyzing competitor positioning, reviewing brand voice consistency, and producing actionable recommendations for differentiation. It's designed for strategic planning sessions or periodic brand health checks.

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
- If competitive landscape reveals a major positioning conflict, escalate to leadership before finalizing recommendations

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
2. Review the included documents, assets, or source nodes and customize them to match your team, brand, or domain conventions where needed.
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

