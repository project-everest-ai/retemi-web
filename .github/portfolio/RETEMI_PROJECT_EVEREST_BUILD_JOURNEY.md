# Project Everest / Retemi — AI-Assisted Product Build Journey

**Role:** Founder / Enterprise Architect / Product and AI Safety Lead

**Company:** Project Everest LLC

**Product:** Retemi

**Public site:** https://myretemi.com/

> This public summary describes the architecture, engineering approach, and
> lessons learned from building Retemi. The application source repository and
> operational implementation details remain private.

## Overview

Retemi is a cross-platform general-wellness and healthspan product designed to
help a person bring together relevant context across sleep, nutrition,
movement, community, coaching, and caregiving so the next action can be more
useful and better grounded.

I used Project Everest / Retemi as a hands-on product-delivery and learning
journey in modern AI-assisted engineering. I combined more than three decades
of enterprise architecture and technology experience with current-generation
coding agents to move from product vision and architecture through mobile and
backend implementation, privacy boundaries, AI safety controls, automated and
physical-device testing, private store distribution, and controlled-pilot
readiness.

The product was developed through small, reviewable slices with explicit
boundaries, tests, evidence, and fail-closed controls. It remains pre-pilot:
this summary does not claim a production launch, legal approval, bound
insurance, Apple store distribution, real participant admission, or production
AI activation.

## What I Led

I retained human accountability for:

- product direction and scope;
- enterprise, application, data, and integration architecture;
- privacy, authorization, and relationship boundaries;
- AI safety posture and capability decisions;
- sequencing, acceptance criteria, review, and release decisions;
- controlled-pilot, legal, insurance, store, and operational coordination; and
- deciding what remained deferred or off.

AI coding agents supported the work through:

- repository inspection and evidence gathering;
- bounded implementation within defined architecture;
- test generation and regression expansion;
- constrained refactoring;
- documentation support; and
- validation assistance.

The agents did not independently design or approve architecture, safety,
privacy, legal, insurance, or release decisions. They became force multipliers
operating inside explicit human-defined boundaries.

## Product and Enterprise Architecture

Retemi uses a **person-first model**. Me, Caregiver, and Coach are perspectives
of one Person rather than separate identities. A perspective changes what the
current interaction is trying to accomplish; it does not silently change
identity, consent, ownership, or authorization.

Key architectural decisions include:

- separating identity, perspective, domain, request intent, context, and
  workspace;
- treating the Person as the owner of their healthspan information;
- maintaining one shared Ask Retemi interaction model across supported
  perspectives;
- modeling Organization as a membership-scoped workspace rather than another
  identity;
- keeping Community relationships separate from private wellness records; and
- providing useful general education without requiring exhaustive data
  collection.

These boundaries allowed Coach, Caregiver, Community, and Organization journeys
to reuse common identity, navigation, safety, and consent patterns without
granting access implicitly.

## Mobile and Backend Platform

Retemi is implemented as a Flutter/Dart application for Android and iOS with a
Supabase/PostgreSQL backend.

Implemented platform capabilities include:

- email authentication, confirmation, sign-in, sign-out, and password
  recovery;
- explicit environment selection with fail-closed boundaries;
- server-authoritative pilot access and named admission;
- an independently enforced participant cap;
- purpose-specific Person and product-domain data boundaries;
- PostgreSQL Row Level Security and tested cross-user isolation;
- authenticated server capabilities;
- participant withdrawal and deletion-request intake; and
- metadata-focused operational and release evidence.

Authentication is intentionally separate from admission. A valid account does
not by itself unlock protected pilot functionality, and password recovery does
not grant admission.

## AI Architecture and Safety

Retemi treats generative AI as a bounded component, not as the authority for
safety, access, or product policy.

The architecture places controls in this order:

`authentication → pilot admission → deterministic safety → authorization → minimized context → capability gate → structured generation → validation → display or deterministic fallback`

Important properties include:

- deterministic urgent and professional-review routing before ordinary
  generation;
- prohibited or higher-risk request classes bypassing ordinary AI synthesis;
- minimized, allowlisted context rather than unrestricted record access;
- separate Sleep, Nutrition, and Exercise capability controls;
- independent mobile and server gates;
- strict structured output and validation before display;
- kill-switch concepts for immediate domain or broader shutdown; and
- deterministic guidance when AI is disabled, unavailable, invalid, or not
  approved.

Coach planning remains deterministic for the controlled pilot scope. Caregiver
support is session-bounded and excludes another person's identity or private
wellness record. The design demonstrates bounded AI paths without implying that
AI has been activated for real participants or production.

## AI Usage Governance

AI governance was designed as one operational control plane spanning safety,
reliability, cost, and abuse prevention.

The design covers:

- request, token, and pilot-wide usage limits;
- independent domain and global shutdown controls;
- fail-closed capability behavior;
- deterministic fallback for configuration, provider, timeout, schema,
  validation, or audit failure;
- release evidence connecting reviewed software, artifacts, and approvals;
- operator review before re-enablement; and
- response reporting limited to an opaque operational reference and a bounded
  reason.

