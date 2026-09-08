# Danco Advanced Prototype v26 — Supabase backend notes

Project Edge Function: `danco-service` — version 3.

## Submission contract
`POST /api/submissions`
- Applicant submission no longer requires an administrator PIN.
- The backend sanitizes application data before storage and strips common raw-SSN field names as a defense-in-depth measure.
- Stored application identity metadata may include `ssnStatus`, `ssnLast4`, `ssnPrototypeBypass`, exception reason, DOB and address fields.
- Full raw SSN is not stored in the normal `danco_submissions.application` JSON.

## Administrator contract
`POST /api/admin`
- Remains administrator-PIN protected.
- Supports all standard and CB checked queues.

## Background screening contract
`POST /api/background`
- Remains administrator-PIN protected.
- Quote/request checks SSN readiness before proceeding.
- In prototype mode, a structurally-valid SSN marker or `PROTOTYPE` bypass can demonstrate the workflow.
- In future live-provider mode, the prototype bypass is not accepted.
- Missing/invalid SSN returns HTTP 422 with code `SSN_REQUIRED_FOR_BACKGROUND_CHECK`.

`danco_background_screenings` now includes:
- `ssn_status`
- `ssn_last4`
- `identity_summary` JSONB

No raw full SSN should be written to these fields.

## Production CRA integration
A credentialed provider adapter must be added server-side. The full SSN should be passed through an approved provider-hosted flow or separately approved encrypted/restricted identity handoff. CRA and Supabase secret/service-role credentials must remain server-side only.
