# 🏗 Technical Design Document: Sahaya AI  
**Subtitle:** Architecture for a Resilient, Multilingual Digital Public Infrastructure.

---

## 1. Architectural Philosophy

Sahaya AI is built on a **Hybrid Edge-Cloud Architecture**. This design balances high-reasoning capabilities (Cloud) with mission-critical reliability in rural connectivity "dead zones" (Edge).

### Key Design Pillars:

- **Sovereign Integration:** Native support for Bhashini (Language) and ONDC (Commerce).
- **Grounding & Accuracy:** RAG-based inference to eliminate LLM hallucinations in policy guidance.
- **Offline Resilience:** On-device SLMs for zero-bandwidth environments.

---

## 2. Technology Stack

| Component | Technology | Role |
|------------|------------|------|
| **Cloud Intelligence** | Amazon Bedrock (Claude 3.5 Sonnet) | Core reasoning and complex RAG |
| **Language Layer** | Bhashini (ASR, NMT, TTS) | Real-time dialect translation & synthesis |
| **Serverless Logic** | AWS Lambda & API Gateway | Request orchestration and protocol routing |
| **Vector Storage** | Amazon OpenSearch Serverless | Semantic indexing of government gazettes |
| **Edge Engine** | Gemma 3 (4-bit Quantized) | On-device inference for offline mode |
| **Primary Database** | Amazon DynamoDB | Scalable user state and preference storage |
| **Asset Storage** | Amazon S3 | Storage for policy PDFs and Knowledge Base |

---

## 3. System Architecture Diagram

The following diagram illustrates the request lifecycle from a rural user to the AWS cloud and ONDC network.

```mermaid
graph TD
User((Rural User)) -->|Voice in Dialect| MobileApp[Mobile App: React Native]

subgraph Edge_Layer
MobileApp -->|Offline Fallback| Gemma[Gemma 3 SLM]
Gemma -->|Local RAG| SQLite[(Local Vector Store)]
end

MobileApp -->|Online Mode| APIGateway[AWS API Gateway]

subgraph AWS_Cloud
APIGateway --> Lambda[AWS Lambda Orchestrator]
Lambda --> Bhashini[Bhashini API: Dialect -> English]
Bhashini --> Bedrock[Amazon Bedrock: RAG Engine]
Bedrock --> KnowledgeBase[(S3 + OpenSearch)]
Lambda --> ONDC[Beckn/ONDC Gateway]
end

Lambda -->|Response| Bhashini
Bhashini -->|Audio Synthesis| MobileApp
MobileApp -->|Voice Response| User
