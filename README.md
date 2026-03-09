# ViraGrowth — Policy‑Driven Promotion Task Platform

[![Laravel](https://img.shields.io/badge/Laravel-11.x-FF2D20?logo=laravel&logoColor=white)](https://laravel.com/)
[![PHP](https://img.shields.io/badge/PHP-8.2-777BB4?logo=php&logoColor=white)](https://www.php.net/)
![Stack](https://img.shields.io/badge/Stack-Sanctum%20%7C%20Vite%20%7C%20Tailwind%20%7C%20Alpine-blue)
[![CI](https://github.com/adessquared/vg-live-task-platform/actions/workflows/ci.yml/badge.svg)](https://github.com/adessquared/vg-live-task-platform/actions)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Policy‑driven task distribution engine for user‑submitted promotions with 6‑hour scheduling windows, duplicate prevention via URL normalization, compliance‑aware approvals, wallets and payouts, and admin/operator tooling.

## Highlights

- 6‑hour window assignment (00:00, 06:00, 12:00, 18:00)
- Owner gating (configurable): block distribution if promoter has current‑window pending assignments
- Recipient preference (configurable): prefer users with zero current‑window pending, then higher monthly completion rates
- Duplicate prevention: normalized URL canonicalization across major platforms (YouTube/Instagram/TikTok/Twitter/LinkedIn)
- Compliance & approvals: expiry for unsubmitted assignments; auto‑approval threshold; manual review flow
- Wallets & payouts: earnings credited on approvals; Binance Pay and NOWPayments integrations
- Genealogy matrix: nested‑set structure with spillover and deep‑level earnings distribution
- Admin UI: review promoted tasks, batch approve/disapprove, inspect user tasks and transactions
- Observability: structured logs for gating and normalized exclusions; UI chips for Active/Inactive/Queued

## Architecture

- Backend: Laravel 11 (PHP 8.2), Sanctum auth, Predis/Redis
- Frontend: Vite + Tailwind CSS + Alpine.js
- Jobs/Schedule: cron entry triggers 6‑hour generation and housekeeping
- Core modules:
  - TaskService: selection rules, gating, per‑window caps, normalized exclusion
  - WalletService: balances and transactions
  - Matrix module: genealogy and earnings distribution
  - Payments: Binance Pay & NOWPayments via webhooks

## Policy Controls

- `tasks.require_owner_clean_pending` (bool): enable owner gating
- `tasks.prefer_completers` (bool): enable recipient preference ordering
- `tasks.pending_scope` (string): `window` | `day` | `month` (default `window`)
- `tasks.normalized_exclusion_enabled` (bool): enable normalized link duplicate exclusion
- `tasks.expiry_days` (int): assignment expiry for unsubmitted tasks (default 30)
- Auto‑approval threshold (percentage): see `tasks.auto_approval_threshold`

## Quickstart

```bash
# Backend
composer install
cp .env.example .env
php artisan key:generate
# configure DB credentials in .env
php artisan migrate

# Frontend
npm ci
npm run build   # or: npm run dev

# Run
php artisan serve
# for schedulers: set up cron to hit /cron/run (or 'php artisan schedule:run')
```

## Tests & Quality

```bash
# Run tests
php vendor/bin/phpunit --testdox

# Lint (style)
php vendor/bin/pint
```

## Security & Secrets

- Never commit `.env` or credentials; use `.env.example` for placeholders
- Enable GitHub secret scanning and rotate any leaked keys immediately

## Screenshots (placeholders)

- Promoter stats with “Active (Queued)” banner
- Admin “Promoted Tasks” with queued badge
- Wallet/Transactions view
- Matrix earnings and hold status

## License

MIT
