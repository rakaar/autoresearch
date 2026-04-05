# TASK

## 1. Project title
Short working title for the research problem.

## 2. Big question
What is the main scientific or engineering question?

## 3. Objective
What should the system try to discover, improve, explain, fit, predict, optimize, or compare?

## 4. Problem type
Choose one or more:
- hypothesis generation
- model comparison
- model fitting
- algorithm design
- search / optimization
- data analysis
- mechanism explanation
- experiment planning
- pipeline improvement

## 5. Inputs
Describe the available inputs.
Examples:
- datasets
- metadata
- literature summaries
- baseline code
- prior results
- simulations
- benchmark tasks

## 6. Expected outputs
Describe the expected outputs.
Examples:
- best-performing model
- ranked hypotheses
- parameter estimates
- comparison plots
- result tables
- heuristic or algorithm
- summary memo
- reproducible scripts

## 7. Constraints
List hard constraints.
Examples:
- no data leakage
- no manual relabeling
- no external API calls
- limited runtime
- limited GPU budget
- certain folders/files are read-only
- only approved libraries may be used

## 8. Known background
Summarize relevant prior knowledge:
- important literature
- known baselines
- previous failures
- domain assumptions
- known confounds

## 9. Search space
What kinds of ideas are allowed?
Examples:
- model families
- fitting strategies
- feature constructions
- optimization tricks
- summary statistics
- mechanistic hypotheses

Also note what is out of scope.

## 10. Success criteria
What counts as progress?
Examples:
- better held-out score
- improved interpretability
- more robust fit across seeds
- lower complexity for similar performance
- clearer mechanistic explanation
- novel but plausible hypothesis

## 11. Failure criteria
What makes a run invalid or uninteresting?
Examples:
- overfitting
- numerical instability
- irreproducible results
- trivial restatement of prior idea
- unsupported interpretation
- metric improvement from leakage or bug

## 12. Minimum artifact set for every accepted run
Each run should ideally produce:
- structured metrics
- short memo
- at least one plot or table
- reproducible command or script reference

## 13. Priority order
Rank what matters most:
1. correctness
2. generalization
3. robustness
4. interpretability
5. novelty
6. simplicity
7. runtime / cost

## 14. Notes for planner and executor
Planner and executor must both read this file before starting work.
Executor may use local judgment where the planner was underspecified, but must stay consistent with this file.
