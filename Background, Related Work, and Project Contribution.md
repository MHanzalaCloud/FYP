# Background, Related Work, and Project Contribution: Sovereign Data Gateway

## 1. Background
AI chat tools are now used constantly for real, sensitive work. A LayerX study of over 10,000 employees found that **15% regularly paste company data into ChatGPT**, often containing sensitive information. In Pakistan specifically, this risk sits on top of a real regulatory push: Pakistan's *National Data Governance Policy* and *Sovereign Cloud Policy* treat government and certain categories of data as sovereign, and some procurement rules require data, logs, and encryption keys to remain hosted in Pakistan.

In banking specifically, the **State Bank of Pakistan** is finalizing AI-governance guidance for the financial sector, while its own survey found that nearly half of regulated entities already use AI in their operations. Regionally, **Bangladesh Bank** has already formally banned staff from entering confidential banking data into AI tools including ChatGPT, Gemini, Claude, Grok, and DeepSeek. This establishes that the problem this project addresses is live, regional, and present-day, not hypothetical.

---

## 2. Related Work

### 2.1 Academic Research

| Work | What It Does |
| :--- | :--- |
| **Hide and Seek (2023)** | Uses two small local models — one hides private details before sending to the cloud AI, the other restores them in the response. |
| **Casper (2024)** | Replaces personal data with unique placeholders before sending prompts to web-based AI services; reported 98.5% accuracy on personal data across 4,000 synthetic test prompts. |
| **PromptGraph (2026)** | Protects only the specific parts of a prompt that carry privacy risk, and verifies placeholders before restoring them in the response. |

### 2.2 Open-Source Tools

| Tool | What It Does |
| :--- | :--- |
| **Microsoft Presidio** | Detects and anonymizes personal data in text; supports custom recognizers for new data types. |
| **LiteLLM** | An open-source AI gateway that runs Presidio-based masking across calls to providers such as Anthropic, Gemini, and Bedrock. Has reported bugs restoring original values, particularly on streaming responses. |

### 2.3 Cloud-Native Services

| Service | What It Does |
| :--- | :--- |
| **Amazon Bedrock Guardrails** | Detects personal data in prompts and responses and can mask or block it — but processing happens inside AWS itself, meaning the raw sensitive text has already reached the cloud provider before any filtering occurs. |
| **Azure AI Language** | Lists Urdu as a supported language for PII detection, but this is a raw detection API, not a complete policy-enforcing gateway. |

### 2.4 Commercial Products
**Nightfall, Microsoft Purview, Netskope, Zscaler, dope.security, and CrowdStrike Falcon AIDR** all sell AI-data-protection products commercially today, confirming that real, funded enterprise demand exists for this category of tool. 

However, Netskope's own users have publicly reported that its detection *“supports only English language,”* and that non-English identifiers such as names and addresses are *“likely to bypass”* its detection mechanism entirely.

---

## 3. Gap Analysis

| Gap | Confirmed By |
| :--- | :--- |
| **No Urdu or Roman Urdu coverage** in any AI-chat protection product | Netskope's own documented user complaints; no contrary evidence found elsewhere |
| **No Pakistani identifier formats** built in (CNIC, local phone numbers) | Not mentioned in any source reviewed |
| **Bedrock Guardrails filters data only after** it reaches the cloud provider | AWS's own documentation |
| **LiteLLM/Presidio has known restore failures** on streaming responses | User-reported issues found during review |
| **No tool ties AI-data protection** to Pakistan's data-sovereignty policy direction | No source found combining these |
| **No published, measured evaluation** (accuracy, leakage, utility, speed, bypass resistance) in this regional context | No source found |

---

## 4. Our Contribution
* **Language coverage:** Detection extended to English and Roman Urdu, with Pakistani identifier formats (CNIC, local phone numbers) built in — directly addressing the documented language gap above.
* **A policy decision before detection:** A policy layer classifies data (public, internal, personal, critical) and decides what may leave at all, rather than only finding and masking personal data as existing tools do.
* **A vault that never leaves the trusted boundary:** Unlike Bedrock Guardrails, the real values and their identity mapping remain local and are never transmitted to any AI provider.
* **A reliable restore step, explicitly tested against streaming responses:** LiteLLM's documented weak point becomes a measured part of this project's own evaluation rather than an unaddressed limitation.
* **Provider-independent design:** Works as a browser extension or an API proxy across multiple AI providers, rather than being tied to a single cloud vendor's own guardrail product.
* **Grounded and measured, not only claimed:** Tied directly to Pakistan's regulatory direction and evaluated through five defined experiments (detection accuracy, leakage rate, AI utility, latency, and adversarial bypass resistance) — a combination not found elsewhere in the sources reviewed.
