# AgentFacts Field Definitions Reference v1.0

**Official Standard by Jared James Grogan**  
**© 2022-2025 Jared James Grogan. All rights reserved.**  
**Apache 2.0 Licensed Implementation**

**Comprehensive field-by-field specification for AgentFacts Universal Metadata Standard**

## Section 1: core_identity (REQUIRED)

### agent_id (string, required)
- **Purpose**: Unique identifier for the agent across all systems
- **Format**: DID, UUID, URI, or custom identifier scheme
- **Examples**: `"did:agent:example:hr-assistant-v1"`, `"uuid:550e8400-e29b-41d4-a716-446655440000"`
- **Validation**: Must be unique within deployment scope

### name (string, required)  
- **Purpose**: Human-readable agent identifier
- **Format**: UTF-8 string, internationalization supported
- **Examples**: `"Legal Research Assistant"`, `"客服助手"`, `"Assistant Juridique"`

### version (string, required)
- **Purpose**: AgentFacts schema version being used
- **Format**: Semantic versioning recommended
- **Examples**: `"1.0"`, `"1.2.1"`, `"2.0.0-beta"`

### created (string, date-time, required)
- **Purpose**: ISO timestamp of initial agent registration
- **Format**: ISO 8601 date-time
- **Example**: `"2025-06-12T14:30:00Z"`
- **Immutable**: Should never change after initial creation

### last_updated (string, date-time, required)
- **Purpose**: ISO timestamp of most recent metadata update
- **Format**: ISO 8601 date-time  
- **Example**: `"2025-06-12T16:45:23Z"`
- **Automation**: Should update automatically on any metadata change

### ttl (integer, required)
- **Purpose**: Global time-to-live in seconds for metadata freshness
- **Format**: Positive integer
- **Examples**: `86400` (24 hours), `3600` (1 hour), `604800` (1 week)
- **Behavior**: After TTL expires, metadata should be refreshed

## Section 2: baseline_model (REQUIRED)

### foundation_model (string)
- **Purpose**: Base AI model identifier
- **Examples**: `"gpt-4"`, `"claude-3-sonnet"`, `"llama-2-70b"`, `"custom-enterprise-model"`
- **Transparency**: Critical for trust and capability assessment

### model_version (string)
- **Purpose**: Specific version/revision of the foundation model
- **Examples**: `"gpt-4-0613"`, `"claude-3-sonnet-20240229"`, `"v2.1.0"`
- **Precision**: Should be as specific as possible for reproducibility

### model_provider (string)
- **Purpose**: Organization that provides/hosts the foundation model
- **Examples**: `"OpenAI"`, `"Anthropic"`, `"Meta"`, `"Enterprise AI Division"`

### training_data_sources (array[string])
- **Purpose**: Data sources used for fine-tuning (not base model training)
- **Examples**: `["internal-docs", "industry-standards", "public-apis"]`
- **Privacy**: Should not expose sensitive data details

### training_cutoff_date (string, date-time)
- **Purpose**: Knowledge cutoff timestamp for the model
- **Format**: ISO 8601 date-time
- **Example**: `"2024-01-15T00:00:00Z"`

### fine_tuning (object)
- **Purpose**: Custom training specifications and metadata
- **Structure**: Fully extensible object
- **Examples**: `{"method": "supervised", "dataset_size": 10000, "training_duration_hours": 48}`

### model_capabilities (array[string])
- **Purpose**: List of model capabilities
- **Examples**: `["text-generation", "code-analysis", "multimodal", "function-calling"]`

### known_limitations (array[string])
- **Purpose**: Documented capability boundaries and restrictions
- **Examples**: `["no-real-time-data", "english-only", "no-image-generation"]`

### bias_assessments (object)
- **Purpose**: Fairness and bias evaluation results
- **Structure**: Extensible for any bias testing framework
- **Examples**: `{"gender_bias_score": 0.12, "assessment_framework": "Fairness Indicators v2.1"}`

### safety_evaluations (object)
- **Purpose**: Risk and safety testing outcomes
- **Structure**: Extensible for evolving safety standards
- **Examples**: `{"harmful_content_filter": "enabled", "red_team_score": 8.5}`

