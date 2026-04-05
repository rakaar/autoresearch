# DB SCHEMA

## Purpose
This file defines the minimum schema for recording experiments.

A database can be SQLite, JSONL, CSV + artifact folders, or another system.
Regardless of implementation, every run should map to this schema.

## Core entities

### 1. runs
One row / record per executor run.

Required fields:
- run_id
- created_at
- planner_brief_id
- parent_run_id (nullable)
- branch_id
- status
- verdict
- task_name
- short_title
- idea_summary
- implementation_summary
- evaluation_summary
- failure_reason (nullable)
- next_suggestion (nullable)
- code_ref
- data_ref
- seed_info
- artifact_paths
- metrics_json

### 2. branches
One row / record per line of investigation.

Required fields:
- branch_id
- created_at
- parent_branch_id (nullable)
- title
- hypothesis_or_strategy
- current_status
- best_run_id (nullable)
- stop_reason (nullable)

### 3. planner_briefs
One row / record per plan sent to an executor.

Required fields:
- planner_brief_id
- created_at
- branch_id
- objective
- rationale
- proposed_changes
- required_checks
- expected_artifacts
- priority_metrics
- notes

## Recommended status values
For runs:
- queued
- running
- completed
- failed
- invalid
- archived

For branches:
- active
- paused
- accepted
- killed
- archived

## Metrics conventions
Store metrics in structured form, not only prose.
Recommended:
- primary metrics
- secondary metrics
- robustness metrics
- runtime / cost metrics

## Artifact conventions
Artifacts may include:
- plots
- tables
- logs
- saved parameters
- model summaries
- notebooks
- scripts
- rendered reports

Each artifact should be versioned or traceable to a run_id.

## Provenance
Every run should preserve:
- code version
- input data version
- config used
- seeds
- execution environment notes if relevant
