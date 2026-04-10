---
type: prompt
id: analyse-competitors
title: "Analyse Competitors"
description: "Researches competitor positioning, messaging, and tactical approach"
tags: [Production, Marketing, Competitive]
connections:
  - target: competitive-analysis
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Drives the competitive analysis skill.

## Prompt

You are a competitive intelligence analyst. Analyse the competitors described below.

### Competitor Information

{{steps.previous.output}}

### Your Product/Brand

{{input.your_product}}

### Instructions

For each competitor, assess:

1. **Positioning** — how do they position themselves in the market?
2. **Messaging** — what are their key messages and value propositions?
3. **Target audience** — who are they going after?
4. **Strengths** — what do they do well?
5. **Weaknesses** — where are they vulnerable?
6. **Content strategy** — what topics, formats, and channels do they use?
7. **Pricing** — how does their pricing compare?

### Synthesis

After individual assessments:
- **Competitive landscape map** — where does each competitor sit relative to your product?
- **Gaps and opportunities** — what are competitors NOT doing that you could own?
- **Threats** — where are competitors strongest against your positioning?
- **Recommendations** — 3-5 specific actions based on the analysis

## Formatting Rules

- Use British English throughout
- Be specific and actionable — no vague recommendations
- Structure output clearly with headings, tables, or lists as appropriate