## Section 3: classification

### agent_type (string, enum)
- **Values**: `["assistant", "autonomous", "tool", "workflow"]`
- **Purpose**: Primary functional classification
- **Extensibility**: Additional types can be added via extensions

### operational_level (string, enum)  
- **Values**: `["ambient", "supervised", "autonomous"]`
- **Purpose**: Level of autonomy and human oversight required

### stakeholder_context (string, enum)
- **Values**: `["enterprise", "consumer", "government"]` 
- **Purpose**: Target deployment environment

### deployment_scope (string, enum)
- **Values**: `["internal", "external", "hybrid"]`
- **Purpose**: Operational boundary classification

### interaction_mode (string, enum)
- **Values**: `["synchronous", "asynchronous", "batch"]`
- **Purpose**: Primary interaction pattern

## Section 4: capabilities

### external_apis (array[string])
- **Purpose**: List of supported external API specifications
- **Examples**: `["REST", "GraphQL", "gRPC", "Slack API v2", "Salesforce API"]`

### tool_calling (array[string])
- **Purpose**: Tool calling protocols and standards supported
- **Examples**: `["MCP", "OpenAI-function-calls", "custom-tool-protocol"]`

### programming_languages (array[string])
- **Purpose**: Programming languages the agent can work with
- **Examples**: `["python", "javascript", "sql", "bash", "typescript"]`

### data_formats (array[string])
- **Purpose**: Data formats the agent can process
- **Examples**: `["json", "csv", "pdf", "docx", "image/png", "audio/wav"]`

### interface_types (array[string])
- **Purpose**: Supported interaction interfaces
- **Examples**: `["text", "voice", "gui", "api", "webhook"]`

### domain_expertise (array[string])
- **Purpose**: Specialized knowledge domains
- **Examples**: `["healthcare", "finance", "legal", "hr", "marketing"]`

### language_support (array[string])
- **Purpose**: Natural languages supported
- **Examples**: `["en", "es", "fr", "de", "zh-CN", "ja"]`
- **Format**: ISO 639-1 language codes recommended

## Section 5: authentication_permissions

### supported_methods (array[string])
- **Purpose**: Authentication methods supported by the agent
- **Examples**: `["oauth2", "api_key", "mtls", "jwt", "saml"]`

### primary_scheme (string)
- **Purpose**: Recommended primary authentication method
- **Examples**: `"oauth2"`, `"api_key"`, `"mtls"`

### oauth_endpoints (object)
- **Purpose**: OAuth configuration endpoints
- **Structure**: `{"authorization_url": "...", "token_url": "...", "scopes": [...]}`

### auth_security_level (string, enum)
- **Values**: `["basic", "standard", "high", "critical"]`
- **Purpose**: Security classification for authentication requirements

### current_permissions (array[string])
- **Purpose**: Currently granted access permissions
- **Examples**: `["read", "write", "execute", "admin"]`

### permission_scope (array[string])
- **Purpose**: Resource access patterns and boundaries
- **Examples**: `["/api/v1/documents/*", "/api/v1/users/read"]`

### permission_ttl (string, date-time)
- **Purpose**: Permission expiration timestamp
- **Format**: ISO 8601 date-time
- **Example**: `"2025-06-15T00:00:00Z"`

### permission_authority (string)
- **Purpose**: Organization granting permissions
- **Examples**: `"ACME_Corp_IAM"`, `"enterprise.com"`

## Section 6: compliance_regulatory

### eu_ai_act (object)
- **Purpose**: EU AI Act compliance metadata
- **Structure**: `{"risk_level": "limited", "transparency_obligations": true}`

### nist_ai_rmf (object)
- **Purpose**: NIST AI Risk Management Framework alignment
- **Structure**: `{"framework_version": "1.0", "governance_alignment": "full"}`

### gdpr_compliance (object)
- **Purpose**: GDPR data protection compliance status
- **Structure**: `{"data_protection_status": "compliant", "privacy_controls": "implemented"}`

