# Unified Account Lockdown & Recovery App — Product Brief

## Vision
Create a security-first personal app that lets a user protect multiple online accounts from one dashboard. If a suspicious login is detected on any connected account, the app can trigger a coordinated lockdown across all linked accounts and require strong multi-step recovery.

## Core Concept
- **One security control center:** user links supported accounts (email, social, banking, productivity, cloud).
- **Coordinated lockdown:** an unapproved high-risk login event on one account can trigger a global account protection workflow.
- **3-step recovery verification:**
  1. Master code/passphrase.
  2. One-time code sent to verified phone number.
  3. Face verification on trusted device.
- **Personal dashboard:** account health, risk alerts, session controls, and audit history.
- **Time + scheduling layer:** daily planner, security tasks, credential rotation reminders, and incident follow-ups.

## Important Reality Check
A third-party app cannot literally lock **every** account on the internet unless each service offers supported APIs or enterprise identity hooks. The realistic implementation is:
- Direct integrations where APIs exist (OAuth, security events, session revoke endpoints).
- Browser extension / password manager assists for partially supported services.
- Manual guided actions for unsupported services.

## User Personas
- **Security-conscious individuals** with many personal accounts.
- **Creators/freelancers** managing multiple business logins.
- **Parents/families** wanting incident response and visibility.

## MVP Scope (Phase 1)
1. **Account Linking**
   - OAuth-based linking for initial providers (Google, Microsoft, Apple where permitted).
   - Encrypted token vault.
2. **Risk Event Pipeline**
   - Ingest suspicious-login alerts from connected providers.
   - Risk scoring engine with configurable policies.
3. **Global Lockdown Playbook**
   - Revoke sessions.
   - Force re-authentication.
   - Freeze sensitive actions where supported.
4. **Recovery Flow (3-Step Verification)**
   - Master code.
   - SMS OTP.
   - Face match liveness check.
5. **Unified Dashboard**
   - Real-time status per account.
   - Lockdown history.
   - Active sessions map.
6. **Scheduling Module**
   - Security checkup reminders.
   - Time-block planner for daily tasks.
   - Incident follow-up tasks.

## System Architecture (High Level)
- **Client Apps:** iOS, Android, Web dashboard.
- **API Gateway:** auth, policy evaluation, orchestration.
- **Identity & Key Management:** master key derivation, secrets vault, HSM/KMS.
- **Integration Connectors:** provider-specific APIs/webhooks.
- **Risk Engine:** behavior analytics, geovelocity, device trust.
- **Incident Orchestrator:** executes lockdown playbooks.
- **Audit Ledger:** immutable event history.
- **Planner Service:** tasks, reminders, calendar sync.

## Security Requirements
- End-to-end encryption for highly sensitive user secrets.
- Device binding and hardware-backed key storage where possible.
- Zero-trust service-to-service authentication.
- Rate limiting + anti-bruteforce on recovery flows.
- Liveness detection for facial step (anti-spoof checks).
- Continuous penetration testing and red-team exercises.

## Compliance & Legal Considerations
- Data privacy compliance (GDPR/CCPA where applicable).
- Biometric data handling policy and user consent.
- Telecom/SMS compliance and fraud controls.
- Clear liability and support policies for account recovery failures.

## Non-Functional Requirements
- High availability for incident response path.
- Fast execution target for global lockdown triggers.
- Explainable alert decisions and user override options.
- Accessible UX with clear emergency workflows.

## Key Risks
- Limited provider API support.
- False positives causing unwanted lockouts.
- SIM-swap risk affecting SMS factor.
- Biometric spoof attempts.

## Risk Mitigations
- Tiered policy modes (monitor, suggest, enforce).
- Backup recovery factors (hardware key, recovery contacts).
- Carrier-change detection and cool-down periods.
- Optional human review for high-value accounts.

## Suggested Tech Stack
- **Frontend:** React/Next.js web + React Native mobile.
- **Backend:** Node.js/TypeScript or Go microservices.
- **Data:** PostgreSQL + Redis.
- **Messaging:** Kafka or SQS/SNS.
- **Security:** KMS/HSM-backed encryption, WebAuthn/FIDO2 support.
- **Observability:** OpenTelemetry + SIEM integration.

## 90-Day Build Plan
- **Weeks 1–2:** product discovery, threat model, provider feasibility matrix.
- **Weeks 3–6:** core auth, token vault, provider connectors, dashboard skeleton.
- **Weeks 7–9:** risk engine + lockdown orchestration.
- **Weeks 10–11:** 3-step recovery, facial liveness flow.
- **Week 12:** pilot test, security hardening, go/no-go review.

## Success Metrics
- Mean time to lockdown after confirmed suspicious event.
- False positive lockdown rate.
- Recovery success rate without support intervention.
- Number of linked accounts per active user.
- Weekly active usage of planner + security reminders.

## Next Deliverables
1. Product requirements document (PRD) with user stories.
2. Provider integration matrix (what can/cannot be auto-locked).
3. Security architecture diagram and threat model.
4. Clickable UX prototype for the dashboard and emergency flow.
