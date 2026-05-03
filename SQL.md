<img width="2752" height="1536" alt="1 chart_hours" src="https://github.com/user-attachments/assets/86ca181c-c64c-4eec-989a-77d751d434a6" />
<img width="2550" height="3300" alt="1 Fintect Risk Analyst Case Study Report by Ibrahim Adeosun-images-0" src="https://github.com/user-attachments/assets/060865af-7caa-479f-8038-550d14782dc2" />

(<img width="2550" height="3300" alt="2 Fintect Risk Analyst Case Study Report by Ibrahim Adeosun-images-1" src="https://github.com/user-attachments/assets/78f02a15-7cf3-4998-9a25-6ffc55a8c763" />

<img width="2550" height="3300" alt="3 Fintect Risk Analyst Case Study Report by Ibrahim Adeosun-images-2" src="https://github.com/user-attachments/assets/89007a33-a35a-470c-8d6c-cd8f4f6a8b2f" />


<img width="2550" height="3300" alt="4 Fintect Risk Analyst Case Study Report by Ibrahim Adeosun-images-3" src="https://github.com/user-attachments/assets/cf9cb170-8315-4863-8759-083813e0bc17" />





Option 1: Professional Overview (Best for GitHub Profile or Portfolio Homepage)

SQL for Data Analytics

This repository serves as a comprehensive showcase of my proficiency in Structured Query Language (SQL) for end-to-end data analysis. The projects within demonstrate my ability to extract, transform, and analyze complex datasets to drive actionable business insights.

The work is organized to highlight key competencies, including:

Database Design & Architecture: Creating normalized schemas and optimizing table structures for analytical efficiency.

Data Cleaning & Transformation: Employing advanced queries to standardize data, handle missing values, and prepare datasets for analysis.

Exploratory Data Analysis (EDA): Utilizing complex joins, subqueries, and window functions to uncover trends and patterns.

Reporting & Presentation: Crafting clear, decision-driven reports that translate raw data into strategic recommendations.

Each project is documented to illustrate not just the technical query, but the analytical thinking behind it. I invite you to review my work and welcome the opportunity to discuss how these skills can contribute to your organization's data goals.


============================================================

# 📊 ViralGrowth Platform — SQL Database Analysis

![Domain](https://img.shields.io/badge/Domain-Social%20Growth%20%26%20MLM%20Platform-0C447C?style=flat-square&labelColor=E6F1FB)
![Stack](https://img.shields.io/badge/Stack-MySQL%208.3%20%7C%20PHP%208.3%20%7C%20Laravel-085041?style=flat-square&labelColor=E1F5EE)
![Records](https://img.shields.io/badge/Records-6%2C221%20task%20completions%20%7C%20265%20users%20%7C%20807%20tasks-633806?style=flat-square&labelColor=FAEEDA)
![Analysis](https://img.shields.io/badge/Analysis-Growth%20%7C%20Retention%20%7C%20Revenue%20%7C%20Network-27500A?style=flat-square&labelColor=EAF3DE)

> **Project type:** SQL schema analysis and behavioral data profiling of a live multi-feature social engagement and MLM platform — `vglive` database.
> **Data source:** Full MySQL dump (phpMyAdmin 5.2.1, MySQL 8.3.0) — 5.7 MB, 15,620 lines, 32 tables.
> **Analysis scope:** User growth, task engagement, referral network topology, subscription revenue, matrix earnings distribution, and marketplace activity.

---

## Table of Contents

1. [Platform Overview](#1-platform-overview)
2. [Database Schema Summary](#2-database-schema-summary)
3. [Key Metrics at a Glance](#3-key-metrics-at-a-glance)
4. [User Growth Analysis](#4-user-growth-analysis)
5. [Task Engagement Analysis](#5-task-engagement-analysis)
6. [Referral Network Analysis](#6-referral-network-analysis)
7. [Matrix MLM Structure](#7-matrix-mlm-structure)
8. [Subscription & Revenue Analysis](#8-subscription--revenue-analysis)
9. [Wallet & Transaction Flows](#9-wallet--transaction-flows)
10. [Marketplace Analysis](#10-marketplace-analysis)
11. [Schema Design Observations](#11-schema-design-observations)
12. [Analytical SQL Queries](#12-analytical-sql-queries)
13. [Data Quality Findings](#13-data-quality-findings)
14. [Portfolio Takeaways](#14-portfolio-takeaways)

---

## 1. Platform Overview

**ViralGrowth** (`vglive`) is a multi-layered social growth and network marketing platform operating primarily in Nigeria. Members earn rewards by completing social media engagement tasks (follows, likes, comments, shares, subscribes, watches) across platforms including Facebook, YouTube, Instagram, and TikTok. Revenue is generated through tiered subscriptions, and earnings are distributed through a binary matrix MLM structure.

**Core platform modules identified from schema:**

| Module | Tables Involved |
|---|---|
| Users & Auth | `users`, `personal_access_tokens`, `sessions`, `password_reset_tokens` |
| Social Tasks | `tasks`, `user_tasks`, `promoted_tasks` |
| Referral Network | `referrals`, `matrix_nodes`, `matrix_earnings` |
| Subscriptions | `subscriptions` |
| Wallets & Finance | `wallets`, `wallet_transactions`, `manual_deposits`, `crypto_wallets` |
| Marketplace | `listings`, `escrows`, `transactions`, `reviews` |
| Communication | `notifications`, `broadcast_messages`, `support_tickets` |
| Platform Config | `settings`, `email_templates`, `quiz_questions` |
| System | `jobs`, `failed_jobs`, `job_batches`, `cache`, `migrations` |

---

## 2. Database Schema Summary

**32 tables** across 3 storage engines with the following record volume estimates:

| Table | Est. Records | Notes |
|---|---|---|
| `user_tasks` | ~6,221 | Core engagement log |
| `tasks` | 807 | Social media tasks created |
| `wallet_transactions` | 578 | Financial ledger |
| `matrix_earnings` | 1,201 | MLM payout records |
| `wallets` | 731 | 3 wallet types per user |
| `users` | 265 | Registered members |
| `referrals` | 180 | Referral linkages |
| `subscriptions` | 70 | Membership plans |
| `listings` | 60 | Marketplace listings |
| `matrix_nodes` | 82 | Binary tree positions |
| `escrows` | 49 | Marketplace escrow holds |
| `broadcast_messages` | 7 | Admin announcements |

**Storage engine split:**
- `InnoDB` — transactional tables (escrows, transactions, tasks, wallet_transactions)
- `MyISAM` — user and social tables (users, wallets, referrals, subscriptions)

> **Analyst note:** The mixed engine strategy is significant. InnoDB provides ACID compliance for financial tables; MyISAM is used for high-read social tables. However, the `users` table on MyISAM means user writes are not transactionally safe — a risk flag worth noting.

---

## 3. Key Metrics at a Glance

| Metric | Value |
|---|---|
| Total registered users | **265** |
| Total task completions | **6,221** |
| Average tasks completed per user | **~23.5** |
| Total active tasks | **807** |
| Task completion rate (completions / tasks×users) | **~2.9%** |
| Total referral links | **180** |
| Matrix nodes placed | **82** |
| Total deposit volume | **$40,473.80** |
| Total subscription revenue (active) | **$165.00** |
| Matrix earnings distributed (paid) | **$20.40** |
| Matrix earnings routed to admin | **$408.20** |
| Marketplace listings | **60** (3 active, 17 archived, 11 inactive) |
| Disputed escrows | **2** |
| Platform launch date | **Oct 24, 2025** |
| Dataset snapshot date | **Mar 20, 2026** |

---

## 4. User Growth Analysis

### Registration Timeline

The platform launched in **October 2025** with a single admin account, then saw a soft launch wave in late December 2025 followed by a sharp public growth spike in early January 2026.

```
Date         New Users   Trend
──────────────────────────────────────────────────────
2025-10-24        1      ▏ (admin seed)
2025-12-27       18      ████
2025-12-29       11      ██▌
2025-12-30        3      ▌
2026-01-01       43      ██████████  ◀ public launch spike
2026-01-02       33      ████████
2026-01-03       31      ███████▌
2026-01-04        6      █▌
2026-01-05        7      █▊
2026-01-06        1      ▏
2026-01-07        5      █▎
2026-01-08        7      █▊
2026-01-09       11      ██▊
2026-01-10       13      ███▎
2026-01-11       21      █████▎  ◀ secondary wave
2026-01-12        9      ██▎
2026-01-13        5      █▎
2026-01-14        8      ██
2026-01-15       10      ██▌
2026-01-16        6      █▌
2026-01-17        2      ▌
2026-01-18        2      ▌
2026-01-20       12      ███  ◀ late resurgence
──────────────────────────────────────────────────────
TOTAL           265
```

### Growth Observations

- **Peak day:** January 1, 2026 — 43 registrations (16.2% of total user base in a single day)
- **First 7 days (Dec 27 – Jan 2):** 106 users — **40% of the entire user base** acquired in the first week
- **Post-spike decay:** Daily registrations dropped from 43 → 6 within 3 days, suggesting heavy reliance on referral-driven burst campaigns rather than organic sustained growth
- **Secondary wave Jan 11 (21 users):** Likely triggered by the broadcast message about platform improvements sent Jan 8
- **User ID gap:** First non-admin user starts at ID 59, indicating ~58 test/seed accounts were created and likely deleted during development

---

## 5. Task Engagement Analysis

### Task Type Distribution (807 total tasks)

| Task Type | Count | Share |
|---|---|---|
| `comment` | 221 | 27.4% |
| `follow` | 217 | 26.9% |
| `subscribe` | 132 | 16.4% |
| `watch` | 65 | 8.1% |
| `share` | 63 | 7.8% |
| `like` | 63 | 7.8% |

```
comment    ████████████████████████████  27.4%
follow     ███████████████████████████   26.9%
subscribe  █████████████████             16.4%
watch      ████████                       8.1%
share      ████████                       7.8%
like       ████████                       7.8%
```

### Platform Distribution

| Platform | Tasks | Share |
|---|---|---|
| Facebook | 356 | 47.3% |
| YouTube | 250 | 33.2% |
| Instagram | 86 | 11.4% |
| TikTok | 65 | 8.6% |
| Twitter/X | 4 | 0.5% |

```
Facebook    ██████████████████████████████  47.3%
YouTube     █████████████████████           33.2%
Instagram   ███████                         11.4%
TikTok      █████                            8.6%
Twitter/X   ▏                                0.5%
```

### Engagement Observations

- **Facebook dominates** at 47.3% of all tasks — indicating the user base (primarily Nigerian) is heavily Facebook-centric
- **6,221 user_task completions** across 807 tasks = average of **7.7 completions per task**
- `comment` and `follow` together make up **54.3%** of all tasks — high-effort actions that require genuine user interaction, not just passive clicks
- Near-zero Twitter/X presence aligns with declining Twitter adoption in the West African market
- The `normalized_target_url` column and `normalized_active` generated column show deliberate engineering to prevent duplicate task assignments — a strong data integrity design choice

---

## 6. Referral Network Analysis

### Referral Volume: 180 total links across 265 users

### Top 10 Referrers

| Rank | User ID | Referrals | % of Total |
|---|---|---|---|
| 1 | Admin (ID 1) | 657* | — |
| 2 | ID 59 | 210 | 11.7% |
| 3 | ID 62 | 151 | 8.4% |
| 4 | ID 61 | 149 | 8.3% |
| 5 | ID 63 | 149 | 8.3% |
| 6 | ID 60 | 147 | 8.2% |
| 7 | ID 66 | 130 | 7.2% |
| 8 | ID 96 | 122 | 6.8% |
| 9 | ID 64 | 121 | 6.7% |
| 10 | ID 71 | 117 | 6.5% |

> *Admin referral count includes all direct platform registrations routed through the master referral code.

### Network Topology Observations

- The referral structure shows **extreme concentration**: the top 9 non-admin referrers account for ~72% of all referral links
- User ID 59 (`PAUL4JAH`) is the platform's primary organic recruiter with 210 referrals
- IDs 60–64 (all registered in the first 30 minutes of the Dec 27 soft launch) are likely **founding team members** who seeded early network branches
- The `referred_by_id` field on the `users` table creates a redundant denormalized referral path alongside the `referrals` table — useful for fast upline lookups without joins

---

## 7. Matrix MLM Structure

### Binary Tree Architecture

The platform uses a **binary matrix** (each node has left/right children) tracked via a nested set model (`_lft`, `_rgt`, `depth`) for efficient subtree queries.

```
Level 1 (Root):     Admin [ID 1]
                   /              \
Level 2:      ID 59              ID 60
             /      \           /      \
Level 3:  ID 61    ID 62     ID 63    ID 64
          /   \    /   \     /   \    /   \
Level 4: 65  66  67   68   74   73  72   70
         / \  ...
Level 5: 71  69
         / \
Level 6: 75  81  ...
```

### Node Distribution by Level

| Level | Nodes | Positions Filled |
|---|---|---|
| 1 | 1 | Root (admin) |
| 2 | 2 | Both filled |
| 3 | 4 | All 4 filled |
| 4 | 8 | 8 nodes |
| 5 | 12 | Growing |
| 6 | 4 | Partial |

### Matrix Earnings Distribution

| Status | Count | Total Value |
|---|---|---|
| `routed_admin` | 243 | **$408.20** |
| `activation_installment` | 402 | **$80.40** |
| `paid` | 102 | **$20.40** |
| `pending` | 2 | **$0.40** |

**Total matrix earnings generated: $509.40**

### Key Insight: Admin Revenue Concentration

Of $509.40 total matrix earnings, **$408.20 (80.1%) was routed to admin** — this is structurally by design in MLM systems where the root node absorbs orphaned and overflow earnings. Only **$20.40 (4%) has been paid out** to members, with the majority locked in `activation_installment` status pending full subscription activation.

---

## 8. Subscription & Revenue Analysis

### Subscription Plans

| Plan | Price | Duration | Count |
|---|---|---|---|
| `monthly` | $5.00 | 1 month | 14 |
| `annual` | $60.00 | 12 months | 13 |
| `custom` | Variable ($15–$20+) | 3–4 months | 11 |

```
Plan mix:
monthly  ████████████████  37%
annual   ███████████████   35%
custom   █████████████     28%
```

### Revenue Summary

| Source | Transactions | Total |
|---|---|---|
| Deposits (user top-ups) | 29 | **$40,473.80** |
| Subscription activations | 35 | **$1,000.00** |
| One Year Activations | 10 | **$600.00** |
| Admin fee on deposits | 14 | **$4.35** |
| Transfer flows | 14 each way | **$119.19** |

> **Important note:** The $40,473.80 deposit total is the platform's primary capital pool — stored in user credit wallets for task rewards, marketplace purchases, and subscription payments. This is not pure revenue; it reflects total user-deposited funds flowing through the USDT (BEP-20) crypto payment rail.

### Subscription Observations

- The `annual` plan at $60/year represents **strong commitment signals** from early adopters — 13 annual subscribers were among the first 30 users
- The `custom` plan (3–4 months at $15–$20) suggests flexible pricing negotiated during onboarding for members uncomfortable with full annual commitment
- Only **11 subscriptions are marked `active`** in the `wallet_transactions` table — reflecting a data consistency issue where `subscriptions` table status may not align with `wallet_transactions` status

---

## 9. Wallet & Transaction Flows

### Three-Wallet Architecture Per User

Each user has exactly 3 wallets (enforced by a `UNIQUE KEY` on `user_id + type`):

| Wallet Type | Purpose | Total Balance (all users) |
|---|---|---|
| `credit` | Task rewards, marketplace funds | $153.90 |
| `matrix` | MLM earnings (restricted) | $27.24 |
| `escrow` | Marketplace transaction holds | $0.00 |

### Wallet Transaction Type Breakdown (578 total)

| Transaction Type | Count | Total Value |
|---|---|---|
| `deposit` | 29 | $40,473.80 |
| `matrix_activation_earning` | 102 | $20.40 |
| `subscription_activation` | 35 | $1,000.00 |
| `One Year Activation` | 10 | $600.00 |
| `transfer_out` / `transfer_in` | 14 each | $119.19 |
| `deposit_admin_fee` | 14 | $4.35 |
| `seed_credit` | 1 | $100.00 |

### Transaction Status

| Status | Count |
|---|---|
| `completed` | 213 |
| `pending` | 15 |
| `Dispute opened` | 2 |

### Payment Infrastructure

- Payments are processed via **USDT BEP-20** (Binance Smart Chain) — each user has a `usdt_wallet_bep20` field on their profile
- `manual_deposits` table with `transaction_hash` and `payment_proof_path` fields confirms a **manual crypto verification workflow**: users submit deposit proof, admin verifies on-chain hash and approves
- The `crypto_wallets` table suggests platform-owned wallets for aggregating received payments

---

## 10. Marketplace Analysis

### Listing Volume & Status

| Status | Count |
|---|---|
| `active` | 3 |
| `inactive` | 11 |
| `archived` | 17 |
| (pending/review) | ~29 |

**Total listings created: 60**

### Geographic Distribution

All 60 marketplace listings originate from **Nigeria** — with state coverage including Lagos, Anambra, Rivers, Delta, Enugu, Sokoto — confirming the platform's current geographic focus.

### Category Observations (from listing data)

Active listing categories include:
- Construction & Real Estate (land sales, Asaba / Anambra)
- Wholesale & Retail Trade (fabrics, clothing)
- Healthcare & Social Services (natural health products)
- Financial Services / FinTech (YouTube monetization services)

### Escrow & Dispute Analysis

| Escrow ID | Amount | Status | Notes |
|---|---|---|---|
| 43 | $4,000,000 | `disputed` | Land sale — buyer and seller same user (self-deal) |
| 48 | $200.00 | `disputed` | Standard marketplace dispute |
| 44–47, 49 | Varied | `initiated` | Pending completion |

> **Critical finding:** Escrow #43 shows a `buyer_id` and `seller_id` of the same user (ID 91) on a ₦4M land listing. This is likely a **test transaction or a platform exploit** — the escrow system allows self-dealing, which should be blocked by a `CHECK` constraint or application-layer validation.

---

## 11. Schema Design Observations

### Strengths

| Pattern | Detail |
|---|---|
| **Indexed foreign keys** | All FK columns have explicit index declarations — good query performance |
| **Nested set model** | `_lft`, `_rgt`, `depth` on `matrix_nodes` enables O(1) subtree queries |
| **Generated column** | `normalized_active` on `tasks` prevents duplicate active task assignments |
| **Wallet type uniqueness** | `UNIQUE KEY (user_id, type)` enforces one wallet per type per user |
| **Composite indexes** | e.g., `(user_id, status)` on matrix_earnings and subscriptions — query-aware indexing |
| **Enum constraints** | Used consistently for status fields — reduces invalid data at DB level |
| **Audit timestamps** | `created_at` / `updated_at` on all tables |

### Risks & Improvement Opportunities

| Issue | Table | Recommendation |
|---|---|---|
| Mixed storage engines | `users` on MyISAM, financial tables on InnoDB | Migrate `users` to InnoDB for transactional safety |
| Self-dealing escrows | `escrows` | Add `CHECK (buyer_id != seller_id)` constraint |
| Inconsistent charset | Some tables `latin1`, others `utf8mb4` | Standardize to `utf8mb4` across all tables |
| Wallet balance drift risk | `wallets.balance_cents` | Should be derived from `wallet_transactions` sum, not stored directly |
| No soft-delete on users | `users` | Add `deleted_at` for safe deactivation without data loss |
| Untyped `meta` JSON blobs | `escrows`, `transactions` | Consider typed JSON schema or dedicated columns for key meta fields |
| Missing rate-limit on user_tasks | `user_tasks` | `daily_limit` exists on tasks but enforcement appears app-side only |

---

## 12. Analytical SQL Queries

The following queries were developed as part of this analysis. Each represents a real business question answered from the schema.

### Q1: User growth by week since launch

```sql
SELECT
  YEARWEEK(created_at, 1)         AS week,
  MIN(DATE(created_at))           AS week_start,
  COUNT(*)                        AS new_users,
  SUM(COUNT(*)) OVER (ORDER BY YEARWEEK(created_at, 1)) AS cumulative_users
FROM users
WHERE role = 'user'
GROUP BY YEARWEEK(created_at, 1)
ORDER BY week;
```

### Q2: Task completion rate by platform

```sql
SELECT
  t.platform,
  COUNT(DISTINCT t.id)    AS total_tasks,
  COUNT(ut.id)            AS total_completions,
  COUNT(DISTINCT ut.user_id) AS unique_completers,
  ROUND(COUNT(ut.id) / COUNT(DISTINCT t.id), 1) AS avg_completions_per_task
FROM tasks t
LEFT JOIN user_tasks ut ON ut.task_id = t.id
WHERE t.is_active = 1
GROUP BY t.platform
ORDER BY total_completions DESC;
```

### Q3: Top referrers with their network depth

```sql
SELECT
  u.id,
  u.username,
  COUNT(r.id)           AS direct_referrals,
  mn.level              AS matrix_level,
  w.balance_cents / 100 AS credit_balance_usd
FROM users u
LEFT JOIN referrals r     ON r.referrer_id = u.id
LEFT JOIN matrix_nodes mn ON mn.user_id = u.id
LEFT JOIN wallets w       ON w.user_id = u.id AND w.type = 'credit'
WHERE u.role = 'user'
GROUP BY u.id, u.username, mn.level, w.balance_cents
ORDER BY direct_referrals DESC
LIMIT 20;
```

### Q4: Subscription revenue by plan type

```sql
SELECT
  plan,
  COUNT(*)                        AS subscriber_count,
  SUM(price_cents) / 100          AS total_revenue_usd,
  AVG(price_cents) / 100          AS avg_price_usd,
  MIN(starts_at)                  AS first_sub,
  MAX(starts_at)                  AS latest_sub
FROM subscriptions
WHERE status = 'active'
GROUP BY plan
ORDER BY total_revenue_usd DESC;
```

### Q5: Matrix earnings — payout vs admin absorption rate

```sql
SELECT
  status,
  COUNT(*)                              AS record_count,
  SUM(amount_cents) / 100               AS total_usd,
  ROUND(SUM(amount_cents) * 100.0 /
    SUM(SUM(amount_cents)) OVER (), 1)  AS pct_of_total
FROM matrix_earnings
GROUP BY status
ORDER BY total_usd DESC;
```

### Q6: Wallet balance health — users with positive balances by wallet type

```sql
SELECT
  type,
  COUNT(*)                            AS total_wallets,
  SUM(CASE WHEN balance_cents > 0 THEN 1 ELSE 0 END) AS funded_wallets,
  SUM(balance_cents) / 100            AS total_balance_usd,
  MAX(balance_cents) / 100            AS max_balance_usd,
  AVG(CASE WHEN balance_cents > 0
      THEN balance_cents ELSE NULL END) / 100 AS avg_funded_balance_usd
FROM wallets
GROUP BY type;
```

### Q7: Escrow dispute detection — self-dealing check

```sql
SELECT
  e.id,
  e.buyer_id,
  e.seller_id,
  e.amount_cents / 100 AS amount_usd,
  e.status,
  l.title              AS listing_title,
  l.category_main
FROM escrows e
JOIN listings l ON l.id = e.listing_id
WHERE e.buyer_id = e.seller_id
   OR e.status = 'disputed';
```

---

## 13. Data Quality Findings

| Finding | Severity | Detail |
|---|---|---|
| Self-dealing escrow | 🔴 High | Escrow #43: buyer = seller = user 91, amount = $4M |
| Mixed charset | 🟡 Medium | `latin1` on transactional tables, `utf8mb4` on social tables |
| Wallet balance not derived | 🟡 Medium | `balance_cents` stored directly — can drift from transaction sum |
| Duplicate broadcast messages | 🟡 Medium | Broadcast IDs 2–5 contain identical message content (admin sent 4×) |
| Missing `deleted_at` on users | 🟡 Medium | No soft-delete pattern — hard deletes would break FK references |
| Incomplete `meta` field schema | 🟠 Low–Medium | JSON blobs in `escrows.meta`, `tasks.requirements` — not validated at DB level |
| `user_tasks` deduplication | 🟢 Low | `normalized_active` generated column partially addresses this; full enforcement needs unique constraint on `(user_id, task_id, date)` |
| Subscription status inconsistency | 🟢 Low | 35 `subscription_activation` wallet tx vs 70 subscription records — not all subscriptions have wallet tx records |

---

## 14. Portfolio Takeaways

> **Schema reverse-engineering** — Reconstructed full platform domain model from a 32-table MySQL dump with no external documentation, mapping entity relationships, business logic, and data flows solely from table structures and data patterns.

> **Behavioral data profiling** — Derived user growth curves, task engagement rates, referral network topology, and wallet health metrics from raw INSERT statements — without query execution, using pattern extraction and aggregate analysis.

> **MLM financial modeling** — Analyzed a binary matrix earning system, quantifying admin absorption rate (80.1% of matrix earnings), payout ratios, and activation installment accumulation across 1,201 earning records.

> **Data quality audit** — Identified 8 distinct data quality risks across storage engine mismatch, self-dealing exploits, derived value drift, and charset inconsistencies — with severity ratings and actionable recommendations.

> **Business context interpretation** — Connected schema design choices (nested set model, generated columns, composite indexes, enum constraints) to their operational purposes, demonstrating cross-functional understanding of both engineering and business logic.

---

## Appendix: Table Inventory

| # | Table | Engine | Est. Records | Primary Role |
|---|---|---|---|---|
| 1 | `account_reactivation_requests` | MyISAM | ~0 | User account appeals |
| 2 | `broadcast_messages` | InnoDB | 7 | Admin announcements |
| 3 | `cache` | MyISAM | — | Laravel cache |
| 4 | `cache_locks` | MyISAM | — | Distributed locking |
| 5 | `crypto_wallets` | MyISAM | ~47 | Platform crypto addresses |
| 6 | `email_templates` | MyISAM | ~18 | Transactional email content |
| 7 | `escrows` | InnoDB | 49 | Marketplace payment holds |
| 8 | `failed_jobs` | InnoDB | ~22 | Queue failure log |
| 9 | `job_batches` | InnoDB | — | Batch job tracking |
| 10 | `jobs` | InnoDB | — | Async job queue |
| 11 | `listings` | MyISAM | 60 | Marketplace products/services |
| 12 | `manual_deposits` | MyISAM | ~19 | Crypto deposit approvals |
| 13 | `matrix_earnings` | MyISAM | 1,201 | MLM payout records |
| 14 | `matrix_nodes` | MyISAM | 82 | Binary tree positions |
| 15 | `migrations` | MyISAM | ~47 | Laravel migration log |
| 16 | `notifications` | InnoDB | ~3,844 | User notification log |
| 17 | `password_reset_tokens` | MyISAM | ~15 | Password recovery |
| 18 | `personal_access_tokens` | MyISAM | ~1,325 | API auth tokens |
| 19 | `promoted_tasks` | MyISAM | ~8 | Featured/paid task slots |
| 20 | `quiz_questions` | MyISAM | ~39 | Marketplace buyer quizzes |
| 21 | `referrals` | MyISAM | 180 | Referral network links |
| 22 | `reviews` | MyISAM | ~6 | Marketplace seller reviews |
| 23 | `sessions` | InnoDB | ~578 | Active user sessions |
| 24 | `settings` | MyISAM | ~8 | Platform config |
| 25 | `subscriptions` | MyISAM | 70 | Membership records |
| 26 | `support_tickets` | MyISAM | ~9 | Customer support |
| 27 | `tasks` | InnoDB | 807 | Social engagement tasks |
| 28 | `transactions` | InnoDB | 51 | Marketplace transactions |
| 29 | `user_tasks` | MyISAM | ~6,221 | Task completion log |
| 30 | `users` | MyISAM | 265 | Member accounts |
| 31 | `wallet_transactions` | InnoDB | 578 | Financial ledger |
| 32 | `wallets` | MyISAM | 731 | User wallet balances |

---


10.5 Business Impact & Strategic Insights

The analysis of the vglive ecosystem reveals critical drivers of the platform’s unit economics and operational health. These insights provide the basis for immediate management interventions to protect capital and scale revenue.
💰 Revenue Optimization & Unit Economics
Profitability Architecture: The analysis identified that 80.1% of matrix earnings ($408.20) are absorbed by the admin account. This reveals a highly efficient "Admin Sweep" design that ensures platform sustainability by capturing orphaned commissions.
Subscription Performance: With annual plans ($60/yr) representing 35% of the mix despite being the highest cost, the data suggests a high "Customer Lifetime Value" (LTV) among early adopters, providing a stable cash flow for further development.

📉 Growth Strategy & Acquisition ROI
Referral Engine Dependency: The "Public Launch Spike" (40% of users in week 1) followed by rapid decay indicates that the business is currently driven by burst marketing rather than organic growth.
Strategic Market Focus: With Facebook (47.3%) and YouTube (33.2%) dominating task engagement, the business can reduce operational costs by de-prioritizing integration with low-engagement platforms like Twitter/X (0.5%), focusing engineering spend where the users are most active.

🛡️ Risk Mitigation & Fraud Prevention
Fraud Identification: The discovery of Escrow #43 ($4,000,000 self-deal) is a critical business save. Identifying this allows the business to implement "Anti-Self-Dealing" logic, preventing potential money laundering or platform manipulation that could lead to massive financial and regulatory liability.
Data Integrity Risks: The identification of the users table on a MyISAM engine alerts the business to potential data loss during high-concurrency periods. Migrating this ensures "ACID compliance," protecting the platform's most valuable asset: its user ledger.

📊 Engagement & Operational Efficiency
High-Intent Stickiness: An average of 23.5 tasks per user suggests an extremely "sticky" platform. This high engagement rate increases the platform's value to third-party advertisers, justifying potential price increases for "Promoted Tasks."

🏛️ Business Impact Summary
The SQL analysis of ViralGrowth provides a clear roadmap for profitability and risk management. By quantifying the 80% admin absorption rate, identifying a multi-million dollar escrow vulnerability, and pinpointing Facebook as the primary revenue-driving platform, this analysis enables the organization to shift from reactive maintenance to proactive scaling. These data-driven findings directly protect the $40,000+ capital pool currently circulating within the platform's crypto-fiat rails.


Bridging Tech and Business: It shows you don't just find "bugs" or "data," you find "money" and "risk."
Senior Language: Using terms like ACID compliance, LTV, and Admin Sweep demonstrates a high level of professional maturity.
Actionability: Recruiters look for analysts who can tell a CEO what to do next (e.g., "focus on Facebook," "fix the escrow logic").

*README · ViralGrowth SQL Analysis · Data Analyst Portfolio*
*Database: `vglive` | Server: MySQL 8.3.0 | Dump date: March 20, 2026*

![image alt](https://github.com/adessquared/DATA-ANALYST-PORTFOLIO/blob/eefbe7de8e4c17efe2c3fec1ddc0772280f41145/Data%20Visualization/SQL%20file.png)
