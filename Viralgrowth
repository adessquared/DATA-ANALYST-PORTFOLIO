### Policy‑Driven Task Distribution for Promotions (Laravel 11)

- Repo: [ViralGrowth Live — Promotion Task Platform]
- Stack: Laravel 11 (PHP 8.2), Sanctum, Vite + Tailwind + Alpine, Redis (Predis)
- Role: Data Analyst & self‑taught engineer — designed fairness policies, implemented assignment algorithms, and instrumented observability.

**Problem**
- Inconsistent distribution across users and duplicate promotions reduced task quality and throughput. Owners could distribute while carrying backlogs, and recipients with poor completion rates consumed capacity.

**Intervention**
- 6‑hour window model (00:00/06:00/12:00/18:00) with policy‑driven gates and preferences:
  - Owner gating: exclude promotions from owners carrying current‑window pending assignments
  - Recipient preference: prioritize users with zero current‑window pending; among equals, higher monthly completion rates
  - URL normalization: canonicalize cross‑platform links to block duplicates
  - Compliance‑aware approvals: expiry for unsubmitted assignments, auto‑approval threshold for high performers
  - Transparent UI: “Active (Queued)” for promoters; “Queued: owner has pending” in admin lists

**Impact (sample metrics placeholders)**
- +X% assignments completed per window after preference ordering
- −Y% duplicate submissions detected via normalized URLs
- −Z% support tickets after introducing queued status messaging
- +W% auto‑approved submissions among compliant users

**Data Signals**
- Current‑window pending = count(status=assigned, assigned_window_start=windowEdge)
- Monthly completion rate = (completed / assigned) * 100 per user
- Normalized target URL = canonicalized identity for cross‑platform duplicates

**Algorithm Summary**
- Selection excludes: historical tasks (completed/expired/rejected), self‑owned, normalized duplicates
- Apply caps: per‑task daily_limit split by 6‑hour windows
- Owner gating → recipient preference ordering → assign until caps or per‑user quotas met

**Financials & Integrations**
- Earnings credited on approvals; monthly payouts to wallets
- Payment integrations with Binance Pay & NOWPayments; webhook‑driven ledger entries
- Genealogy matrix (nested‑set) for deep‑level distributions with spillover rules

**Observability**
- Structured logs for owner‑gating and normalized exclusions
- UI chips for Active/Inactive/Queued to align expectations and reduce ambiguity

**What I Contributed**
- Designed fairness policy and preference ordering criteria grounded in operational signals
- Implemented gating and ordering behind config flags for safe rollout
- Added normalized URL duplicate checks and compliance‑aware approvals
- Instrumented logs and status messaging for explainability

**Future Work**
- Experiment with gating thresholds (e.g., allow distribution when pending ≤ 1)
- Dashboard KPIs: queue rate, completion latency, duplicate rate, approval latency
- Aggregated precomputations to further reduce query costs in large cohorts
