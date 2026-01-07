# MLOps, Version Control & DevOps – Production Cheat Sheet

> **Purpose**: A battle-tested cheat sheet for taking ML/AI from notebook to production.
> Covers **MLOps + Version Control + DevOps**, end-to-end.
> Built for **real systems**, not Kaggle demos.
> Strong focus on **reproducibility, security, reliability, and scale**.

---

## 1. Mental Model (Get This Right or Everything Breaks)

MLOps = **Software Engineering + Data Engineering + ML Discipline**.

```text
Code + Data + Model + Config + Infra = System
```

If any one is not versioned, your system is not reproducible.

---

## 2. Why MLOps Exists (Reality Check)

ML fails in production because:

* Data changes
* Models decay
* Pipelines break silently
* Nobody owns retraining

MLOps exists to **control entropy**.

---

## 3. Core Lifecycle (End-to-End)

```text
Data → Training → Validation → Registry → Deployment → Monitoring → Retraining
```

Skipping steps does not make you faster. It makes you fragile.

---

## 4. Version Control Strategy (Non-Negotiable)

### What Must Be Versioned

* Code (Git)
* Configs (YAML)
* Data schemas
* Models
* Prompts (for LLM systems)

### What Must NOT Be Versioned

* Raw secrets
* Credentials
* Large raw datasets

---

## 5. Git Strategy for ML Systems

### Branching (Recommended)

* `main`: production
* `develop`: integration
* `feature/*`: experiments

### Commit Discipline

```text
feat: add demand sensing model
fix: handle missing demand spikes
exp: test new embedding model
```

Messy commits = untraceable experiments.

---

## 6. Experiment Tracking (Critical)

Track:

* Parameters
* Metrics
* Artifacts
* Dataset version

If you cannot reproduce a result, it never existed.

---

## 7. Data Versioning (Most Ignored)

### What to Version

* Dataset snapshots
* Feature definitions
* Training splits

### Approaches

* Hash-based snapshots
* Metadata-based versioning
* Object storage + manifests

Data drift without detection is guaranteed failure.

---

## 8. Feature Stores (When Scale Begins)

Purpose:

* Centralized feature definitions
* Online and offline consistency

Rule:
If features are re-written per model, you are doing it wrong.

---

## 9. Model Training Pipelines

```text
Ingest → Validate → Transform → Train → Evaluate → Package
```

Pipelines must be:

* Deterministic
* Idempotent
* Automated

---

## 10. Model Registry (Source of Truth)

Registry tracks:

* Model version
* Metrics
* Stage (staging, prod)
* Lineage

Never deploy directly from a notebook.

---

## 11. Deployment Patterns

### Batch Inference

* Forecasting
* Scoring

### Online Inference

* APIs
* Low-latency systems

### Streaming Inference

* Events
* Near real-time signals

Choose based on latency, not hype.

---

## 12. CI/CD for ML (DevOps Layer)

### CI

* Linting
* Unit tests
* Data validation

### CD

* Model promotion
* Canary deployment
* Rollbacks

CI/CD without rollback is reckless.

---

## 13. Infrastructure as Code (IaC)

Why:

* Reproducibility
* Auditability
* Security

Infra must be versioned like code.

---

## 14. Monitoring (Where Most Teams Fail)

Monitor:

* Data drift
* Prediction drift
* Performance decay
* Latency
* Cost

Accuracy alone is a lagging indicator.

---

## 15. Retraining Strategies

* Scheduled retraining
* Drift-triggered retraining
* Human-in-the-loop approval

Blind auto-retraining is dangerous.

---

## 16. MLOps for LLMs (LLMOps)

Additional versioning:

* Prompts
* Embeddings
* Vector indexes

LLMs amplify mistakes faster.

---

## 17. Security (OWASP + ISO Aligned)

* Least privilege access
* Signed artifacts
* Secrets via vaults
* Secure model endpoints
* Audit logs

Models can leak data. Treat them as assets.

---

## 18. Cost Management

Track:

* Training cost
* Inference cost
* Storage

Unmonitored ML costs scale exponentially.

---

## 19. Anti-Patterns (Stop These Immediately)

* Notebook-to-prod
* No data versioning
* No rollback plan
* Manual retraining
* One-off pipelines

---

## 20. DevOps vs MLOps (Clear Distinction)

* DevOps: code + infra
* MLOps: data + models + DevOps

MLOps extends DevOps. It does not replace it.

---

## 21. Reference Architecture (Mental Map)

```text
Git → CI → Train → Registry → Deploy → Monitor → Feedback
```

---

## 22. Emergency Checklist

Before any prod deploy:

* Model version tagged
* Dataset identified
* Metrics validated
* Rollback ready
* Monitoring active

---

## 23. Mental Models to Remember

> Reproducibility beats accuracy.
> Drift is inevitable.
> Automation without control is chaos.

---

