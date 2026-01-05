# StartupAI Decision Crew (Crew 3)

3-agent synthesis and decision engine for final pivot/proceed recommendations.

## Overview

This crew synthesizes validation evidence from Crew 2 and presents pivot/proceed options for human decision-making.

## Agents (3 total - COMPASS Team)

- **C1 (ProductPM)**: Evidence synthesizer, generates pivot/proceed options
- **C2 (HumanApproval)**: Human decision facilitator
- **C3 (RoadmapWriter)**: Decision documenter and roadmap writer

## Tasks (5)

1. `synthesize_evidence` - Analyze D/F/V signals and synthesize recommendation
2. `propose_pivot_proceed_options` - Generate options (PROCEED, SEGMENT_PIVOT, VALUE_PIVOT, PRICE_PIVOT, COST_PIVOT, KILL)
3. `request_human_decision` (HITL) - Present options and capture final decision
4. `document_decision` - Create comprehensive decision document for audit trail
5. `update_roadmap` - Translate decision into actionable roadmap updates

## HITL Checkpoint

- `request_human_decision` - Final pivot/proceed decision (the culmination of the validation pipeline)

## Deployment

```bash
# Install dependencies
uv sync

# Test locally
crewai run

# Deploy to AMP
crewai login
crewai deploy create
```

## Environment Variables

See `.env.example` for required configuration.

## Part of StartupAI Ecosystem

This is Crew 3 of 3 in the StartupAI validation pipeline:
- Crew 1: Intake → Crew 2: Validation → **Crew 3: Decision**

## Output

The final output is delivered to the product app webhook and includes:
- `roadmap_action`: proceed | pivot | kill
- `next_milestones`: Prioritized next steps
- `sprint_priorities`: Immediate focus areas
- `metrics_to_track`: Key success metrics
- `resource_requirements`: Resource needs
- `timeline_estimate`: Estimated timeline
