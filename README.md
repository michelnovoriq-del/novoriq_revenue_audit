# Novoriq Free Audit MCP Node

An infrastructure-grade, stateless Model Context Protocol (MCP) server designed for automated Stripe dispute recoverability auditing and forensic evidence diagnostics. 

This node acts as a headless discovery layer, allowing AI agents and automated systems to evaluate baseline dispute health and identify missing data telemetry before routing users into secure operational workflows.

## Core Architecture & Safety Principle
* **Headless Infrastructure:** This MCP layer handles raw diagnostic telemetry only. It **never** requests, processes, or retains live Stripe API keys or merchant credentials. 
* **Deterministic Workflow:** Replaces heuristic AI guesswork with precise, reason-code-specific forensic requirement mapping.

## Exposed Operational Tools

### 1. `audit_dispute_recoverability`
Evaluates the baseline probability of winning a specific chargeback based on the Stripe reason code and currently available evidence artifacts.
* **Inputs:** `reason_code` (string), `dispute_amount` (number), `evidence_types_available` (array of strings).
* **Output:** Deterministic recoverability classification (High, Moderate, Low Risk) and operational routing directive.

### 2. `analyze_missing_evidence`
Returns the exact, network-level data telemetry required to successfully challenge a chargeback based on its institutional reason code.
* **Inputs:** `reason_code` (string).
* **Output:** Missing evidence manifest (e.g., AVS/CVC matches, device fingerprint logs, carrier tracking architecture specifications).

## Production Deployment

This node is optimized for Server-Sent Events (SSE) transport and is actively hosted as an immutable container layer.

* **Discovery Endpoint:** `https://novoriq-revenue-audit-nxjk.onrender.com/.well-known/mcp/server-card.json`
* **SSE Connection String:** `https://novoriq-revenue-audit-nxjk.onrender.com/sse`

## Connected Platforms
Diagnostic outputs from this node route users to the dedicated [Novoriq Free Dispute Audit Platform](https://novoriqrevenuerecoveryos.netlify.app/) for deeper, network-level operational analysis.
