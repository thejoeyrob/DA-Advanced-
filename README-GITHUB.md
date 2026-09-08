# Danco Workforce Assessment — Advanced Prototype v26

This is the flat GitHub Pages / PWA package for the **secondary advanced Danco prototype**.

## What this version demonstrates
- User-selected route after language: **Danco Workforce Assessment** or **Apply to work at Danco**.
- Administrator device lock: workforce-assessment only, application only, or user choice.
- English / Spanish assessment journey, recorded narration, accessibility support and existing roofing assessment.
- Commercial Account Manager role-specific sales-suitability assessment.
- Shared Supabase submissions and administrator queues.
- Application identity-readiness fields: address, city, state, ZIP, DOB and SSN readiness.
- SSN structural validation, exception/reason workflow and `PROTOTYPE` bypass for demonstrations.
- Background-screening demonstration with cost approval and CB checked workflow queues.

## Deploy
Upload **every file in this ZIP** to the root of a dedicated GitHub Pages repository. Keep this advanced build separate from the established Danco prototype.

GitHub Pages: Settings → Pages → Deploy from a branch → `main` → `/ (root)`.

## Important prototype privacy rule
Do **not** enter a real Social Security number while demonstrating this public prototype. Enter `PROTOTYPE` instead.

The ordinary Danco shared applicant record does not persist a full raw SSN. It stores only readiness status, masked last four digits for structurally valid entries, prototype-bypass state, and an exception reason if the applicant proceeds without a valid number.

A production CRA integration must use a provider-hosted secure identity flow or a separately approved encrypted/restricted identity handoff. The public PWA must never contain a CRA secret key or Supabase secret/service-role key.
