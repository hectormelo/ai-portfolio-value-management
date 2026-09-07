# Architecture

## Overview

The proof of concept uses a deliberately lightweight local architecture so organizational documents can remain within the local environment.

```mermaid
flowchart TD
    U[User] --> UI[HTML / JavaScript interface]
    UI --> LF[Langflow API]
    LF --> P[Prompt / custom components]
    LF --> C[Benefits catalog]
    LF --> O[Ollama]
    O --> Q[Qwen2.5 local LLM]
    Q --> LF
    LF --> R[Structured or natural-language result]
    R --> UI
    UI --> H[Human validation]
```

## Flow A — Benefit Identification

```mermaid
flowchart LR
    A[PDF contract] --> B[File reader]
    B --> C[LLM: extract deliverables]
    C --> D[Deliverable list]
    E[Benefits catalog] --> F[LLM: map deliverables to benefits]
    D --> F
    F --> G[Structured JSON mapping]
    G --> H[Web UI / optional local file]
```

The output records the project/contract, deliverable, identified benefit, category, associated indicator, rationale, and contribution/confidence level.

## Flow B — Benefit Recommendation

```mermaid
flowchart LR
    A[Project objective + deliverables] --> B[Role-aware prompt]
    C[Benefits catalog] --> B
    B --> D[Local LLM]
    D --> E[Recommendations]
    E --> F[Human review]
```

The user can request a project-level view or a portfolio/PMO view. Recommendations can include clearer objectives, missing benefits, changes to deliverables, and additional deliverables.

## Design choices

### Local model execution

The original PoC uses Ollama and Qwen2.5 locally. This reduces dependence on external model services and supports greater control over document processing. Local execution does **not** remove the need for access controls, auditability, security, and quality assurance.

### Human-in-the-loop

The system does not autonomously approve projects or determine whether benefits will materialize. Its role is to surface relationships and recommendations for expert review.