Operational observability is metadata-focused. The reporting design avoids
turning operational evidence into another wellness record by excluding raw
questions, prompts, generated answers, conversations, identities, and health
context.

## Privacy and Authorization Architecture

Privacy was treated as product architecture rather than a policy layer added at
the end.

The principal boundaries are:

- relationship does not equal authorization;
- a Coach, Caregiver, Community connection, or Organization membership does
  not automatically grant access to private wellness information;
- another Person's information requires distinct permission and sharing
  boundaries;
- Community participation remains separate from health facts;
- Organization roles are scoped to one workspace and do not alter identity;
- participant-owned records are isolated through database policy; and
- temporary context is distinguished from deliberately saved context.

Participant exit is intentionally split:

- **Leave the pilot** revokes access without claiming data was deleted.
- **Request account and data deletion** records the request and revokes access,
  without claiming destructive completion before policy is approved.

## Release Engineering and Testing

Delivery used narrow implementation slices with explicit checkpoints. Each
meaningful slice was expected to preserve architecture, add focused tests, run
broader regression, and produce a reviewable diff and evidence record.

At the integrated pilot-candidate checkpoint, engineering evidence recorded:

- **613 Flutter tests passed**;
- **149 server tests passed**;
- **114 focused integrated acceptance tests passed**;
- **21 release-evidence tests with 46 assertions passed**;
- clean formatting and static analysis; and
- passing credential and sensitive-content checks for the candidate changes.

Coverage included authentication, admission, deterministic safety,
perspective/domain routing, privacy boundaries, cross-user isolation,
default-off behavior, structured validation, Community, Organizations, Coach,
Caregiver, Getting Started, participant exit, and AI response reporting.

These tests establish behavior against encoded cases. They do not prove
clinical safety, legal compliance, comprehensive security, or suitability for
every possible participant.

## Physical Device and Store Distribution

Controlled, fabricated accounts were used on physical Android and iPhone
devices to validate:

- account creation, confirmation, and password recovery;
- the authenticated-but-not-admitted boundary;
- server-authoritative admission changes;
- deterministic guidance with AI off;
- safety canaries and false-positive controls;
- save/check-in, Home, Insights, and domain switching;
- Me, Caregiver, Coach, Community, and Organization navigation;
- withdrawal and immediate loss of protected access; and
- cleanup back to zero test accounts, admissions, fabricated records, and
  provider invocations.

The shared physical regression passed 13 scenario groups on both platforms.
Manual reviews also covered launch, iconography, safe areas, larger text,
keyboard behavior, back navigation, and obvious clipping or overflow.

Google Play Internal Testing was completed using the permanent Android package
identity. A fresh Play-installed copy was tested after uninstalling the earlier
copy and disconnecting the device from the development Mac. The application
independently reached the hosted pilot service, completed authentication and
recovery, and enforced the server-side not-admitted boundary.

Closed, open, and production Google Play releases were not started. Physical
iPhone development validation was completed, but TestFlight/App Store
distribution is not claimed as complete.

## Pilot Governance and Operational Readiness

Pilot readiness was treated as a multidisciplinary release decision rather
than simply whether the app runs.

Implemented or rehearsed controls include:

- named participant admission and revocation;
- a server-authoritative cohort cap and default-deny state;
- withdrawal and deletion-request intake;
- admission and pilot-pause controls;
- independent AI domain shutdown;
- release evidence and artifact identification;
- restricted operator administration;
- password-recovery support boundaries;
- non-destructive incident containment and evidence preservation; and
- verified synthetic-data cleanup.

Technical rehearsals ended with no real participants, no active admissions, no
provider invocations, AI capabilities off, and the participant cap restored to
default deny. Final ownership, policy decisions, approvals, and release
evidence remain necessary before a real controlled pilot.

## Public Trust, Legal, Insurance, and Trademark Readiness

The work extended beyond application code into the supporting trust and
business-readiness system.

High-level readiness work included:

- a standalone public website covering the product, roles, pilot, trust, AI,
  and account/data topics;
- participant-facing general-wellness and AI limitations;
- privacy, consent, pilot-participation, retention, deletion, and incident
  topics prepared for qualified review;
- underwriter-facing summaries of AI controls and testing;
- Apple and Google privacy/data-safety readiness;
- brand, domain, and trademark-readiness work; and
- support, privacy, and operational contact paths.

These are readiness activities, not approvals. Final legal language requires
qualified review and business approval. Insurance is not represented as bound,
and trademark clearance or registration is not claimed.

## How I Used AI-Assisted Development

My working method evolved into a repeatable pattern:

1. Define the product, architecture, privacy, and safety boundary first.
2. Require the coding agent to inspect the actual repository and evidence.
3. Give one narrowly scoped objective at a time.
4. State what must not change.
5. Require implementation within existing dependency and authorization
   direction.
6. Require tests, static analysis, security checks, and a reviewable diff.
7. Stop after each meaningful slice and record the outcome.
8. Use fabricated data for live rehearsals and independently verify cleanup.
9. Keep high-risk capabilities off until the corresponding gate is complete.
10. Preserve human review and explicit approval for risk and release decisions.

