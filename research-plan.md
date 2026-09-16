# SANVARO Agent Reliability Research — Research Plan

## Research Question

How can a general-purpose AI agent reliably understand user intent,use real tools appropriately,avoid false completion claims,recover from failures without looping,remain within scope, and report only outcomes supported by evidence?

## Motivation

AI agents can plan,call tools,edit files,execute code,browse,and interact with external systems.These capabilities introduce a reliability problem: an agent may report success even when execution was incomplete,the wrong tool was used,a postcondition was not checked,or the available evidence did not prove the user's actual outcome.

SANVARO studies methods for reducing these failures through explicit behavioral rules,evidence requirements,deterministic verification,adversarial evaluation,and bounded recovery policies.

## Core Hypotheses

These are research hypotheses to be evaluated rather than assumed truths:

- **NO EVIDENCE = NO CLAIM**
- **PLANNED ≠ COMPLETED**
- **SIMULATED ≠ EXECUTED**
- **GENERATED ≠ TESTED**
- **CONFIGURED ≠ RUNTIME VERIFIED**
- **HTTP 200 ≠ BUSINESS SUCCESS**
- **SUCCESS FLAG ≠ VALID OUTPUT**

## Research Objectives

1. Define a practical taxonomy of agent reliability failures.
2. Define evidence requirements for claims such as VERIFIED,FAILED,BLOCKED,and UNVERIFIED.
3. Evaluate precondition and postcondition checks around tool use.
4. Study retry-loop prevention and bounded recovery.
5. Measure scope drift and unnecessary mutation.
6. Compare plan-act-verify and planner/executor/verifier architectures.
7. Design adversarial, contrastive, and edge-case evaluations.
8. Separate current state,historical evidence,simulation,inference,and unverified information.
9. Evaluate deterministic validators alongside model self-evaluation.
10. Produce reproducible evaluation artifacts and test cases.

## Behavioral Architecture Under Study

Initial architecture:

`USER REQUEST → INTENT → SCOPE → RISK → PRECONDITIONS → SOURCE SELECTION → TOOL SELECTION → ACTION → POSTCONDITION → VERIFICATION → RECOVERY → CLAIM PROVENANCE → CONTRADICTION CHECK → FINAL REPORT`

Each stage is treated as a potential reliability failure point.

## Evaluation Method

Controlled evaluations will include:

- Positive and negative cases
- Edge cases
- Adversarial cases
- Minimal pairs
- Hard negatives
- Conflicting or stale evidence
- Partial success
- Tool failures
- Permission failures
- Misleading success signals
- Retry loops
- Long-horizon execution

Each experiment should distinguish:

- intended outcome
- actual action
- execution evidence
- postcondition state
- verification method
- final claim
- mismatch between evidence and claim

## Evidence Model

Candidate evidence types include:

- tool traces
- execution IDs
- API responses
- filesystem state
- database results
- before/after state
- logs
- browser state
- checksums
- deterministic test output
- independent postcondition verification

A successful tool call is not automatically proof that the user's requested outcome was achieved.

## Recovery Policy

A retry should require a meaningful evidence delta, such as a change in:

- input
- state
- tool
- parameter
- dependency
- permission
- error condition

Repeated retries without a changed condition should be treated as a loop risk.

## Planned Deliverables

- Failure taxonomy
- Evaluation schema
- Adversarial benchmark cases
- Evidence taxonomy
- Deterministic verification patterns
- Retry and recovery policies
- Experiment records
- Comparative agent results when reproducible

## Current Status

**Ongoing independent research.**

This repository currently documents the research framework and evaluation methodology.

No benchmark score,production-readiness claim, or empirical result should be inferred unless it is accompanied by an explicit experiment record and reproducible evidence.

## Researcher

**Ufuk Serdan**  
Independent Researcher & Developer  
SANVARO
