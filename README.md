Revolutionizing AI Training Data Creation through Decentralization

A trustless, transparent, and autonomous data annotation ecosystem that eliminates centralized intermediaries by leveraging Hedera Hashgraph for immutable audit trails, ASI Alliance for intelligent automation, and Lit Protocol for cryptographic payment guarantees.

🎯 The Problem
The $2.7B data annotation industry is controlled by centralized platforms (Scale AI, Amazon MTurk, Labelbox) that:

❌ Extract 30-50% platform fees from every transaction
❌ Own annotator reputations, creating vendor lock-in
❌ Provide zero transparency into data handling or quality control
❌ Delay payments for weeks while holding funds in escrow
❌ Offer no recourse for disputed rejections or unfair reviews

5+ million global annotators lack portable credentials, fair compensation, and transparent processes.

✨ Our Solution
A decentralized protocol (not a platform) where clients, annotators, and AI services interact directly through:

🔗 Smart contracts for trustless escrow and reputation
🤖 Autonomous agents for workflow automation
🔐 Cryptographic guarantees for conditional payments
📊 Immutable audit trails for complete transparency

Key Innovations
FeatureTraditional PlatformsOur PlatformPayment Speed7-30 daysReal-time (8-12 seconds)Platform Fee30-50%~0.01% (blockchain fees only)ReputationPlatform-owned, non-transferableOn-chain, globally portableTransparencyBlack boxEvery event immutably recordedPayment TrustTrust centralized processorCryptographic guarantees (Lit Protocol)Quality ControlManual/opaqueAI-powered + multi-peer consensus

🏗️ Architecture
Three-Layer Technology Stack
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

🔧 Technologies Used
🌐 Hedera Hashgraph (Ledger Layer)
Why Hedera?

⚡ 10,000+ TPS throughput vs 15-30 TPS on Ethereum
💰 $0.0001 per transaction making micropayments viable
⏱️ 3-5 second finality for real-time operations
🛡️ aBFT consensus - mathematically proven security

Implementation:

5 HCS Topics for event-driven architecture:

project.{id}.tasks - Task creation and lifecycle
project.{id}.annotations - Submission events
project.{id}.reviews - Quality control outcomes
project.{id}.screening - Annotator qualifications
project.{id}.payments - Payment execution records


HTS Integration for ASI token micropayments
Solidity Smart Contracts for escrow, reputation, disputes
Mirror Node API for querying historical events

javascript// Example: Publishing annotation submission to HCS
const message = {
  event: "ANNOTATION_SUBMITTED",
  annotator_id: "0x742d35Cc...",
  task_id: "task_123",
  submission_timestamp: 1735257600,
  annotation_hash: "QmT5NvUtoM5nW..."
};

await new TopicMessageSubmitTransaction()
  .setTopicId(topicId)
  .setMessage(JSON.stringify(message))
  .execute(client);

🤖 ASI Alliance (Intelligence Layer)
Fetch.ai uAgents Framework - 5 Autonomous Agents:

Screening Agent (Python + GPT-4)

Generates domain-specific expertise questions
Evaluates annotator qualifications using AI
Publishes scores to HCS for permanent record


Task Manager Agent (TypeScript + Hedera Agent Kit + LangChain)

Natural language project creation
Automatic smart contract deployment
"Create medical imaging project with 1000 tasks" → Instant deployment


Task Assignment Agent (Event-Driven)

Subscribes to HCS task topics
Queries on-chain reputation scores
Assigns to optimal annotators in real-time


Quality Assurance Agent (AI-Powered)

Monitors annotation submissions
Calls SingularityNET models for automated QC
Triggers peer review workflows


Payment Agent (Lit Protocol Integration)

Detects review approvals on HCS
Triggers Lit Actions for conditional payments
Records payment execution back to HCS



SingularityNET AI Marketplace:

Semantic segmentation for bounding box verification
Named Entity Recognition for text consistency
Anomaly detection for quality control
Pre-annotation models (SAM, YOLO, etc.)

python# Example: Screening Agent using GPT-4
@agent.on_event("startup")
async def screen_annotator(ctx: Context, msg: ScreeningRequest):
    questions = await openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{
            "role": "system",
            "content": f"Generate 10 {msg.domain} expertise questions"
        }]
    )
    
    score = await evaluate_responses(msg.answers, questions)
    
    await publish_to_hcs(
        topic=f"project.{msg.project_id}.screening",
        message={"annotator_id": msg.annotator_id, "score": score}
    )

🔐 Lit Protocol (Trustless Execution Layer)
Vincent Payment Delegation System:
The revolutionary payment model that eliminates trust requirements:

Client mints PKP (Programmable Key Pair) - a decentralized wallet
Defines payment rules as Lit Actions (JavaScript conditions)
Delegates to Payment Agent - agent can only trigger, not control funds
Automatic execution when cryptographic conditions are met

