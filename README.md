# AgentFacts Universal Metadata Schema Specification v1.0

**Official Standard by Jared James Grogan**  
**© 2022-2025 Jared James Grogan. All rights reserved.**  
**Apache 2.0 Licensed Implementation**

## Overview

AgentFacts is the universal "Know Your Agent" (KYA) metadata standard for verified AI agent capabilities and deployment, inspired by the success of Nutrition Facts labeling in establishing consumer trust through standardized transparency.

### Original Vision (2022)
Just as Nutrition Facts transformed food safety by providing standardized ingredient and nutritional information, AgentFacts transforms AI agent procurement by providing standardized capability and trust metadata.

## Schema Files & Usage

### 1. Minimal Categories (`agentfacts-categories-minimal-v1.json`)
**Use Case**: Rapid prototyping, documentation, examples
- Ultra-lightweight structure showing 10 core sections
- Perfect for understanding AgentFacts architecture
- Copy-paste foundation for implementations

### 2. Categories with Descriptions (`agentfacts-categories-v1.json`) 
**Use Case**: Schema validation, developer guidance, API contracts
- JSON Schema with validation rules
- Comprehensive section descriptions
- Ideal for tooling and IDE support

### 3. Complete Implementation (`agentfacts-v1.json`)
**Use Case**: Production deployments
- Full field definitions and validation
- Enterprise-grade feature coverage
- Complete extensibility framework

### 4. Foundation Schema (`/foundation/agentfacts-v1-foundation.json`)
**Use Case**: Reference implementation - IMMUTABLE
- Original authoritative version
- Legal and IP reference
- Historical preservation

## Core Architecture

### 10 Universal Sections
1. **core_identity** (Required) - Agent identification and lifecycle
2. **baseline_model** (Required) - Foundation AI model transparency  
3. **classification** - Universal categorization system
4. **capabilities** - Extensible skill declarations
5. **authentication_permissions** - Enterprise security and dynamic permissions
6. **compliance_regulatory** - Multi-jurisdictional regulatory alignment
7. **performance_reputation** - Measurable quality metrics
8. **supply_chain** - SBOM integration and transparency
9. **verification** - Cryptographic trust and multi-authority validation
10. **extensibility** - Future-proofing mechanisms

### Extensibility Framework
- `additionalProperties: true` on all objects
- `patternProperties: {"^x-": {...}}` for custom extensions
- Domain-specific metadata via `extensibility.custom_facts`
- Unlimited expansion without breaking compatibility

## Governance & Authority

**Official Specification**: https://agentfacts.org  
**Standard Owner**: Jared James Grogan  
**Academic Foundation**: "AgentFacts: Universal KYA Standard for Verified AI Agent Metadata & Deployment" (May 12, 2025)

### Licensing
- **Standard Specification**: © Jared James Grogan. All rights reserved.
- **Schema Implementation**: Apache 2.0 licensed for universal adoption
- **Original Concept**: © 2022 Jared James Grogan (prior art established)

### Contributions
All contributions must maintain compatibility with this official specification. Extensions should use the `x-` prefix pattern to avoid conflicts with future standard evolution.

### Validation Requirements
1. **Required Sections**: `core_identity` and `baseline_model` must be present
2. **JSON Schema Validation**: All schemas include comprehensive validation rules
3. **TTL Compliance**: Metadata must respect time-to-live expiration
4. **Extension Compatibility**: Custom extensions must use `x-` prefix pattern

---

*AgentFacts: Making AI agent capabilities as transparent and trustworthy as nutrition labels.*