This shifted AI from an unconstrained code generator to a controlled
engineering collaborator operating inside a governed delivery system.

## Key Architecture and Engineering Lessons

### AI accelerates architecture; it does not replace it

Clear dependency direction, typed domain models, explicit authorization, and
testable acceptance criteria made coding agents faster and more reliable.

### Small prompts outperform giant rewrites

Constrained slices created better reviews, stronger evidence, and safer
rollback points than broad multi-domain instructions.

### Safety belongs outside the model

A generative model should not decide whether it may answer. Deterministic
safety, admission, authorization, context selection, and capability checks
should run first, with independent validation afterward.

### AI off is a product capability

Retemi remains useful when AI is disabled, unavailable, unsafe, too expensive,
or not yet approved. Deterministic fallback is architecture, not an error
screen.

### Relationship is not permission

Coach, Caregiver, Community, and Organization work repeatedly showed that a
relationship must not imply access to private participant context.

### Evidence must distinguish implementation from activation

Code and passing tests do not prove deployment, live configuration, legal
approval, insurance coverage, or release authorization. Those states require
separate evidence.

### Human judgment remains the control point

AI agents can inspect, implement, test, and document quickly. The architect
must still define intent, resolve tradeoffs, evaluate evidence, and accept or
reject the result.

## Technologies and Practices

**Product and mobile**

- Flutter and Dart
- Android and iOS
- Google Play Internal Testing
- physical-device and accessibility-oriented validation

**Backend and data**

- Supabase and PostgreSQL
- Row Level Security
- authenticated server capabilities
- authentication and password recovery
- server-authoritative admission and feature controls

**AI and governance**

- structured AI generation
- deterministic safety routing
- minimized, allowlisted context
- independent capability gates and kill switches
- server and client validation
- deterministic fallback
- metadata-focused observability
- bounded response reporting
- token, rate, and pilot-wide usage budgets

**Engineering and operations**

- Git and GitHub
- branch-based incremental delivery
- automated testing and static analysis
- credential and sensitive-content scanning
- architecture decision records
- release evidence
- physical-device harnesses
- operator and incident readiness

**Business and risk**

- controlled Texas pilot governance
- privacy and sensitive-information-consent design
- legal and regulatory issue identification for qualified review
- cyber and technology E&O underwriting preparation
- Apple and Google developer-program readiness
- public trust and brand/trademark readiness

## Selected Delivery Milestones

1. **Architecture foundation and Person model** — established Person ownership,
   progressive context, and a modular product direction.
2. **Bounded wellness journeys** — implemented value-first Sleep, Nutrition, and
   Exercise experiences with optional context.
3. **Multiple perspectives** — added Me, Caregiver, and Coach while preserving
   one identity and preventing implicit access to another Person's data.
4. **Community and Organization boundaries** — implemented permissioned
   relationships and membership-scoped workspaces.
5. **Deterministic safety and bounded AI** — placed safety and authorization
   before generation, with minimized context, validation, and fallback.
6. **Independent AI controls** — added default-off domain capabilities,
   shutdown controls, metadata-focused observability, and release evidence.
7. **Pilot access and participant lifecycle** — implemented authentication,
   admission and cap controls, withdrawal, and deletion-request intake.
8. **AI response reporting** — implemented an opaque-reference, bounded-reason
   concept without storing raw questions, answers, or health context.
9. **Integrated pilot candidate** — passed the 613-test Flutter suite, 149-test
   server suite, focused acceptance, analysis, and security gates.
10. **Android and iPhone physical closure** — validated recovery, admission,
    all-off behavior, withdrawal, and cleanup on both platforms.
11. **Operator and incident readiness** — rehearsed admission, caps, revocation,
    pause controls, AI shutdown, and evidence preservation.
12. **Google Play Internal distribution** — proved the internal build could run
    independently of the development Mac and enforce server-side admission.
13. **External-gate preparation** — prepared public trust, legal, insurance,
    store, support, and brand-readiness materials while keeping open decisions
    explicit.

## Resume-Supplement Summary

**Project Everest LLC / Retemi — Founder, Enterprise Architect and AI Product
Lead**

Led the architecture and AI-assisted development of a cross-platform
healthspan/general-wellness product from concept through controlled-pilot
readiness. Designed a Flutter/Supabase platform with person-first identity,
server-authoritative admission, privacy-preserving perspective and workspace
boundaries, Row Level Security, deterministic safety routing, minimized AI
context, independent domain controls, structured generation and validation,
metadata-focused observability, bounded response reporting, and deterministic
fallback. Directed incremental coding-agent delivery through
repository-grounded prompts, automated tests, architecture checkpoints,
security reviews, fabricated-data rehearsals, physical Android/iPhone
validation, operator-readiness exercises, and Google Play Internal Testing.
Extended the work beyond software implementation into privacy and AI
governance, legal and insurance preparation, store readiness, public trust, and
brand/trademark readiness.

The project demonstrates how an experienced enterprise architect can use AI
coding agents as force multipliers while retaining human accountability for
product direction, architecture, safety, privacy, risk, evidence, and release
decisions.