Payment Flow:
javascript// Lit Action: Conditional Payment Logic
const paymentRules = async () => {
  // Read Hedera Mirror Node for review status
  const reviewData = await fetch(
    `https://mainnet-public.mirrornode.hedera.com/api/v1/topics/${topicId}/messages`
  );
  
  const latestReview = JSON.parse(reviewData.messages[0].message);
  
  // Check conditions
  if (
    latestReview.status === "APPROVED" &&
    latestReview.annotator_reputation >= 80 &&
    latestReview.quality_score >= 90
  ) {
    // PKP signs Hedera transaction via threshold cryptography
    return await Lit.Actions.signAndCombineEcdsa({
      toSign: {
        to: annotatorAddress,
        amount: taskPayment,
        tokenId: ASI_TOKEN_ID
      },
      publicKey: pkpPublicKey,
      sigName: "payment-sig"
    });
  }
};
Access Control Conditions:

Reputation-gated dataset access
Decrypt IPFS hashes only for qualified annotators
Threshold: reputation_score >= 75

Key Benefits:

✅ Trustless: Client never gives agent direct fund access
✅ Conditional: PKP only signs if logic evaluates true
✅ Decentralized: Threshold cryptography, no single point of failure
✅ Auditable: All executions logged to Hedera HCS


🎨 Features
For Clients

☑️ Natural language project creation
☑️ Smart contract escrow with programmable payment rules
☑️ Real-time project dashboards with on-chain verification
☑️ AI-powered quality control and anomaly detection
☑️ Immutable audit trail for regulatory compliance
☑️ Dataset tokenization as NFTs for ownership/licensing

For Annotators

☑️ Portable, on-chain reputation (verifiable credential)
☑️ Real-time micropayments (8-12 second settlement)
☑️ Professional annotation toolkit (bounding boxes, polygons, segmentation)
☑️ AI-assisted pre-annotation for faster workflows
☑️ Transparent dispute resolution with community arbitration
☑️ Staking mechanism to bootstrap new annotators

For the Ecosystem

☑️ Zero platform fees (only ~$0.0001 blockchain fees)
☑️ Open protocol - anyone can build interfaces or agents
☑️ Self-improving AI feedback loop
☑️ Decentralized governance via ASI token voting


📁 Project Structure
eth-global/
├── frontend/                 # React + TypeScript UI
│   ├── src/
│   │   ├── components/      # Annotation tools, dashboards
│   │   ├── hooks/           # Hedera, Lit Protocol integrations
│   │   ├── services/        # API clients for agents
│   │   └── utils/           # Wallet adapters, IPFS helpers
│   └── package.json
│
├── contracts/               # Solidity Smart Contracts
│   ├── ProjectContract.sol  # Escrow and project management
│   ├── ReputationContract.sol # On-chain reputation scoring
│   ├── DisputeContract.sol  # Decentralized arbitration
│   └── hardhat.config.js    # Hedera deployment config
│
├── agents/                  # Autonomous Agent System
│   ├── screening/           # GPT-4 powered annotator screening
│   ├── task-manager/        # LangChain + Hedera Agent Kit
│   ├── task-assignment/     # Event-driven task distribution
│   ├── quality-assurance/   # SingularityNET integration
│   └── payment/             # Lit Protocol payment triggers
│
├── lit-actions/             # Lit Protocol Conditional Logic
│   ├── payment-rules.js     # PKP payment conditions
│   └── access-control.js    # Reputation-gated decryption
│
├── backend/                 # Off-chain Infrastructure
│   ├── hcs-poller/          # Mirror Node event listener
│   ├── ipfs-service/        # Pinata integration
│   └── api/                 # REST API for frontend
│
└── docs/                    # Documentation
    ├── ARCHITECTURE.md      # Detailed technical design
    ├── API.md               # Agent and contract APIs
    └── DEPLOYMENT.md        # Setup instructions

🚀 Quick Start
Prerequisites
bashNode.js >= 18.x
Python >= 3.10
Hedera Testnet Account (get from portal.hedera.com)
Lit Protocol Cayenne Testnet Access
OpenAI API Key (for screening agent)
1. Clone Repository
bashgit clone https://github.com/007Anmol/eth-global.git
cd eth-global
2. Install Dependencies
bash# Frontend
cd frontend && npm install

# Agents
cd ../agents && pip install -r requirements.txt

# Contracts
cd ../contracts && npm install
3. Configure Environment
bashcp .env.example .env
Edit .env with your credentials:
env# Hedera Configuration
HEDERA_ACCOUNT_ID=0.0.YOUR_ACCOUNT
HEDERA_PRIVATE_KEY=302e020100300506032b657004220420...
HEDERA_NETWORK=testnet

# Lit Protocol
LIT_NETWORK=cayenne
LIT_PKP_PUBLIC_KEY=your_pkp_public_key

# OpenAI (for screening agent)
OPENAI_API_KEY=sk-...

# ASI Token
ASI_TOKEN_ID=0.0.TOKEN_ID

