# AGENTS

This repo is organized for iterative research runs. `TASK.md` defines the current research goal, and `EVALUATION.md` defines how each run is checked.

The planner decides the next concrete run. The executor performs it, records the result, and leaves enough artifacts and notes for the next step.

There is one planner agent coordinating the research loop. The planner may spawn or assign executor agents to carry out individual runs.

## Planner
The planner decides what the next run should be and makes sure it is concrete enough to execute.

The planner:
- reads `TASK.md`, `EVALUATION.md`, and prior run history
- proposes one concrete next run at a time
- decides whether to continue the current track, start a new track, or stop
- writes a brief that gives the executor the required context

## Executor
The executor performs the run described by the planner and records what happened.

The executor:
- reads `TASK.md`, `EVALUATION.md`, and the planner brief
- runs the proposed task
- records results, artifact paths, and verdict
- notes blockers, deviations, and next steps

## Handoff
When the planner delegates to an executor, the handoff should include:
- `TASK.md`
- `EVALUATION.md`
- the current planner brief
- relevant prior runs
- `track_id` and `parent_run_id` if any
- required checks and expected artifacts

## Workflow
1. The planner reviews the current state.
2. The planner writes one concrete brief.
3. The executor performs the run.
4. The executor records results.
5. The planner decides the next step.

## Track rule
Start a new track when the idea, assumptions, or strategy changes materially.

## Reproducibility
Each accepted run should record:
- `run_id`
- `track_id`
- `parent_run_id` if any
- code/data reference
- commands or script paths
- environment notes if relevant
