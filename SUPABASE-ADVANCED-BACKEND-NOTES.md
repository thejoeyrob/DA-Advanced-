# Danco Advanced Prototype v27 - Supabase backend notes

Project Edge Function: `danco-service` - version 4.

## Applicant submissions
`POST /api/submissions`
- No administrator PIN required from applicants.
- Raw/full SSN field names are stripped before normal application storage.

## Administrator
`POST /api/admin`
- Administrator-PIN protected.
- Queues: standard, CB checked, Employment contracts and Signed employment contracts.
- Generic status updates cannot manually place records into either contract queue.

## Background screening
`POST /api/background`
- Administrator-PIN protected.
- Preserves SSN-readiness enforcement, cost approval and prototype screening records.
- A production CRA adapter remains a separate go-live step.

## Employment contracts
`POST /api/contracts`
- Administrator-PIN protected.
- `create`: requires explicit confirmation that the background check meets Danco criteria, a stored background-screening record and one of the four Danco roles. Stores offer fields and automatically files to `employment_contracts`.
- `upload_signed`: accepts PDF/JPEG/PNG (prototype max 8 MB), stores to private bucket `danco-signed-employment-contracts`, records uploader/file audit metadata and automatically files to `signed_employment_contracts`.
- `signed_url`: returns a short-lived signed download URL for an existing signed file.

## Data/security boundary
`danco_employment_contracts` has RLS enabled and direct anon/authenticated privileges revoked. Application data continues to flow through the Edge Function. The signed-contract bucket is private. Secret/service-role credentials remain server-side only.
