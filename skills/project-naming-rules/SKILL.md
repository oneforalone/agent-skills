---
name: project-naming-rules
description: Enforce project naming rules for documentation, API paths, URLs, code identifiers, database fields, and source filenames. Use when creating, reviewing, renaming, or normalizing project names across docs, routes, schemas, migrations, files, or code.
---

# Project Naming Rules

## Core Rule

Use names that are concise, logical, and semantically precise. Prefer the shortest common form that preserves meaning.

Case conventions:

- Documentation files, API paths, and URLs: use `kebab-case`.
- Code identifiers, database fields, and source filenames: use `snake_case`.

Apply the rule to new work by default. For existing public or external names, avoid breaking compatibility unless the task explicitly includes a migration or compatibility plan.

## Format Rules

Documentation, API, and URL names:

- Use lowercase words separated by hyphens.
- Prefer path segments that read as resources or actions.
- Examples: `auth-feats.md`, `/api/user-configs`, `/billing/req-history`.

Code, database, and source file names:

- Use lowercase words separated by underscores.
- Apply to variables, functions, modules, database columns, table names, migration names, and code filenames. If a language or framework mandates another casing for exported types or components, keep the required casing but still keep the words concise and semantic.
- Examples: `auth_feats.py`, `user_cfg`, `resp_body`, `req_id`, `tx_id`, `user_req_logs`.

## Abbreviation Rules

Prefer common, unambiguous abbreviations over long words:

- `feature` or `features` -> `feat` or `feats`
- `configuration`, `config`, or their plurals in code -> `cfg` or `cfgs`
- `configurations` in docs/API/URL -> `configs`
- `response` -> `resp`
- `request` or `requests` -> `req` or `reqs`
- `transaction` or `transactions` -> `tx` or `txs`

Use domain abbreviations only where they are conventional for the surface:

- Computer/software code identifiers: `application` -> `app`, `authentication` -> `auth`, `database` -> `db`, `connection` -> `conn`, `synchronization` -> `sync`, `identifier` -> `id`.
- Network code identifiers: `address` -> `addr`, `internet protocol` -> `ip`, `domain name system` -> `dns`, `hypertext transfer protocol` -> `http`, `transmission control protocol` -> `tcp`, `websocket` -> `ws`.
- Finance code identifiers: `account` -> `acc`, `balance` -> `bal`, `transaction` -> `tx`, `portfolio` -> `pf`, `profit and loss` -> `pnl`, `net asset value` -> `nav`.
- Do not apply code-only domain abbreviations to file names, API paths, URLs, or database fields unless the abbreviation is already the canonical domain term.
- Use `acc` for account only in finance/accounting context; keep a clearer name if `acc` could mean accumulator, access, or another local concept.

Use the same abbreviation across surfaces unless this skill defines a surface-specific form:

- Documentation/API/URL: `tx-history`, `req-queue`, `config-example`.
- Code/database/source files: `tx_history`, `req_queue`, `cfg_example`.
- Configuration naming is intentionally surface-specific: use `config` or `configs` in docs/API/URL, and `cfg` or `cfgs` in code/database/source filenames.
- Portfolio naming is intentionally surface-specific: use `pf` only for code identifiers; use `portfolio` in file names, API paths, URLs, and database fields.

Use the form that matches the meaning:

- Use singular names for one item: `req`, `user_cfg`, `auth-feat`.
- Use plural names for collections: `reqs`, `user_configs`, `auth-feats`.
- Do not abbreviate domain terms when the shorter form would be unclear.

## Examples

Documentation, API, and URL examples:

| Avoid                              | Prefer                      | Reason                                                      |
| ---------------------------------- | --------------------------- | ----------------------------------------------------------- |
| `feature-configurations.md`        | `feat-configs.md`           | Shorter, still clear, keeps `kebab-case`.                   |
| `/api/user-requests-history`       | `/api/user-req-history`     | `requests` becomes `req`, and the path stays resource-like. |
| `/transactions/response-examples`  | `/txs/resp-examples`        | Uses common `txs` and `resp` abbreviations.                 |
| `configuration-migration-guide.md` | `config-migration-guide.md` | Docs use the readable `config` form.                        |

Code, database, and source filename examples:

| Avoid                       | Prefer          | Reason                                                            |
| --------------------------- | --------------- | ----------------------------------------------------------------- |
| `feature_configurations.py` | `feat_cfgs.py`  | Code uses `cfgs`, not verbose `configurations`.                   |
| `transaction_response`      | `tx_resp`       | Both terms have common short forms.                               |
| `request_identifier`        | `req_id`        | `id` is the standard short form for identifiers.                  |
| `user_transactions`         | `user_txs`      | Collection name stays plural.                                     |
| `configuration_loader.py`   | `cfg_loader.py` | Source filename follows `snake_case` and code abbreviation rules. |

Domain abbreviation examples:

| Surface                | Avoid                         | Prefer                  | Reason                                                                 |
| ---------------------- | ----------------------------- | ----------------------- | ---------------------------------------------------------------------- |
| Code identifier        | `database_connection`         | `db_conn`               | `db` and `conn` are conventional software abbreviations.               |
| Code identifier        | `internet_protocol_address`   | `ip_addr`               | Network code commonly uses `ip` and `addr`.                            |
| Code identifier        | `domain_name_system_response` | `dns_resp`              | Keep protocol terms compact without losing meaning.                    |
| Code identifier        | `portfolio_value`             | `pf_value`              | `pf` is acceptable for local code identifiers.                         |
| Code identifier        | `account_balance`             | `acc_bal`               | Finance code commonly shortens account and balance.                    |
| Code identifier        | `profit_and_loss_summary`     | `pnl_summary`           | `pnl` is the canonical finance abbreviation.                           |
| Documentation filename | `pf-overview.md`              | `portfolio-overview.md` | Do not abbreviate `portfolio` in file names.                           |
| Source filename        | `pf_sync.py`                  | `portfolio_sync.py`     | Do not abbreviate `portfolio` in filenames.                            |
| API/URL                | `/api/pf-txs`                 | `/api/portfolio-txs`    | Public routes should keep `portfolio` readable.                        |
| Database field         | `pf_id`                       | `portfolio_id`          | Persisted schema names should not use the code-only `pf` abbreviation. |

## Review Checklist

When reviewing names:

1. Classify the surface: docs/API/URL uses `kebab-case`; code/database/source files use `snake_case`.
2. Check that each word carries useful domain meaning.
3. Replace verbose terms with approved common abbreviations when clarity remains intact.
4. Remove filler words such as `data`, `info`, `manager`, `helper`, or `utils` unless they describe the actual responsibility.
5. Keep compatibility risks visible before renaming public APIs, URLs, database fields, or persisted identifiers.
