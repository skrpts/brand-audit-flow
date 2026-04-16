---
type: skill
id: audience-segmentation
title: Audience Segmentation
description: "Divides target markets into actionable segments based on behaviour and demographics"
tags: [Tested, Audience, Writing]
context_params:
  market_context:
    label: "Market Context"
    description: "Market information including target segments and competitors"
    default: ""
    required: true
connections:
  - target: llm-service
    type: runs_on
---

## Capability

Analyses customer data and market research to identify distinct audience segments with shared characteristics, needs, and behaviours.

## When to Use

- Planning targeted campaigns
- Personalising email marketing
- Defining ad audience groups
- Prioritising product messaging

## Inputs

Customer data, survey results, behavioural analytics, market research

## Outputs

Segment profiles: demographics, psychographics, pain points, preferred channels, messaging angle
