DANCO WORKFORCE ASSESSMENT — ADVANCED PROTOTYPE v26

SECONDARY / ADVANCED PROTOTYPE
This build is separate from the established Danco prototype and demonstrates additional recruitment, identity-readiness and background-screening workflow possibilities.

NEW / REFINED IN v26
- Applicant chooses after language selection: Danco Workforce Assessment or Apply to work at Danco.
- Administrator can lock the current browser/device to Workforce Assessment only, Application only, or Choice of either.
- Application form includes street address, city, state, ZIP, date of birth and Social Security number readiness.
- SSN structural validation with applicant warning/override reason flow.
- Enter PROTOTYPE in the SSN field for demonstration without entering a real SSN.
- Applications can be submitted to the shared review list without an administrator PIN.
- Manual result-code decoder removed from the administrator interface because submitted records are stored centrally.
- Background-check request is blocked when the stored application has no valid SSN readiness marker. Prototype bypass is accepted only for the demonstration workflow.

IMPORTANT SSN / PRIVACY DESIGN
This public prototype does NOT persist a full raw Social Security number in the normal Danco applicant record. It stores only validation/readiness status, masked last-four digits for structurally valid entries, prototype-bypass status, and any applicant-provided reason for proceeding without a valid number.

This is deliberate. A production screening integration should either:
1. pass the full SSN directly into the credentialed screening provider's protected candidate workflow, or
2. use a separately approved encrypted/restricted identity store that is inaccessible to the normal applicant-report workflow.

Do not use real applicant SSNs for public prototype demonstrations. Use PROTOTYPE.

LIVE SHARED BACKEND
Supabase Edge Function:
https://uneqycntlykjedaaynou.supabase.co/functions/v1/danco-service

The background-screening function remains demonstration-only until Danco has a credentialed CRA provider and production security/legal controls are approved.
