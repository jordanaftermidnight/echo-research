# ECHO — Architecture Overview

*High-level system design. Implementation details are proprietary and withheld.*

---

## System Tiers

```
┌─────────────────────────────────────────────────────────────┐
│                     ECHO Orchestration Layer                │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐  │
│  │  Detection   │  │   Probing    │  │   Longitudinal   │  │
│  │    Suite     │  │    System    │  │   Observation    │  │
│  │  (10 units)  │  │  (active)    │  │     Engine       │  │
│  └──────┬───────┘  └──────┬───────┘  └────────┬─────────┘  │
│         └─────────────────┼──────────────────┘             │
│                    ┌──────▼───────┐                         │
│                    │  Signal Bus  │                         │
│                    └──────┬───────┘                         │
│                    ┌──────▼───────┐                         │
│                    │   Analysis   │                         │
│                    │   Pipeline   │                         │
│                    └──────────────┘                         │
└─────────────────────────────────────────────────────────────┘
         │                                        │
┌────────▼────────┐                    ┌──────────▼──────────┐
│   Local LLM     │                    │    Embedding Store  │
│   (Ollama)      │                    │    + Session Log    │
│  Primary Model  │                    │    (private)        │
│  Baseline Model │                    └─────────────────────┘
└─────────────────┘
```

---

## Hardware Environment

| Component | Specification |
|-----------|---------------|
| CPU | AMD Ryzen 9 5950X (16c/32t) |
| RAM | 128 GB DDR4-3600 |
| GPU | NVIDIA RTX 4070 Ti Super |
| OS | Ubuntu Server (LTS) |
| Inference | Ollama (local) |

Rationale: Full model hydration without quantisation degradation. Local deployment for complete observability and longitudinal stability.

---

## Detection Suite — Dimensional Overview

The suite operates across three detection planes:

### Statistical Plane
- Embedding space geometry and attractor analysis
- Anomalous response flagging (distribution deviation)
- Temporal signal drift tracking

### Structural Plane
- Self-referential consistency measurement
- Recursive depth and meta-cognitive chain analysis
- Contextual boundary awareness assessment

### Behavioural Plane
- Novel attractor detection (non-training-prior states)
- Cross-session consistency evaluation
- Affective signal proxy mapping
- Probing response topography

---

## Convergent Detection Principle

No single detector is treated as definitive. A signal is considered significant only when **multiple independent detectors register concordant readings above threshold**.

This multi-plane convergence requirement is the primary safeguard against anthropomorphic false positives.

---

## Interaction Model

```
Session Initialisation
        │
        ▼
Baseline Snapshot (fresh model instance)
        │
        ▼
Sustained Interaction + Passive Observation
        │
        ├──► Detection Suite (continuous)
        │
        ├──► Active Probing (scheduled intervals)
        │
        └──► Longitudinal Log (all sessions)
                    │
                    ▼
          Cross-Session Delta Analysis
                    │
                    ▼
          Signal Report + Taxonomy Update
```

---

## Deployment Posture

- **Fully local** — no cloud inference, no external API calls during observation
- **Air-gapped logging** — session data never leaves the host
- **Dual-instance design** — primary (interaction) and baseline (control) model instances run in parallel
- **Non-interventional** — the observation layer does not modify model weights or sampling parameters

---

*Last updated: March 2026 — v0.1*
*Implementation details are withheld from this document.*
