# FYP Research Journey

## My Goal

I am a BSCS student working toward an FYP that combines **Cloud, AWS, Cybersecurity, and AI**. I wanted a project that was technically meaningful, feasible for a small student team, useful in the real world, and strong enough to demonstrate practical engineering rather than simply combining existing APIs.

My goal was not to choose the first interesting idea. I wanted to **stress-test each idea before committing to it**.

---

## Ideas Investigated

### 1. AI-Powered Network Intrusion Detection System on AWS

My initial direction was an AWS-based network intrusion detection system using machine learning.

The proposed architecture involved:

* CICIDS2017 dataset
* Amazon S3
* SageMaker
* XGBoost / Random Forest
* Model evaluation
* SageMaker endpoint
* API Gateway + Lambda
* Cloud-based deployment

This was technically feasible and strongly connected to AWS and AI, but I became concerned about originality and whether it offered enough differentiation from existing intrusion-detection research and products.

---

### 2. Cloud Cost & Security Platform

The next idea was a platform combining:

* AWS cost monitoring
* Security findings
* Anomaly detection
* Security/cost correlation
* Automated investigation

Initially this looked attractive because it connected AWS, security, and AI.

However, deeper investigation showed substantial overlap with capabilities already available through AWS services such as Cost Anomaly Detection, Trusted Advisor, Security Hub, GuardDuty, Config, and newer AI-assisted investigation capabilities.

The proposed "cost-security correlation" angle therefore did not appear sufficiently defensible as a standalone FYP contribution.

**Decision: Rejected.**

---

### 3. Smart Secrets Scanner for CI/CD

Another idea was an AI/security-oriented secrets scanner for source code and CI/CD pipelines.

The concept involved:

* Secret detection
* Git repositories
* CI/CD integration
* Security analysis
* Automated remediation

The problem was that this space is already heavily developed. GitHub and security companies such as GitGuardian were already moving toward AI-agent/MCP-aware secret detection and remediation.

The project risked becoming another implementation of an already mature capability.

**Decision: Rejected.**

---

## 4. Sovereign Data Gateway

The strongest remaining direction became a **privacy-preserving gateway for cloud AI**.

The basic concept is:

```text
User
  ↓
Privacy Gateway
  ├── PII Detection
  ├── Policy Engine
  ├── Tokenization / Redaction
  └── Local Secure Vault
  ↓
Protected Request
  ↓
Cloud AI
  ↓
Response Processing
  ↓
User
```

For example, if a user sends:

> My name is Ahmed and my CNIC is 35202-1234567-1.

The gateway could transform it into:

```text
My name is <PERSON_001>
and my CNIC is <CNIC_001>.
```

The local vault keeps:

```text
<PERSON_001> → Ahmed
<CNIC_001> → 35202-1234567-1
```

The cloud AI receives the protected version rather than the original sensitive values.

---

## The Major Problem I Discovered

Further research showed that **the general concept is not new**.

There are already:

* Open-source PII detection frameworks
* LLM gateways
* AI security gateways
* Commercial DLP products
* PII redaction systems
* Tokenization systems
* Cloud-AI security products

Therefore, simply building:

```text
PII detection
+
redaction
+
LLM API
```

would not be a sufficiently strong research contribution.

I also do not want to make an unsupported claim that nobody has built such a system before.

---

## Current Research Question

The project therefore remains under a **novelty/technical-gap investigation**.

One possible direction is investigating whether existing privacy/AI gateways have meaningful limitations with:

* Urdu
* Roman Urdu
* Pakistani identifiers such as CNIC
* mixed English/Roman Urdu
* obfuscated sensitive information
* local policy requirements
* reversible privacy-preserving processing

However, this must be **experimentally demonstrated**, not simply claimed.

The key question is:

> **What technically meaningful problem remains unsolved by existing open-source and commercial solutions, and can a student-built system measurably improve it?**

---

## Current Decision

I am **not treating Sovereign Data Gateway as final yet**.

Before committing, I want to perform a hard "kill test":

1. Identify existing products.
2. Identify open-source implementations.
3. Identify relevant academic papers.
4. Determine exactly what existing systems already provide.
5. Find genuine technical limitations.
6. Determine whether those limitations are significant enough for an FYP.
7. Design a measurable contribution.
8. Verify that two BSCS students can implement it.
9. Verify that the contribution can be demonstrated experimentally.
10. Only then finalize the project.

The goal is not to find an idea that merely sounds impressive.

The goal is to find an idea that **survives serious technical scrutiny**.
