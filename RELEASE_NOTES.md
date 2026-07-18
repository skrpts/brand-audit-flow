# Release Notes

## v1.1.28
GH#863 Wave 1 (K-045 intent/output-mismatch) — the `competitor-report` deliverable was never invoked by the workflow. Wire it as an execution step: add backing skill `competitor-reporting` (Competitor Report Builder), run competitor-report as the last content step before language-polish, bind its inputs (competitor analysis, brand-voice match, audience segments) via explicit `from_step`, and bind `language-polish` `source` from the report. Convert the prompt's positional `{{steps.*.output}}` ref to `context_params` + `{{step.context.*}}`. Re-pin polish-language to v1.0.6.

## v1.1.27
GH#845 — republish with American English (en-US) content, completing the source-only GH#805 flip that never reached the Hub. Copy only — no functional or behaviour change.

## v1.1.26
GH#745 — declare per-step `output: {name, type}` on every execution step (competitor_analysis/text, voice_match/text, audience_segments/list, consistency_verdict/decision, polished_audit/text). Lights up the #744 rich flow-map. Content-only; no bindings or logic changes.

## v1.1.25
GH#645 Row 3b — migrate to K-037 dep-referenced schema. Strip 11 inline shared-content files and declare 11 hub-shared deps (UUID id + slug name + version + checksum from `gen-dep-checksums.mjs`). Closes pre-Step-3 inline-vendoring for this bundle.

## v1.1.24
Wave 2: re-signed with canonical engine signing pipeline.

## v1.1.23
Tags migrated inline into manifest (GH#586). tags.yaml retired.

## v1.1.22
Bundle re-signed with canonical engine signing pipeline (Wave 2 migration).

## v1.1.21
Signature fix — RELEASE_NOTES.md now included in integrity checksum.

## v1.1.20
Initial catalog release with full structural and content-quality validation. All scanner checks pass.
