# Skills Factory

AI skills factory with advanced reasoning techniques for research, evaluation, and documentation.

## Quick Reference

- **Generate a skill:** Use advanced-skill-creator skill or `/generate-skill` command
- **Run expert panel:** Use expert-panel-deliberation skill or `/run-expert-panel` command
- **Research workflow:** Use research-interviewer → create-research-brief → consolidate-research skills

## Core Libraries

Located in `core/`:
- `technique-taxonomy.yaml` — 200+ reasoning techniques
- `artifact-contracts.yaml` — Standardized I/O schemas
- `scoring-rubrics.yaml` — Evaluation algorithms
- `skill-patterns.yaml` — Workflow patterns

## Available Skills

### Meta
- **advanced-skill-creator** — Generate domain-specific skills from templates

### Evaluation
- **expert-panel-deliberation** — Multi-expert evaluation and consensus
- **generate-ideas** — Structured ideation with tournament ranking

### Research

#### Workflow
```
┌─────────────────────┐
│research-interviewer │  Elicit knowledge and requirements
└──────────┬──────────┘
           │ PROBLEM-STATEMENT
           ▼
┌─────────────────────┐
│create-research-brief│  Design multi-LLM research strategy
│     (Phase 1)       │
└──────────┬──────────┘
           │ RESEARCH-BRIEF
           ▼
┌─────────────────────┐
│ consolidate-research│  Synthesize multi-source findings
└─────────────────────┘
```

- **research-interviewer** (v2.0) — Systematic knowledge elicitation
  - 6-phase workflow: establish → map → elicit → track → validate → output
  - Epistemic confidence tracking with 5-tier labeling
  - MECE coverage verification and gap detection
  - Bias protection: frame equivalence, disconfirmation hunt, assumption surfacing
  - Outputs: PROBLEM-STATEMENT, KNOWLEDGE-CORPUS, REQUIREMENTS
  - Domain references: product, architecture, research, requirements, custom
- **create-research-brief** (v2.0) — Multi-model research design and consolidation
  - Phase 1: MECE decomposition, risk assessment, model-specific prompts
  - Phase 2: Evidence tribunal, uncertainty decomposition, gap analysis
  - Features: Multi-hypothesis framing, expert panel integration, decision trees, kill criteria
- **consolidate-research** — Synthesize multi-source findings

### Documentation
- **create-documentation** — Diátaxis-aligned documentation

### Prompts
- **improve-prompt** — Optimize prompts for Claude

## Commands

- `/generate-skill` — Create new skill from templates
- `/run-expert-panel` — Quick expert panel invocation

## Working With This Repo

1. Skills auto-activate based on context
2. Use `/skill-name` for explicit invocation
3. Core libraries loaded on-demand via `@core/filename.yaml`
