# DIKE Protocol — The Multiverse Market

**A Next-Generation Prediction Market with Branching Predictions, AMM Liquidity, and Human-Verified Outcomes**

![DIKE Protocol](https://img.shields.io/badge/Status-Active-brightgreen) ![Solidity](https://img.shields.io/badge/Solidity-0.8+-blue) ![Next.js](https://img.shields.io/badge/Frontend-Next.js-black)

## 🌌 Overview

DIKE Protocol reimagines prediction markets by introducing **prediction trees** and **multiverse branching**. Traditional prediction markets force users to split capital between predictions, limiting upside. DIKE changes that by allowing users to leverage up to 60% of their initial capital to create "child" predictions without needing additional funds—creating a compounding effect where wins branch into further wins, multiplying outcomes far beyond the usual 2x ceiling.

### Key Innovations

- **🌳 Prediction Trees**: Start with one stake, branch into multiple predictions using leverage
- **💰 AMM-Powered Liquidity**: Enter and exit positions at fair, liquid prices without order books
- **✅ Human-Verified Resolution**: Outcomes resolved by KYCed validators verified using Self protocol
- **🔐 Risk-Managed Leverage**: Protocol loans for branching, reclaimed with interest upon resolution
- **📊 Stable Trading Environment**: PyUSD stablecoin base for volatility protection
- **🛡️ Sybil-Resistant Validation**: Decentralized identity verification prevents manipulation

## 🏗️ Project Structure

```
dike-protocol/
├── client/                    # Frontend application (Next.js)
│   ├── app/                   # Next.js app directory
│   │   ├── api/               # API routes (resolution, verification)
│   │   ├── chains/            # Chain-specific pages
│   │   ├── create-predic/     # Prediction creation interface
│   │   ├── dashboard/         # User dashboard
│   │   ├── predictions/       # Predictions listing
│   │   ├── profile/           # User profile
│   │   ├── swap/              # Swap interface
│   │   └── landing/           # Landing page
│   ├── components/            # React components
│   │   ├── ui/                # Reusable UI components (badge, button, card, etc.)
│   │   ├── prediction-details-modal.tsx
│   │   ├── chain-visualization.tsx
│   │   ├── opportunity-card.tsx
│   │   └── ...
│   ├── hooks/                 # Custom React hooks
│   │   ├── createOpportunity.ts
│   │   ├── useInvestInPrediction.ts
│   │   ├── useIPFS.ts
│   │   ├── useReadChains.ts
│   │   └── ...
│   ├── lib/                   # Utility functions
│   │   ├── ipfs.ts
│   │   ├── utils.ts
│   │   └── ...
│   └── package.json           # Frontend dependencies
│
└── dike-contracts/            # Smart contracts (Solidity)
    ├── src/
    │   ├── Dike.sol           # Core protocol contract
    │   ├── FullDike.sol       # Extended protocol features
    │   ├── Swap.sol           # Swap/AMM logic
    │   └── Counter.sol        # Example contract
    ├── test/                  # Test files
    │   ├── Dike.t.sol
    │   ├── Swap.t.sol
    │   └── Counter.t.sol
    ├── script/                # Deployment scripts
    │   ├── DeployDike.s.sol
    │   ├── DeployFullDike.s.sol
    │   └── DeploySwap.s.sol
    ├── lib/                   # Dependencies (Foundry)
    │   ├── forge-std/
    │   ├── openzeppelin-contracts/
    │   ├── pyth-sdk-solidity/
    │   └── openzeppelin-foundry-upgrades/
    ├── foundry.toml           # Foundry configuration
    └── package.json           # Contract dependencies
```

## 🚀 Core Features

### 1. **Prediction Trees & Multiverse Branching**
Users start with an initial stake and can create child predictions using up to 60% leverage without additional capital. This creates a branching structure where:
- Initial prediction resolves → User can branch into new predictions
- Wins compound across branches
- Capital efficiency maximized through protocol-provided loans

### 2. **AMM-Powered Market Making**
- Decentralized liquidity pools replace traditional order books
- Dynamic odds adjustment based on user trades
- Continuous price discovery
- Fair entry and exit prices for all participants
- Liquidity providers earn fees

### 3. **Human-Verified Resolution**
- Price-based predictions: Resolved via **Pyth Network** price feeds (tamper-proof, real-time)
- Event-based predictions: Resolved by **KYCed human validators**
- Validators verified through **Self protocol** QR-based identity verification
- Sybil-attack resistant through decentralized identity validation
- Near real-time sync between off-chain verification and on-chain validator registry

### 4. **Protocol Loans & Risk Management**
- Leverage for branching provided as protocol loans
- Loans reclaimed with interest upon prediction resolution
- Liquidation protection: Positions below loan + interest threshold are liquidated
- Self-sustaining and capital-efficient system

### 5. **Stable Trading with PyUSD**
- **PyUSD** (PayPal's stablecoin) as base currency
- Protects users from protocol token volatility
- Creates more resilient and trustworthy market environment

## 🛠️ Technology Stack

### Smart Contracts
- **Language**: Solidity 0.8+
- **Framework**: Foundry
- **Network**: Sepolia testnet
- **Key Integrations**:
  - **Pyth Network**: Price feeds for deterministic outcome resolution
  - **OpenZeppelin**: Contract standards and upgradeable patterns
  - **PyUSD**: Stablecoin for trading

### Frontend
- **Framework**: Next.js 14+
- **Language**: TypeScript
- **Styling**: CSS (custom) with Tailwind CSS support
- **State Management**: React hooks, wagmi for blockchain interaction
- **UI Components**: Custom component library (Badge, Button, Card, Dropdown, etc.)
- **Key Libraries**:
  - **Wagmi**: Ethereum React hooks
  - **IPFS**: Distributed file storage (useIPFS hook)
  - **Self SDK**: KYC verification integration

### Backend
- **Verification Service**: Self KYC integration
- **API Routes**: Next.js API routes for:
  - `/api/resolution` - Prediction resolution
  - `/api/verify` - User/validator verification
- **Chain Interaction**: Direct smart contract calls for on-chain operations

## 📋 API Endpoints

### Verification API
```
POST /api/verify
```
Handles KYC verification through Self protocol, creates validator registry entries.

### Resolution API
```
POST /api/resolution
```
Triggers prediction resolution with price feeds (Pyth) or human validators.

## 🔄 User Journey

1. **User Registration**: KYC verification through Self
2. **Create Prediction**: Initialize with capital stake
3. **Trade**: Use AMM to adjust positions at fair prices
4. **Branch Predictions**: Leverage up to 60% for child predictions
5. **Resolution**: 
   - Automatic for price-based (Pyth feeds)
   - Human-verified for events (KYCed validators)
6. **Settle**: Claim winnings, protocol reclaims loans + interest

## 📊 Prediction Market Mechanics

### AMM Formula
The protocol uses custom AMM logic for dynamic odds:
- Prices adjust based on liquidity and trade volume
- Fairness ensured through constant product formulas
- No order book dependencies

### Leverage & Branching
```
Max Child Prediction Capital = Initial Stake × 0.60
Number of Branches = No limit (per liquidity)
Compounding Effect = Child Wins → More Capital for Grandchildren
```

### Liquidation Threshold
```
If Position Value < (Loan Amount + Interest):
  → Position Liquidated
  → Collateral Returned (after loan repayment)
```

## 🔐 Security & Validation

### Sybil Resistance
- All validators KYCed through Self protocol
- QR-code based verification flow
- Each person = one validator identity
- Off-chain verification synced on-chain in near real-time

### Outcome Verification
| Prediction Type | Resolution Method | Security |
|---|---|---|
| Price Predictions | Pyth Network feeds | Cryptographic proof, tamper-proof |
| Event Predictions | Human validators | KYC-verified, Sybil-resistant |

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- Git
- Foundry (for smart contracts)
- Wallet with Sepolia testnet funds

### Installation

#### Frontend Setup
```bash
cd client
npm install
npm run dev
```

#### Smart Contracts Setup
```bash
cd dike-contracts
forge install
forge test
forge script script/DeployDike.s.sol --rpc-url sepolia
```

## 📝 Smart Contracts

### Core Contracts

#### `Dike.sol`
Main protocol contract handling:
- Prediction creation and management
- Branching logic and capital allocation
- Loan accounting and interest calculation
- Integration with Pyth price feeds

#### `FullDike.sol`
Extended features including:
- Advanced branching scenarios
- Enhanced liquidity management
- Multi-stage predictions

#### `Swap.sol`
AMM swap and liquidity pool logic:
- Dynamic fee calculation
- Liquidity provider management
- Order execution and price discovery

## 🧪 Testing

### Run Contract Tests
```bash
cd dike-contracts
forge test
```

### Run Frontend Tests
```bash
cd client
npm run test
```

## 📱 Frontend Pages

- **Landing** (`/landing`): Project introduction
- **Dashboard** (`/dashboard`): User overview and portfolio
- **Create Prediction** (`/create-predic`): Prediction initialization
- **Predictions** (`/predictions`): Browse all active predictions
- **Chains** (`/chains/[id]`): Chain-specific market data
- **Swap** (`/swap`): Direct token swapping
- **Profile** (`/profile`): User account settings
- **KYC Test** (`/kyc-test`): Verification workflow testing

## 🎯 How It's Made

1. **Smart Contracts**: Solidity contracts deployed on Sepolia handle prediction trees, branching logic, loan accounting, and AMM mechanics
2. **Price Feeds**: Integrated Pyth Network for tamper-proof, real-time price data
3. **Human Validation**: Self KYC SDK provides decentralized identity verification with QR-code authentication
4. **Stable Base**: PyUSD stablecoin ensures market stability
5. **Frontend**: Next.js application with wagmi for seamless blockchain interaction
6. **Backend Bridge**: API routes connect off-chain verification with on-chain contracts

### Technical Highlights
- QR-based KYC approval flow synced with contract validator registry
- Custom AMM engine for dynamic odds without order books
- Protocol-managed loans for leverage without external capital
- Sybil-resistant validator selection through decentralized identity

## 🌐 Deployment

Contracts deployed on **Sepolia testnet**. Deployment scripts in `dike-contracts/script/`.

### Broadcast Records
Deployment history tracked in `dike-contracts/broadcast/`

## 📚 Documentation

- **DEPLOYMENT.md**: Detailed deployment instructions
- **SELF_VERIFICATION_README.md**: Self KYC integration guide
- **Smart Contract ABIs**: Available in `client/app/abi.ts`

## 🤝 Contributing

Contributions welcome! Please ensure:
- All tests pass
- Code follows Solidity and TypeScript conventions
- New features include tests
- README updated for significant changes

## 📄 License

[Add appropriate license]

## 🙋 Support

For questions or issues:
- Review documentation in contract README files
- Check API endpoint specifications
- Test on Sepolia testnet first

---

**DIKE Protocol**: Transforming prediction markets into living multiverse strategies where capital compounds, liquidity flows freely, and outcomes are verified by trusted, decentralized validators.