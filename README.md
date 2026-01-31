# ADR

**Architecture Decision Record (ADR) – Financial Services Grade**

**ADR Template (Optimized for Regulated Banks)**
1. Title

Clear, unique, and decision-oriented.

**ADR-014: Standardize External API Ingress Using AWS API Gateway**

2. Status

Proposed

Accepted

Superseded

Deprecated

3. Context

Describe why the decision is required.

Include:

Business drivers

Regulatory / security constraints

Current-state challenges

4. Decision

State the decision clearly and concisely.

“We will …”

No ambiguity. No implementation detail overload.

5. Alternatives Considered
Option	Reason Not Selected
Option A	Reason
Option B	Reason

Demonstrates due diligence (important for audits).

6. Risk & Control Considerations

Mandatory for financial institutions

Data Classification: Public / Internal / Confidential / Restricted

Regulatory Impact: SOX / PCI / GDPR / SOC2 (as applicable)

Security Controls: AuthN, AuthZ, encryption, logging

Risk Assessment: Low / Medium / High

7. Consequences

Positive

Benefits

Negative

Trade-offs

Constraints introduced

Shows conscious risk acceptance, not accidental risk.

8. Ownership & Approvals

Decision Owner:

Reviewers: Security, Risk, Infra, Data

Approval Date:

Critical for accountability in banks.

9. Revisit Criteria / Follow-ups

Regulatory change

Security incident

Scale or cost threshold breach

Technology deprecation

Prevents “set and forget” architecture.

Example ADR (Realistic Banking Use Case)
ADR-021: Adopt AWS PrivateLink for Cross-Account Service Access
Status

Accepted

Context

Multiple application teams require access to shared platform services (e.g., pricing, reference data) hosted in separate AWS accounts.
Current access patterns rely on VPC peering and public endpoints, increasing:

Network blast radius

Security review complexity

Operational overhead

The organization requires a secure, auditable, least-privilege connectivity model aligned with internal security policies.

Decision

We will use AWS PrivateLink as the standard mechanism for cross-account and cross-VPC service access for internal platform services.

Public endpoints will be disallowed unless explicitly approved by Security Architecture.

Alternatives Considered
Option	Reason Not Selected
VPC Peering	Large blast radius, complex routing
Transit Gateway	Overkill for point-to-point services
Public ALB + WAF	Increased exposure and compliance effort
Risk & Control Considerations

Data Classification: Confidential

Regulatory Impact: SOX, internal data residency policies

Security Controls:

Private connectivity (no internet exposure)

IAM-based service access

VPC Flow Logs enabled

Risk Level: Low

Security Architecture review completed and approved.

Consequences

Positive

Reduced network blast radius

Strong service isolation

Simplified security approvals

Negative

Additional cost per endpoint

Requires service interface standardization

Ownership & Approvals

Decision Owner: Enterprise Cloud Architecture

Reviewers: Security Architecture, Network Engineering

Approval Date: 12-Jan-2026

Revisit Criteria / Follow-ups

If service latency exceeds SLA

If AWS pricing model changes significantly

If regulatory guidance changes on internal connectivity
