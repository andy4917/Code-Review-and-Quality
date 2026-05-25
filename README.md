# Code Review and Quality

## Overview
This skill implements a multi-dimensional code review process with strict quality gates. Every single change must be reviewed before merging to the main branch. Approvals are granted if the change definitely improves overall code health.

## When to Use
- Before merging any PR or code modification
- After completing a feature implementation or refactoring existing code
- When evaluating code produced by another agent, model, or human
- After any bug fix to review both the fix and its regression test

## The Five-Axis Review Criteria
1. **Correctness**: Checks spec alignment, boundary/edge cases, error paths, and test efficacy.
2. **Readability & Simplicity**: Ensures clear naming, straightforward control flow, abstraction justification, and dead code hygiene.
3. **Architecture**: Assesses system design compliance, module boundaries, duplication, and dependency direction.
4. **Security**: Verifies input sanitization, parameterized SQL queries, secret preservation, and untrusted external data boundaries.
5. **Performance**: Inspects for N+1 query patterns, unconstrained data fetching, missing pagination, and synchronous blocks.

## Change Sizing & Splitting
- **~100 lines**: Good / **~300 lines**: Acceptable for a single logical change / **~1000 lines**: Too large (must be split).
- Refactoring and feature additions must be submitted as two separate changes.
- Splitting strategies include: Stack, By file group, Horizontal, and Vertical.

## Finding Severities
All comments must be categorized to establish clear expectations for authors:
- *(No prefix)*: Required change before merge.
- **Critical:**: Blocks merge due to security flaws, data loss, or broken behavior.
- **Nit:**: Minor, optional formatting or style preference.
- **Optional: / Consider:**: Non-mandatory suggestion.
- **FYI**: Informational context with no action required.

## Hard Rules & Red Flags
- Never rubber-stamp reviews with a blind "LGTM" or accept "I'll clean it up later".
- Always prioritize technical facts, style guides, and engineering principles over personal preference.
- Explicitly identify unreachable or orphaned code, list it, and ask before executing any deletion.
