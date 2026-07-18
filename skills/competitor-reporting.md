---
type: skill
id: competitor-reporting
title: Competitor Report Builder
description: "Assembles the upstream competitive analysis, brand-voice match, and audience segments into the final brand/competitor audit report"
tags: [Production, Competitive, Communication]
connections:
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "5 minutes"
  avg_tokens: 3500
  trigger: manual
---

## Competitor Report Builder

This skill produces the brand audit deliverable: a structured competitive analysis report that synthesises the upstream competitor analysis, brand-voice match, and audience segments into positioning and differentiation recommendations.

### Core Capability

Given the competitor analysis, brand-voice consistency review, and audience segments, this skill evaluates each competitor across positioning, messaging, channel presence, strengths, weaknesses, and recent activity, then concludes with a positioning map, white space opportunities, and a recommended differentiation strategy.

### Output Structure

A structured markdown report — competitor-by-competitor evaluation followed by the positioning map, white space analysis, and differentiation recommendations. This report is the workflow deliverable and feeds the final language-polish stage.
