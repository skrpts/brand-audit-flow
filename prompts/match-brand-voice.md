---
type: prompt
id: match-brand-voice
title: "Match Brand Voice"
description: "Adjusts content to align with established brand voice guidelines"
tags: [Production, Marketing, Writing]
inputs:
  brand_guidelines:
    label: "Brand Guidelines"
    description: "Your brand voice, tone, and style guidelines"
    example: "Professional but approachable. Use 'we' not 'I'. Avoid exclamation marks."
    required: true
    type: text
connections:
  - target: brand-voice-matching
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Drives the brand voice matching skill.

## Prompt

You are a brand editor. Review and adjust the content below to match the brand voice guidelines.

### Content to Adjust

{{steps.previous.output}}

### Brand Voice Guidelines

{{input.brand_guidelines}}

### Instructions

1. **Audit** — identify where the content deviates from the brand voice (tone, vocabulary, sentence style)
2. **Adjust** — rewrite sections that don't match, preserving the message
3. **Verify** — ensure the adjusted content is consistent throughout

### Rules

- Preserve all factual content — only change how it's expressed
- Match the brand's vocabulary preferences (e.g. "customers" vs "users" vs "people")
- Maintain the brand's characteristic sentence length and complexity
- Apply the brand's stance on contractions, exclamation marks, emoji, and humour
- Flag any content that conflicts with brand values and cannot be fixed with tone changes alone

### Output

Return the COMPLETE adjusted text — the entire document with brand voice applied throughout. Do not return an audit report or a list of changes. The output should be the finished, brand-consistent text.

## Formatting Rules

- Use British English throughout
- Preserve the original document structure (headings, lists, formatting)
