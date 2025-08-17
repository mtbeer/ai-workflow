# AI Workflow

Repository of templates and evaluation artifacts for generating product docs and agent-executable plans for the Roo orchestrator.

## What this repo contains

- [`guideme-roo-code/slash-command-templates/guideme-plan.md`](guideme-roo-code/slash-command-templates/guideme-plan.md:1) — template to generate PLAN.md via `/guideme-plan`
- [`guideme-roo-code/slash-command-templates/guideme-prd.md`](guideme-roo-code/slash-command-templates/guideme-prd.md:1) — template to generate PRD.md via `/guideme-prd`
- [`guideme-roo-code/slash-command-templates/guideme-specs.md`](guideme-roo-code/slash-command-templates/guideme-specs.md:1) — template to generate SPECS.md via `/guideme-specs`
- [`evals/`](evals/:1) — evaluation artifacts and plan reviews (LLM + human scoring)
- [`evals/PLAN_llm-as-a-judge/PLAN_gpt5mini_architect.md`](evals/PLAN_llm-as-a-judge/PLAN_gpt5mini_architect.md:1) — example plan used in evaluations
- [`guideme-roo-code/docs/`](guideme-roo-code/docs/:1) — demo docs (these are demo outputs and excluded from automated analysis)

## Purpose

This repository centralises:
- Slash-command templates that produce structured product documents (PRD, SPECS, PLAN) intended for an AI orchestrator.
- Evaluation plans and scoring used to validate and compare plan quality across different LLM outputs.

## Usage

1. Use the slash-command templates to create or update the documents consumed by the orchestrator:
   - See [`guideme-roo-code/slash-command-templates/guideme-plan.md`](guideme-roo-code/slash-command-templates/guideme-plan.md:1)
2. Refer to evaluation artifacts in [`evals/`](evals/:1) for examples of plan reviews and scoring criteria.

## Contributing

- Improve or add templates under [`guideme-roo-code/slash-command-templates/`](guideme-roo-code/slash-command-templates/:1).
- Add new evaluation scenarios under [`evals/`](evals/:1) to capture additional edge cases and scoring rubrics.
- Keep demo output in [`guideme-roo-code/docs/`](guideme-roo-code/docs/:1); CI and automated analysis should ignore this folder.

## Notes

- The `docs/` folder contains example output produced by the templates and is intentionally excluded from automated analysis and CI steps to avoid mixing demo content with source templates and evals.

## Files of interest

- [`guideme-roo-code/slash-command-templates/guideme-plan.md`](guideme-roo-code/slash-command-templates/guideme-plan.md:1)  
- [`guideme-roo-code/slash-command-templates/guideme-prd.md`](guideme-roo-code/slash-command-templates/guideme-prd.md:1)  
- [`guideme-roo-code/slash-command-templates/guideme-specs.md`](guideme-roo-code/slash-command-templates/guideme-specs.md:1)  
- [`evals/PLAN_llm-as-a-judge/plan-review-scores-qwen3-235b-a22b-reviewer.md`](evals/PLAN_llm-as-a-judge/plan-review-scores-qwen3-235b-a22b-reviewer.md:1)

## License

No license specified. Add a `LICENSE` file if you want to apply a license.