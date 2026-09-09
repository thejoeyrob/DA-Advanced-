# Danco Workforce Assessment — Standard + Danco+ Prototype v29

Flat GitHub Pages PWA containing the current Standard Danco Workforce Assessment and the owner-approved Danco+ demonstration layer.

## Standard
- English / Spanish assessment and application journeys.
- DISC/work-style primer for all roles.
- Roofing progression assessment for Service Helper, Roofer and Foreman.
- Commercial Account Manager sales-suitability assessment with balanced answer wording.
- Candidate-specific suitability brief and four interview-direction prompts.
- Recorded Danco narration with device-reader fallback / selectable device voice.
- Live shared submissions and protected administrator review.

## Danco+
- Owner-approved device trial access with Standard / Danco+ presentation toggle.
- Restored background-screening approval window.
- Checkr and GoodHire public package-price references for prototype demonstration:
  - Basic — $29.99
  - Essential — $59.99
  - Complete — $94.99
  - court/database pass-through fees may apply in real vendor use.
- Prototype-only selectable successful / unsuccessful screening outcome so both workflow branches can be demonstrated.
- Successful demo screenings file automatically to Background checked — Eligible.
- Unsuccessful demo screenings flag an error, block contract creation and file automatically to Background checked — Not eligible.
- In a live release the app must not manufacture a result: provider data is returned through the approved integration and Danco completes the required human review.
- Employment agreement creation is permitted without a Danco+ screening record if the administrator confirms a satisfactory background check was received through another approved source.
- Expanded Danco employment-agreement / offer-terms prototype with optional fields and PDF printing.
- Bank account and routing details are deliberately excluded from the agreement; payroll/direct-deposit information belongs in a separate secure payroll onboarding process.
- Employment contracts and upload-only Signed employment contracts filing remain in the private Danco workflow.

## Deployment
Upload all files in the full package to the repository root, or use the update-only ZIP to replace changed files in an existing v28.1 deployment.

The PWA uses:
- `danco-service-v5` for v29 background/contract behavior while proxying unchanged Standard endpoints to the established service.
- `danco-plus-access` for owner-approved Danco+ trial requests.

## Prototype privacy
Do not enter a real Social Security number in a public demonstration. Use `PROTOTYPE`.

The ordinary applicant record excludes the full raw SSN. Signed employment files remain in private Supabase Storage and are opened through time-limited signed links.