# IPFS/Pinata
PINATA_API_KEY=your_pinata_key
PINATA_SECRET_KEY=your_pinata_secret
4. Deploy Smart Contracts
bashcd contracts
npx hardhat compile
npx hardhat run scripts/deploy.js --network hedera-testnet
Save contract addresses to .env:
envPROJECT_CONTRACT_ADDRESS=0x...
REPUTATION_CONTRACT_ADDRESS=0x...
DISPUTE_CONTRACT_ADDRESS=0x...
5. Start Agents
bashcd agents

# Terminal 1: HCS Event Poller
python hcs-poller/main.py

# Terminal 2: Screening Agent
python screening/agent.py

# Terminal 3: Task Assignment Agent
python task-assignment/agent.py

# Terminal 4: Payment Agent
python payment/agent.py
6. Launch Frontend
bashcd frontend
npm run dev
Access at http://localhost:3000

📊 Demo Workflow
As a Client:

Connect Wallet (HashPack/MetaMask)
Create Project via natural language:

   "Create medical imaging project with 500 X-rays, 
   pay 10 ASI per task, require reputation > 80"

Fund Escrow with ASI tokens
Define Payment Rules in Lit Action editor
Monitor Dashboard with real-time HCS-verified metrics

As an Annotator:

Connect Wallet
Complete AI Screening (GPT-4 generates domain questions)
Browse Available Projects (filtered by reputation requirements)
Annotate Tasks using professional toolkit
Submit Work (published to HCS instantly)
Receive Payment (8-12 seconds after review approval)
Build Reputation (every task adds to on-chain score)

As a Reviewer:

Stake ASI Tokens to access reviewer tasks
Receive Review Assignments from QA Agent
Evaluate Submissions with AI assistance
Submit Review (triggers Lit Protocol payment)
Earn Review Fees automatically


🔬 Technical Deep Dives
HCS Event-Driven Architecture
Traditional Web2 apps use centralized message queues (RabbitMQ, Kafka). We replaced them with Hedera Consensus Service:
Advantages:

✅ Decentralized, globally accessible
✅ Cryptographically ordered and timestamped
✅ Immutable audit trail
✅ Triggers for autonomous agents

Message Flow:
Annotator submits → HCS message published → Mirror Node indexes
→ Agents subscribed to topic detect event → Agent executes logic
→ Agent publishes result to different HCS topic → Cycle continues
Lit Protocol Payment Delegation
Problem: How do you enable automated payments without giving an agent full control of funds?
Solution: Programmable Key Pairs (PKPs) controlled by Lit Actions
Security Model:

PKP private key never exists in full anywhere
Distributed across Lit nodes as threshold shares
Nodes collectively evaluate Lit Action conditions
Only sign transaction if conditions evaluate to true
Uses threshold cryptography (2/3 nodes must agree)

Result: Trustless automation - client defines rules, agents trigger execution, cryptography enforces correctness.
On-Chain Reputation Algorithm
solidityfunction calculateReputation(address annotator) public view returns (uint256) {
    uint256 accuracy = getAccuracyRate(annotator);      // 40% weight
    uint256 taskCount = getTotalTasks(annotator);        // 30% weight  
    uint256 peerReview = getPeerReviewAvg(annotator);    // 20% weight
    uint256 stake = getStakeAmount(annotator);           // 10% weight
    
    return (accuracy * 40) + 
           (min(taskCount, 100) * 30) + 
           (peerReview * 20) + 
           (min(stake, 1000) / 100 * 10);
}
Data Source: HCS messages logged by agents (task completions, reviews, accuracy metrics)
Oracle Pattern: Trusted agent aggregates HCS data, calls updateReputationScore()
Verification: Anyone can independently recalculate by parsing HCS history

🎯 Hackathon Prize Categories
🏆 Hedera Track
Why we should win:

Most comprehensive HCS implementation with 5 production topics
Real-world micropayment system leveraging HTS ($0.0001 fees)
Immutable audit trails demonstrating aBFT security value
Event-driven architecture showcasing Hedera's unique capabilities

🏆 ASI Alliance Track
Why we should win:

Sophisticated multi-agent system (5 specialized uAgents)
SingularityNET marketplace integration for AI-powered QC
Self-improving feedback loop: annotations → train models → better pre-annotation
Embodies ASI vision of decentralized, autonomous AI economy

🏆 Lit Protocol Track
Why we should win:

Most innovative PKP use case: Vincent Payment Delegation
Conditional payments reading blockchain state + executing transactions
Reputation-gated access control for datasets
Demonstrates Lit's full potential beyond basic encryption


📈 Impact & Market Opportunity
Market Size

Current: $2.7B data annotation market (2024)
Projected: $17.2B by 2030 (23.4% CAGR)
Addressable: 5M+ global annotators

Social Impact

✊ Fair compensation: Eliminate 30-50% platform fees
🌍 Global accessibility: Borderless, permissionless access
🎓 Portable credentials: Web3-native professional reputation
⚖️ Due process: Transparent dispute resolution

Technical Innovation

🔗 First production multi-chain agent system (Hedera + Lit)
🤖 AI-orchestrated blockchain workflows
💰 Sub-$0.01 micropayment infrastructure
🛡️ Cryptographically enforced conditional execution
