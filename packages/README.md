## Package Ecosystem

PowerChain Checkout™ is built as a modular, enterprise-grade platform. Each package has a clearly defined responsibility, enabling developers to build everything from lightweight checkout experiences to large-scale enterprise commerce platforms.

### Core Packages

| Package | Description |
|---------|-------------|
| `@powerchain/checkout` | Core checkout engine for shopping carts, checkout sessions, payment flows, customer journeys and order processing. |
| `@powerchain/ui` | Enterprise React component library with design tokens, themes, accessibility and responsive layouts. |
| `@powerchain/payments` | Payment orchestration, provider integrations, billing, subscriptions, refunds and settlement services. |
| `@powerchain/wallets` | Embedded wallets, Solana wallet adapters, WalletConnect integration, digital identity and multi-asset wallet management. |
| `@powerchain/runtime` | Runtime platform providing configuration, middleware, plugins, caching, feature flags, telemetry and environment management. |
| `@powerchain/plugins` | Plugin framework for extending checkout, payments, UI components, APIs and third-party integrations. |
| `@powerchain/auth` | Enterprise authentication and identity services supporting OAuth 2.1, OpenID Connect (OIDC), JWT, Passkeys and RBAC. |
| `@powerchain/analytics` | Analytics, reporting, customer insights, event tracking and OpenTelemetry integration. |

---

### Commerce & Financial Services

| Package | Description |
|---------|-------------|
| `@powerchain/billing` | Subscription billing, invoicing, recurring payments, taxation and revenue management. |
| `@powerchain/treasury` | Treasury operations, liquidity management, reconciliation, settlement and financial reporting. |
| `@powerchain/marketplace` | Multi-vendor marketplace infrastructure, merchant onboarding, commissions, escrow and product catalogues. |
| `@powerchain/orders` | Order lifecycle management, fulfilment, shipping and order tracking. |
| `@powerchain/customers` | Customer profiles, organisations, accounts, contacts and lifecycle management. |

---

### Digital Assets & Blockchain

| Package | Description |
|---------|-------------|
| `@powerchain/blockchain` | PowerChain Network™ client, transaction lifecycle, accounts and blockchain utilities. |
| `@powerchain/programs` | Smart contract clients, program interfaces and PowerChain Virtual Machine (PVM™) integrations. |
| `@powerchain/tokens` | SPL Tokens, Token-2022, token metadata, tokenisation workflows and digital asset utilities. |
| `@powerchain/assets` | Digital asset management, NFTs, token registries and asset lifecycle services. |
| `@powerchain/rpc` | Enterprise RPC client with batching, retries, failover and load balancing. |
| `@powerchain/helius` | Helius integration for indexing, enhanced RPC services and webhooks. |
| `@powerchain/jupiter` | Jupiter integration for token swaps, liquidity aggregation and routing. |
| `@powerchain/pyth` | Pyth Network integration providing decentralised price feeds and oracle services. |

---

### Artificial Intelligence

| Package | Description |
|---------|-------------|
| `@powerchain/ai` | AI-powered assistants, workflow automation, financial intelligence and recommendations. |
| `@powerchain/copilot` | Enterprise AI Copilot for merchants, operators and developers. |
| `@powerchain/risk` | Fraud detection, compliance, transaction monitoring and risk intelligence. |

---

### Enterprise Platform

| Package | Description |
|---------|-------------|
| `@powerchain/identity` | Identity, organisations, multi-tenancy, permissions and access management. |
| `@powerchain/compliance` | KYC, AML, sanctions screening, audit logging and regulatory compliance. |
| `@powerchain/notifications` | Email, SMS, push notifications, webhooks and event delivery. |
| `@powerchain/integrations` | Enterprise connectors, ERP, CRM, accounting and third-party platform integrations. |

---

### Developer Experience

| Package | Description |
|---------|-------------|
| `@powerchain/sdk` | Unified enterprise SDK combining all PowerChain platform services. |
| `@powerchain/cli` | Command-line tools for project scaffolding, configuration and deployment. |
| `@powerchain/testing` | Testing utilities, mock services, fixtures and integration testing. |
| `@powerchain/codegen` | OpenAPI, GraphQL and TypeScript code generation tools. |
| `@powerchain/devtools` | Runtime diagnostics, debugging utilities and developer tooling. |
| `@powerchain/examples` | Production-ready reference applications, templates and sample integrations. |

---

### Platform Principles

- **Composable Architecture** — Use only the packages your application requires.
- **TypeScript First** — Fully typed APIs with first-class IDE support.
- **Tree-Shakeable** — Optimised ES Modules minimise bundle size.
- **Enterprise Ready** — Built for production with security, observability and scalability.
- **API First** — Consistent REST, GraphQL and SDK interfaces.
- **Cloud Native** — Designed for containers, Kubernetes, serverless and edge deployments.
- **Extensible** — Plugin-based architecture supporting custom integrations and workflows.
- **Semantic Versioning** — Stable public APIs with predictable release management.

> **Enterprise Foundation** — Every package is independently versioned, production-ready and designed to work seamlessly together, enabling developers to build everything from standalone checkout experiences to enterprise-scale commerce, payment and digital asset platforms on the **PowerChain Platform™**.
