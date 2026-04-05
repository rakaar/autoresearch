# EVALUATION

## 1. Purpose
This file defines the abstract evaluation contract for all tasks and runs.

The planner may specify what should be emphasized in a particular run.
The executor may instantiate the exact calculations for that run.
However, the executor must remain consistent with this contract.

## 2. Evaluation layers

### Layer A: validity checks
These are mandatory checks that determine whether a run is valid at all.
Examples:
- code runs successfully
- outputs have expected shape/type
- no missing critical artifacts
- no data leakage detected
- model converged or failed explicitly
- no forbidden resources were used

### Layer B: primary objective
This is the main quantity to optimize.
Examples:
- held-out predictive score
- likelihood
- classification accuracy
- reconstruction error
- optimization objective
- scientific fit to benchmark patterns

### Layer C: secondary objectives
These help rank ideas that are close on the primary objective.
Examples:
- robustness across seeds
- cross-subject consistency
- complexity penalty
- runtime
- memory usage
- interpretability
- calibration
- simplicity

### Layer D: sanity checks
These are designed to catch misleading wins.
Examples:
- shuffled-label baseline
- null model comparison
- simpler baseline comparison
- ablation checks
- seed sensitivity
- train/test split robustness
- subset robustness

## 3. Standard verdict classes
Each run should end with one of:
- invalid
- failed
- weak_negative
- inconclusive
- promising
- strong_positive
- accepted_baseline
- accepted_candidate

## 4. Tie-breaking rules
When primary scores are close, prefer:
1. valid over questionable
2. robust over fragile
3. simpler over more complex
4. interpretable over opaque
5. reproducible over hard-to-reproduce
6. lower cost over higher cost

## 5. Planner responsibilities
The planner should specify:
- what is the primary target of the current run
- which secondary metrics matter most for this run
- what comparisons are mandatory

## 6. Executor responsibilities
The executor should specify in the run report:
- exact metric definitions used
- exact data split / evaluation subset used
- exact sanity checks performed
- any deviations from default evaluation assumptions

## 7. Recommended result object
Each run should produce a structured result object like:

```json
{
  "valid": true,
  "status": "completed",
  "primary_metrics": {},
  "secondary_metrics": {},
  "sanity_checks": {},
  "verdict": "promising",
  "notes": "Short explanation"
}
```
