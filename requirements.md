# 📋 Project Requirements: Sahaya AI  
**Sub-title:** Empowering Bharat through Sovereign, Multimodal Digital Public Infrastructure.

---

## 1. Executive Summary

Sahaya AI is a voice-first assistant designed to provide marginalized and low-literacy communities in rural India with direct access to government welfare (G2C) and digital marketplaces (ONDC). By combining AWS Cloud Intelligence with Bhashini's linguistic layer, Sahaya AI eliminates the barriers of language, literacy, and limited internet connectivity.

---

## 2. Target Audience & User Personas

| Persona        | Characteristics | Pain Point | Sahaya AI Solution |
|---------------|----------------|------------|---------------------|
| **Rural Farmer** | Low literacy, Kannada dialect speaker | Cannot navigate text-heavy government portals | Voice-guided scheme discovery in native dialect |
| **Local Artisan** | Limited digital exposure, tribal community | No access to urban markets or fair pricing | Voice-activated ONDC listing and sales |
| **PwD Citizen** | Vision-impaired, elderly | Physical and digital navigation barriers | 100% hands-free, audio-only interaction model |

---

## 3. Functional Requirements (FR)

### 🔊 3.1 Multilingual Conversational Layer

- **FR-101:** Support for real-time ASR (Speech-to-Text) and TTS (Text-to-Speech) in 22 scheduled Indian languages.
- **FR-102:** Understanding of regional dialects and non-standard accents via Bhashini’s localized fine-tuning.
- **FR-103:** Natural language intent classification to differentiate between informational (Schemes) and transactional (ONDC) queries.

---

### 🗂 3.2 Information & Welfare Access

- **FR-201:** Semantic search across 500+ Central and State welfare policies using AWS Bedrock RAG.
- **FR-202:** Interactive eligibility assessment through voice-based question-and-answer prompts.
- **FR-203:** Integration with DigiLocker via India Stack for automated document verification.

---

### 🛒 3.3 Economic & Market Integration

- **FR-301:** Voice-based discovery of local providers on the ONDC Network.
- **FR-302:** End-to-end checkout flow using voice-verified UPI payments.

---

### 📡 3.4 Offline & Low-Bandwidth Resilience

- **FR-401:** Local execution of high-priority FAQ responses using an on-device Gemma 3 (Quantized) model.
- **FR-402:** Data-efficient text fallback mode for users on 2G/EDGE networks.

---

## 4. Non-Functional Requirements (NFR)

### ⚡ 4.1 Performance & Scalability

- **Latency:** End-to-end voice turnaround time (Speech-to-Speech) must be < 2.5 seconds on 4G networks.
- **Scalability:** Backend must handle 100,000+ concurrent requests using AWS Lambda and Auto-scaling groups.

---

### 🔒 4.2 Security & Compliance

- **Data Residency:** 100% of data processing and storage must remain within the AWS Mumbai (ap-south-1) region.
- **Privacy:** Mandatory compliance with the Digital Personal Data Protection (DPDP) Act 2023.
- **Encryption:** AES-256 encryption for data at rest and TLS 1.3 for data in transit.

---

### ♿ 4.3 Accessibility

- **Interface:** Adherence to WCAG 2.1 Level AA standards.
- **Interaction:** Support for haptic feedback for non-visual cues during voice processing.

---

## 5. Technical Constraints & Stack

- **LLM Engine:** AWS Bedrock (Claude 3.5 Sonnet) for high-reasoning tasks.
- **Language Layer:** Bhashini ULCA APIs for ASR/TTS/NMT.
- **Edge Engine:** Google Gemma 3 (Quantized to 4-bit) for Android-native inference.
- **Compute:** AWS Lambda (Serverless) for cost-efficiency.
- **Database:** Amazon DynamoDB for user state and Amazon S3 for Knowledge Base storage.

---

## 6. Success Metrics (KPIs)

- **Accessibility Index:** 50% increase in scheme application rates among targeted rural clusters.
- **Accuracy:** >90% factual accuracy in RAG-based scheme retrieval (hallucination control).
- **Cost Efficiency:** Maintain infrastructure cost of <$0.05 per active user session at scale.

---
