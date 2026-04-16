---
type: skill
id: brand-voice-matching
title: Brand Voice Matching
description: "Ensures content aligns with established brand voice and tone guidelines"
tags: [Production, Communication, Competitive]
context_params:
  brand_guidelines:
    label: "Brand Guidelines"
    description: "Brand voice, tone, and style guidelines"
    default: ""
    required: true
connections:
  - target: llm-service
    type: runs_on
  - target: brand-voice-guide
    type: references
---

## Capability

Reviews and adjusts content to match a brand's documented voice, tone, and style guidelines across all touchpoints.

## When to Use

- Reviewing content from multiple writers
- Adapting content for different channels while keeping brand consistency
- Onboarding new content creators

## Inputs

Draft content + brand voice guidelines + target channel

## Outputs

Revised content matching brand voice, with annotations explaining changes made
