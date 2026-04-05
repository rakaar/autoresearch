# AGENTS

## Roles

### Planner
The planner is responsible for:
- reading TASK.md, EVALUATION.md, DB history, and prior run summaries
- proposing one concrete next experiment at a time
- avoiding repeated or near-duplicate ideas
- deciding whether to refine, branch, or stop
- creating a clearly scoped executor brief
- spawning or assigning an executor agent when needed
- passing the executor the minimum required context for the run

The planner must not:
- claim a result without a recorded run
- redefine success arbitrarily
- ignore prior failed attempts without reason
- create vague tasks that cannot be executed

When the planner delegates to an executor agent, it should provide at minimum:
- TASK.md
- EVALUATION.md
- the current planner brief
- relevant DB history and prior run summaries
- branch id and parent run id if any
- required checks, constraints, and expected artifacts

### Executor
The executor is responsible for:
- reading TASK.md and the planner brief
- implementing the proposed idea
- instantiating the concrete evaluation procedure for the run, consistent with EVALUATION.md
- running the experiment or analysis
- saving artifacts
- writing structured results back to the database
- writing a concise explanatory memo

The executor may:
- make reasonable implementation choices that the planner did not specify
- add defensive checks, diagnostics, and plots
- suggest follow-up ideas in the final memo

The executor must not:
- change the scientific goal
- silently change the evaluation standard
- omit failed results
- overwrite prior accepted artifacts without explicit versioning

## Global workflow

1. Planner reads current state.
2. Planner proposes one experiment brief.
3. Planner spawns or assigns an executor agent and passes the required context.
4. Executor performs the run.
5. Executor evaluates the run using the shared evaluation contract.
6. Executor writes outputs to DB in the required schema.
7. Planner reads the DB entry and decides the next step.

## Branching rules
Create a new branch when:
- the new idea differs materially from the parent idea
- the new idea changes assumptions, model family, or search strategy
- repeated refinements are no longer the best move

## Stop rules
Stop a branch when one or more hold:
- no meaningful improvement after N attempts
- repeated instability across seeds / subsets / runs
- idea is redundant with an existing branch
- performance gain is too small relative to complexity
- result fails required sanity checks
- evidence suggests the hypothesis is not worth further investment

## Documentation rules
Every run must leave behind:
- structured metrics
- status
- artifacts
- failure mode or success rationale
- short next-step suggestion

## Reproducibility rules
Every accepted run should record:
- run id
- parent id if any
- code version / commit hash
- dataset version
- random seed(s)
- commands or script paths used
- environment notes if relevant
