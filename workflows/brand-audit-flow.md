---
type: workflow
id: brand-audit-flow
title: Brand Audit Flow
description: "Competitive analysis, brand voice review, and positioning recommendations"
tags: [Needs Review]
connections:
  - target: competitive-analysis
    type: uses
  - target: brand-voice-matching
    type: uses
  - target: competitor-report
    type: uses
metadata:
  estimated_duration: "15-30 minutes"
  trigger: manual
---

## Overview

This workflow conducts a comprehensive brand audit by analysing competitor positioning, reviewing brand voice consistency, and producing actionable recommendations for differentiation. It's designed for strategic planning sessions or periodic brand health checks.

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

**Output:** Comprehensive competitive analysis report with strategic recommendations.

## Error Handling

- If competitor information is insufficient, supplement with publicly available marketing materials
- If brand voice has drifted significantly, flag for a brand strategy workshop rather than just correcting copy
- If competitive landscape reveals a major positioning conflict, escalate to leadership before finalising recommendations
