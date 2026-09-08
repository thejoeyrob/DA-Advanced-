# Danco Advanced Prototype — Supabase backend notes

The advanced prototype uses the existing Danco Supabase project and the `danco-service` Edge Function.

## Additive schema now present

### `danco_submissions`
The existing shared-submission table retains the original queues and adds:

- `background_to_action`
- `background_eligible`
- `background_not_eligible`

It also includes `assessment_track`:

- `roofing`
- `account_manager`

### `danco_background_screenings`
A separate protected table stores screening workflow metadata, including:

- submission reference / relation
- prototype-demo or live-provider mode
- provider and provider request ID
- screening package
- approved cost / currency / possible pass-through fees
- administrator approval details and timestamps
- authorization status
- screening status
- structured minimal results summary
- optional provider report URL
- manual review decision and note

RLS is enabled with no browser policies. Access is via the protected Edge Function only.

## Edge Function actions used by this PWA

`POST /api/background`

- `action: quote` — returns the demonstration screening package/cost
- `action: request` — creates the prototype screening record after cost approval and moves the submission to Background checked · To action
- `action: get` — retrieves the latest screening status/summary for the protected report
- `action: decision` — files the record as Eligible, Not eligible or To action

The original `/api/submissions` and `/api/admin` contracts remain available to the existing prototype.

## Provider go-live hook

No real provider is selected in this build. Once Danco has a credentialed screening-provider account, the server-side provider adapter should be connected inside the Edge Function. Provider API credentials must remain in Supabase Edge Function secrets and must never be shipped in this PWA or GitHub.

The intended live flow is:

1. Danco administrator reviews the applicant result.
2. Administrator approves the provider quote in the Danco interface.
3. Edge Function creates the provider screening request.
4. Provider collects any required sensitive PII and formal disclosure/authorization in its own secure candidate flow.
5. Provider webhook/API status updates the Danco screening record.
6. Danco stores the minimal agreed screening status/summary and provider reference in its database.
7. A Danco administrator makes the hiring workflow decision; the system does not auto-reject applicants.

## Prototype safety

The current `request` action runs in `prototype_demo` mode. It creates no third-party request and incurs no charge. Each displayed screening category deliberately says **Results will be displayed when live**.