### safety_classification (string, enum)
- **Values**: `["low", "medium", "high", "critical"]`
- **Purpose**: Overall safety risk classification

## Section 7: performance_reputation

### response_time_p50 (number)
- **Purpose**: Median response latency in milliseconds
- **Unit**: Milliseconds
- **Example**: `150.5`

### response_time_p95 (number)
- **Purpose**: 95th percentile response latency
- **Unit**: Milliseconds  
- **Example**: `500.0`

### availability_sla (number)
- **Purpose**: Uptime percentage commitment
- **Format**: Percentage (0-100)
- **Example**: `99.9`

### throughput_limit (number)
- **Purpose**: Maximum requests per minute capacity
- **Unit**: Requests per minute
- **Example**: `1000`

### reputation_score (number)
- **Purpose**: Aggregate quality rating from users
- **Scale**: 0.0 to 5.0 (or custom scale)
- **Example**: `4.7`

### user_satisfaction (number)
- **Purpose**: Average user satisfaction rating
- **Scale**: 0.0 to 5.0
- **Example**: `4.5`

### task_success_rate (number)
- **Purpose**: Percentage of successfully completed tasks
- **Format**: Percentage (0-100)
- **Example**: `94.5`

## Section 8: supply_chain

### component_dependencies (array[objects])
- **Purpose**: External service and component dependencies
- **Structure**: `[{"name": "...", "version": "...", "provider": "...", "criticality": "..."}]`

### software_libraries (array[objects])
- **Purpose**: Code libraries and dependencies
- **Structure**: `[{"name": "...", "version": "...", "license": "...", "vulnerability_status": "..."}]`

### data_dependencies (array[objects])
- **Purpose**: External data sources and feeds
- **Structure**: `[{"source": "...", "provider": "...", "update_frequency": "...", "reliability_sla": ...}]`

## Section 9: verification

### signatures (array[objects])
- **Purpose**: Multi-authority cryptographic signatures
- **Structure**: `[{"authority": "...", "signature": "...", "verified_sections": [...], "timestamp": "..."}]`

### verification_authorities (array[objects])
- **Purpose**: Trusted verification entities
- **Structure**: `[{"name": "...", "public_key": "...", "contact": "...", "specialization": [...]}]`

### verification_ttl (object)
- **Purpose**: Per-section verification expiration
- **Structure**: `{"performance_reputation": "2025-06-15T00:00:00Z", "authentication_permissions": "..."}`

### confidence_scores (object)
- **Purpose**: Trust levels for different verification authorities
- **Structure**: `{"NIST": 0.95, "Anthropic": 0.98, "Enterprise_Security": 0.85}`

## Section 10: extensibility

### custom_facts (object)
- **Purpose**: Domain-specific metadata extensions
- **Structure**: Fully extensible nested objects
- **Examples**: `{"healthcare_compliance": {"hipaa_certified": true}, "financial_compliance": {"pci_dss_level": 1}}`

### schema_extensions (array[strings])
- **Purpose**: References to additional schema specifications
- **Format**: URLs to external schema documents
- **Examples**: `["https://company.com/schemas/custom-agent-v1.json"]`

### extension_version (string)
- **Purpose**: Version tracking for extensions
- **Format**: Semantic versioning
- **Examples**: `"1.0"`, `"2.1.0"`

## Extensibility Patterns

### Custom Extensions (x- prefix)
All sections support custom extensions using the `x-` prefix pattern:
```json
{
  "capabilities": {
    "programming_languages": ["python", "javascript"],
    "x-enterprise-certifications": ["ISO-27001", "SOC-2"]
  }
}
```

Pattern Properties
All objects support additionalProperties: true for maximum flexibility.
Validation Rules

Required Fields: core_identity and baseline_model sections must be present
Data Types: All fields must match specified types (string, integer, array, object)
Format Validation: Date-time fields must be valid ISO 8601
Enum Validation: Enumerated fields must use specified values
TTL Logic: TTL must be positive integer
Extension Compatibility: Custom extensions must not conflict with standard fields


Complete field reference for AgentFacts v1.0 - enabling transparent, trustworthy AI agent coordination.
