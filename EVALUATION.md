# EVALUATION

## 1. Purpose
This file defines how each run should be checked and reported.

## 2. Pre-processing required
Before evaluation, any extra steps taken like splitting dataset in 80/20 or evaluating only on few animals.

Examples:
- data extraction or cleaning
- train/test split creation


## 3. Primary check
Each run must define the main thing being checked.

Examples:
- the model's RTD matches data RTD
- train loss decreases as expected
- the reproduced metric matches the published result closely enough

## 4. Results
Each run report should record:
- what was run
- what data, split, or subset was used
- the main output or metric
- relevant figures, tables, or image files
- any deviations, blockers, or audit notes

## 5. Verdict
- Did it work? Problems with current run? Possible next steps?