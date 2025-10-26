# 🚀 Decentralized Data Annotation Platform

![Banner](https://github.com/user-attachments/assets/50adb70a-2c77-4bd1-9a81-f8f7dc5f1cce)

**Revolutionizing AI Training Data Creation through Decentralization**

A trustless, transparent, and autonomous data annotation ecosystem that eliminates centralized intermediaries by leveraging Hedera Hashgraph for immutable audit trails, ASI Alliance for intelligent automation, and Lit Protocol for cryptographic payment guarantees.

---

## 🎯 The Problem

The $2.7B data annotation industry is controlled by centralized platforms (Scale AI, Amazon MTurk, Labelbox) that:

- ❌ Extract 30-50% platform fees from every transaction
- ❌ Own annotator reputations, creating vendor lock-in
- ❌ Provide zero transparency into data handling or quality control
- ❌ Delay payments for weeks while holding funds in escrow
- ❌ Offer no recourse for disputed rejections or unfair reviews

**5+ million global annotators** lack portable credentials, fair compensation, and transparent processes.

---

## ✨ Our Solution

A **decentralized protocol** (not a platform) where clients, annotators, and AI services interact directly through:

- 🔗 **Smart contracts** for trustless escrow and reputation
- 🤖 **Autonomous agents** for workflow automation
- 🔐 **Cryptographic guarantees** for conditional payments
- 📊 **Immutable audit trails** for complete transparency

### Key Innovations

| Feature | Traditional Platforms | Our Platform |
|---------|----------------------|--------------|
| **Payment Speed** | 7-30 days | Real-time (8-12 seconds) |
| **Platform Fee** | 30-50% | ~0.01% (blockchain fees only) |
| **Reputation** | Platform-owned, non-transferable | On-chain, globally portable |
| **Transparency** | Black box | Every event immutably recorded |
| **Payment Trust** | Trust centralized processor | Cryptographic guarantees (Lit Protocol) |
| **Quality Control** | Manual/opaque | AI-powered + multi-peer consensus |

---

## 🏗️ Architecture

### Three-Layer Technology Stack

```
┌─────────────────────────────────────────────────────────────┐
│                     USER INTERFACE LAYER                     │
│  React + TypeScript + Canvas API + WalletConnect            │
└─────────────────────────────────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                   INTELLIGENCE LAYER                         │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │ Fetch.ai     │  │ SingularityNET│  │  LangChain   │      │
│  │ uAgents      │  │ AI Marketplace│  │  NLP Engine  │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
│                                                               │
│  Screening • Task Assignment • QA • Payment • Marketplace    │
└─────────────────────────────────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────┐
│              TRUSTLESS EXECUTION LAYER                       │
│  ┌──────────────────────────────────────────────────────┐  │
│  │           Lit Protocol (PKPs + Lit Actions)          │  │
│  │  • Conditional Payments  • Access Control            │  │
│  │  • Threshold Cryptography • Decentralized Signing    │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                              ▼
┌─────────────────────────────────────────────────────────────┐
│                    LEDGER LAYER                              │
│  ┌─────────────┐  ┌─────────────┐  ┌──────────────┐        │
│  │ Hedera HCS  │  │ Hedera HTS  │  │  Smart       │        │
│  │ (Events)    │  │ (Payments)  │  │  Contracts   │        │
│  └─────────────┘  └─────────────┘  └──────────────┘        │
│                                                               │
│  10,000 TPS • $0.0001/tx • 3-5s finality • aBFT security    │
└─────────────────────────────────────────────────────────────┘
```

---

## 🔧 Technologies Used

### 🌐 Hedera Hashgraph (Ledger Layer)

**Why Hedera?**
- ⚡ **10,000+ TPS** throughput vs 15-30 TPS on Ethereum
- 💰 **$0.0001 per transaction** making micropayments viable
- ⏱️ **3-5 second finality** for real-time operations
- 🛡️ **aBFT consensus** - mathematically proven security

**Implementation:**
- **5 HCS Topics** for event-driven architecture:
  - `project.{id}.tasks` - Task creation and lifecycle
  - `project.{id}.annotations` - Submission events
  - `project.{id}.reviews` - Quality control outcomes
  - `project.{id}.screening` - Annotator qualifications
  - `project.{id}.payments` - Payment execution records

- **HTS Integration** for ASI token micropayments
- **Mirror Node API** for querying historical events

---

### 🤖 ASI Alliance (Intelligence Layer)

**Fetch.ai uAgents Framework** - 5 Autonomous Agents:

1. **Screening Agent** (Python + GPT-4)
   - Generates domain-specific expertise questions
   - Evaluates annotator qualifications using AI
   - Publishes scores to HCS for permanent record

2. **Task Manager Agent** (TypeScript + Hedera Agent Kit + LangChain)
   - Natural language project creation
   - Automatic smart contract deployment
   - "Create medical imaging project with 1000 tasks" → Instant deployment

3. **Task Assignment Agent** (Event-Driven)
   - Subscribes to HCS task topics
   - Queries on-chain reputation scores
   - Assigns to optimal annotators in real-time

4. **Quality Assurance Agent** (AI-Powered)
   - Monitors annotation submissions
   - Calls SingularityNET models for automated QC
   - Triggers peer review workflows

5. **Payment Agent** (Lit Protocol Integration)
   - Detects review approvals on HCS
   - Triggers Lit Actions for conditional payments
   - Records payment execution back to HCS

---

### 🔐 Lit Protocol (Trustless Execution Layer)

**Vincent Payment Delegation System:**

The revolutionary payment model that eliminates trust requirements:

1. **Client mints PKP** (Programmable Key Pair) - a decentralized wallet
2. **Defines payment rules** as Lit Actions (JavaScript conditions)
3. **Delegates to Payment Agent** - agent can only trigger, not control funds
4. **Automatic execution** when cryptographic conditions are met

**Access Control Conditions:**
- Reputation-gated dataset access
- Decrypt IPFS hashes only for qualified annotators
- Threshold: `reputation_score >= 75`

**Key Benefits:**
- ✅ **Trustless**: Client never gives agent direct fund access
- ✅ **Conditional**: PKP only signs if logic evaluates true
- ✅ **Decentralized**: Threshold cryptography, no single point of failure
- ✅ **Auditable**: All executions logged to Hedera HCS

---

## 🎨 Features

### For Clients
- ☑️ Natural language project creation
- ☑️ Smart contract escrow with programmable payment rules
- ☑️ Real-time project dashboards with on-chain verification
- ☑️ AI-powered quality control and anomaly detection
- ☑️ Immutable audit trail for regulatory compliance
- ☑️ Dataset tokenization as NFTs for ownership/licensing

### For Annotators
- ☑️ Portable, on-chain reputation (verifiable credential)
- ☑️ Real-time micropayments (8-12 second settlement)
- ☑️ Professional annotation toolkit (bounding boxes, polygons, segmentation)
- ☑️ AI-assisted pre-annotation for faster workflows
- ☑️ Transparent dispute resolution with community arbitration
- ☑️ Staking mechanism to bootstrap new annotators

### For the Ecosystem
- ☑️ Zero platform fees (only ~$0.0001 blockchain fees)
- ☑️ Open protocol - anyone can build interfaces or agents
- ☑️ Self-improving AI feedback loop
- ☑️ Decentralized governance via ASI token voting

---



## 🚀 Quick Start
---

HCS Topics can be verified on hashscan.io

PROJECT_TOPICS_ID=0.0.7121902
SCREENING_TOPICS_ID=0.0.7121903
COMPLETION_TOPICS_ID=0.0.7121905

---

ASI agent: @ai-screening-agent
Address: agent1qw4q278rq5zgyvjz8snrvm03dvvpaw546v8lwa499md2336elksjc9l7tyz
Link: https://agentverse.ai/agents/details/agent1qw4q278rq5zgyvjz8snrvm03dvvpaw546v8lwa499md2336elksjc9l7tyz/profile 

---

env template
PINATA_JWT= 
NEXT_PUBLIC_GATEWAY_URL=
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=

# Hedera Testnet Credentials
HEDERA_TESTNET_ACCOUNT_ID=
HEDERA_TESTNET_PRIVATE_KEY=
HEDERA_TESTNET_OPERATOR_KEY=


# Mirror Node URL
MIRROR_NODE_URL=h
REPUTATION_CONTRACT_ADDRESS=

PROJECT_TOPICS_ID=
SCREENING_TOPICS_ID=
ASSIGNMENT_TOPICS_ID=
COMPLETION_TOPICS_ID=
PAYMENT_TOPICS_ID=

ASI_API_KEY=

LIT_NETWORK=
LIT_PRIVATE_KEY=

JWT_SECRET=

---


## 📊 Demo Workflow

### As a Client:

1. **Connect Wallet** (HashPack/MetaMask)
2. **Create Project** via natural language:
   ```
   "Create medical imaging project with 500 X-rays, 
   pay 10 ASI per task, require reputation > 80"
   ```
3. **Fund Escrow** with ASI tokens
4. **Define Payment Rules** in Lit Action editor
5. **Monitor Dashboard** with real-time HCS-verified metrics

### As an Annotator:

1. **Connect Wallet**
2. **Complete AI Screening** (GPT-4 generates domain questions)
3. **Browse Available Projects** (filtered by reputation requirements)
4. **Annotate Tasks** using professional toolkit
5. **Submit Work** (published to HCS instantly)
6. **Receive Payment** (8-12 seconds after review approval)
7. **Build Reputation** (every task adds to on-chain score)

---


## 🎯 Hackathon Prize Categories

### 🏆 Hedera Track
**Why we should win:**
- Most comprehensive HCS implementation with 5 production topics
- Real-world micropayment system leveraging HTS ($0.0001 fees)
- Immutable audit trails demonstrating aBFT security value
- Event-driven architecture showcasing Hedera's unique capabilities

### 🏆 ASI Alliance Track  
**Why we should win:**
- Sophisticated multi-agent system (5 specialized uAgents)
- SingularityNET marketplace integration for AI-powered QC
- Self-improving feedback loop: annotations → train models → better pre-annotation
- Embodies ASI vision of decentralized, autonomous AI economy

### 🏆 Lit Protocol Track
**Why we should win:**
- Most innovative PKP use case: Vincent Payment Delegation
- Conditional payments reading blockchain state + executing transactions
- Reputation-gated access control for datasets
- Demonstrates Lit's full potential beyond basic encryption

---

## 📈 Impact & Market Opportunity

### Market Size
- **Current:** $2.7B data annotation market (2024)
- **Projected:** $17.2B by 2030 (23.4% CAGR)
- **Addressable:** 5M+ global annotators

### Social Impact
- ✊ **Fair compensation:** Eliminate 30-50% platform fees
- 🌍 **Global accessibility:** Borderless, permissionless access
- 🎓 **Portable credentials:** Web3-native professional reputation
- ⚖️ **Due process:** Transparent dispute resolution

### Technical Innovation
- 🔗 First production multi-chain agent system (Hedera + Lit)
- 🤖 AI-orchestrated blockchain workflows
- 💰 Sub-$0.01 micropayment infrastructure
- 🛡️ Cryptographically enforced conditional execution

## 🔗 Links

- **GitHub:** [github.com/007Anmol/eth-global](https://github.com/007Anmol/eth-global)
- **Live Demo:** Coming Soon

---



</div>
