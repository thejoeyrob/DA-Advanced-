# Danco Workforce Assessment - Advanced Prototype v27 implementation brief

## Purpose
A secondary, progressive Danco recruitment prototype that preserves the established bilingual application/assessment experience while adding structured sales suitability, applicant-specific interview direction, background-screening orchestration and employment-contract workflow demonstration.

## Standard assessment/application layer
- User-selected route after language: **Danco Workforce Assessment** or **Apply to work at Danco**.
- Administrator device lock: Workforce Assessment only, Application only or Choice of either.
- English / Spanish journeys, work-style/DISC primer and role-specific assessment.
- Roles: Service Helper, Roofer, Foreman and Commercial Account Manager.
- Commercial Account Manager uses the established ten-question suitability model with rebalanced concise answer wording. Scoring concepts and outcome model are preserved.
- Administrator report begins with a candidate-specific overall suitability brief and ends with four short assessment-led interview prompts with fact-finding tags.
- Applicant submissions are PIN-free; administrator review remains protected.

## Narration
The established Danco recorded narration sprites are preserved and their manifest contains a verified 0.300-second minimum gap with no overlapping clip boundaries. When revised/dynamic content does not have an exact recorded clip, the app routes the whole prompt to the device's English or Spanish system reader so a question never mixes voices mid-prompt. Help also lets the user select **Danco recorded** or **Device reader** for the whole journey.

## Background-screening layer
Application mode captures address, city, state, ZIP, date of birth and SSN readiness. The normal applicant record never stores the full raw SSN. Background-screening demonstration remains administrator-controlled and requires cost approval. Prototype `PROTOTYPE` bypass is supported; live provider mode must require real provider-approved identity data.

Background queues:
- CB checked - To action
- CB checked - Eligible
- CB checked - Not eligible

## Employment-contract layer
From a stored application report, an administrator can select **Create employment contract**. The workflow asks whether the candidate's background check meets Danco criteria. A No response blocks contract creation and directs the reviewer to senior staff. A Yes response opens a four-role offer selector and a pre-filled offer/contract form.

The contract prototype captures offer-specific fields including employment type, FLSA classification, start date, compensation, pay frequency, work location, reporting line, schedule, introductory period, benefits/PTO, overtime, travel/vehicle requirements and additional offer terms. The generated document matches the visual language of the Danco report and can be printed/saved as PDF.

Creating a contract automatically files the record in **Employment contracts**.

## Signed-contract file store
**Signed employment contracts** is upload-only. It accepts PDF, JPEG or PNG scanned signed contracts up to the prototype limit of 8 MB. Upload writes the file to a private Supabase Storage bucket, records an audit trail and moves the applicant into the Signed employment contracts queue. Generic queue controls cannot move a record into either contract queue.

## Security boundary
- Full raw SSNs are excluded from the normal Danco database record.
- Supabase secret/service credentials remain server-side.
- Signed contract files are held in a private bucket and opened through short-lived signed URLs.
- This is a prototype workflow; Danco HR/counsel should approve final employment contract wording and production retention/access rules.
