# Danco Workforce Assessment — Advanced Prototype v26 implementation brief

## Purpose
A secondary prototype demonstrating how the established Danco recruitment assessment can expand into a workforce-assessment/application entry point, role-specific sales screening and an administrator-controlled background-screening workflow.

## Entry routes
After language selection the default device mode offers:
1. **Danco Workforce Assessment** — suitable for existing employees, refresher/internal assessment and assessment-only use.
2. **Apply to work at Danco** — application form followed by work-style questions and the appropriate role assessment.

An administrator can lock a browser/device to Workforce Assessment only, Application only, or Choice of either.

## Application identity readiness
Application mode captures street address, city, state, ZIP code, date of birth and SSN readiness. The SSN field performs structural plausibility checks. Invalid/missing entries can proceed only after an explicit warning and recorded reason. `PROTOTYPE` is the safe demonstration bypass.

The normal shared applicant record never stores a full raw SSN. For a valid entry it stores only a masked last-four reference and readiness state. A production CRA implementation requires a secure direct/provider-hosted identity handoff.

## Submission
Completed records submit directly to the shared Supabase workflow without requiring an applicant to know the administrator PIN. Administrator browsing, status changes and background-screening actions remain protected.

## Background screening
Danco's prototype rule is enforced: a background-screening quote/request cannot proceed without SSN readiness. In prototype mode `PROTOTYPE` is accepted. A future live provider mode must require real provider-validated identity data; the bypass will not satisfy a live request.

No real CRA is called and no charge is made in prototype mode.

## Administrator workflow
Standard queues:
- Yet to process
- Actioned
- Archived

Background-screening queues:
- CB checked · To action
- CB checked · Eligible
- CB checked · Not eligible

The manual result decoder has been removed from the interface because deliberately submitted records are stored centrally and retrieved from the shared list.
