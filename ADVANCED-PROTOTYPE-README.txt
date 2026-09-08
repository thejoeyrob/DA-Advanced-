DANCO APPLICANT ASSESSMENT — ADVANCED PROTOTYPE v25

This is a SECONDARY prototype. It does not replace the current Danco prototype.

NEW DEMONSTRATION FEATURES
1. Commercial Account Manager role
   - Select Application Mode, then choose Commercial Account Manager.
   - The same five-question work-style primer is retained.
   - The timed ten-question assessment then switches to commercial-sales suitability.
   - The administrator report shows a 0–100% advisory suitability indicator, commercial strengths and an estimated sales approach.

2. Background-screening demonstration
   - Application Mode now records a background-screening consent response.
   - After a submitted application is opened in the protected administrator dashboard, use Request background check.
   - A cost-approval screen demonstrates Danco-funded provider billing.
   - No third-party provider is connected and NO CHARGE is made in prototype mode.
   - The prototype creates a background-screening record in Supabase and adds placeholder screening categories reading “Results will be displayed when live”.
   - The application automatically moves to CB checked · To action.
   - An administrator can then manually file it as CB checked · Eligible or CB checked · Not eligible.

3. Live-ready Supabase structure
   - Background-screening records are stored separately from applicant submissions.
   - The structure includes provider, provider request ID, package, approved cost, authorization status, results summary, provider report URL and decision fields.
   - When a screening provider is selected, its API adapter and secure secret credentials can be connected server-side without exposing keys in this PWA.

LIVE DATA ENDPOINT
https://uneqycntlykjedaaynou.supabase.co/functions/v1/danco-service

IMPORTANT
- This is an employment-screening demonstration only and does not run a real background check.
- The prototype’s “Eligible / Not eligible” folders are manual administrative workflow labels, not an automated hiring decision.
- A live provider must supply its required disclosure/authorization flow and compliance process.

DEPLOYMENT
Upload all files in this ZIP to the root of a SEPARATE GitHub Pages repository, for example:
thejoeyrob/Danco-Advanced-Prototype
Do not overwrite the existing production/prototype repository if you want to preserve both versions.

AUDIO NOTE
The existing roofing assessment retains the bundled recorded Danco narration. New Commercial Account Manager wording uses the device's language-aware speech fallback where a dedicated recorded clip does not yet exist. A production sales track can be supplied with the same dedicated neural narration treatment as the existing roofing assessment.
