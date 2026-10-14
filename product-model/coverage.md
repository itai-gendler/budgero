---
scope: 'The web app and Push API of Budgero across the shared core, the app, the local-first runtime, the API server and the Python SDK: budgeting, accounts and transactions, recurring transactions, rules, currencies, payees and labels, imports, exports, the audit log, reports, workspaces and sharing, and master-password encryption.'
method: Static inspection of source, tests and the published documentation; no code was executed.
covered:
- description: Shared domain services for budgets, Ready to Assign, categories, goals, accounts, transactions, splits, payees, labels and recurring transactions.
  paths:
  - packages/core/src/services/monthly-budgets/
  - packages/core/src/services/budgets/
  - packages/core/src/services/categories/
  - packages/core/src/services/goals/
  - packages/core/src/services/recurring/
  - packages/core/src/services/transactions/
  - packages/core/src/services/accounts/
  - packages/core/src/services/user-meta/
- description: Shared services for rules, currencies, import and import history, export, the audit log, scenarios, saved reports and custom dashboards.
  paths:
  - packages/core/src/services/rules/
  - packages/core/src/services/currency/
  - packages/core/src/services/import/
  - packages/core/src/services/export/
  - packages/core/src/services/mutation-history/
  - packages/core/src/services/scenarios/
  - packages/core/src/services/reports/
  - packages/core/src/services/custom-dashboards/
- description: App features and pages for planning, goals, categories, budgets, accounts, transactions and recurring transactions.
  paths:
  - packages/app/src/features/budget-planning/
  - packages/app/src/features/goal-management/
  - packages/app/src/features/category-management/
  - packages/app/src/features/account-management/
  - packages/app/src/features/transactions/
  - packages/app/src/features/recurring/
  - packages/app/src/features/budget-management/
  - packages/app/src/pages/budgeting/
  - packages/app/src/pages/accounts/
  - packages/app/src/pages/settings/recurring/
  - packages/app/src/pages/settings/RecurringTransactionsPage.tsx
  - packages/app/src/pages/settings/BudgetSettingsPage.tsx
- description: App features and settings pages for rules, currencies, payees, labels, imports, the audit log, data management and the Push API.
  paths:
  - packages/app/src/features/rules/
  - packages/app/src/features/currencies/
  - packages/app/src/features/payees/
  - packages/app/src/features/labels/
  - packages/app/src/features/import/
  - packages/app/src/pages/settings/automation-rules/
  - packages/app/src/pages/settings/AutomationRulesPage.tsx
  - packages/app/src/pages/settings/CurrencySettingsPage.tsx
  - packages/app/src/pages/settings/PayeesPage.tsx
  - packages/app/src/pages/settings/LabelsPage.tsx
  - packages/app/src/pages/settings/ImportsPage.tsx
  - packages/app/src/pages/settings/AuditLogPage.tsx
  - packages/app/src/pages/settings/DataManagementPage.tsx
  - packages/app/src/pages/settings/push-api/
- description: 'App report pages: prebuilt reports and the scenario planner, the Explorer and custom dashboards.'
  paths:
  - packages/app/src/pages/analytics/
  - packages/app/src/pages/explorer-page/
  - packages/app/src/pages/custom-dashboards/
  - packages/app/src/features/analytics/
  - packages/app/src/features/reports/
  - packages/app/src/features/custom-dashboards/
- description: App operation registry and runtime hooks that run mutations, continuous rules and the push queue.
  paths:
  - packages/app/src/shared/mutations/
  - packages/app/src/shared/runtime/app-runtime.ts
  - packages/app/src/entities/
- description: Workspace sharing, invitations, startup gates, master password and sign-in in the app.
  paths:
  - packages/app/src/features/budget-sharing/
  - packages/app/src/pages/settings/WorkspaceSettingsPage.tsx
  - packages/app/src/pages/JoinWorkspacePage.tsx
  - packages/app/src/pages/settings/SecurityPage.tsx
  - packages/app/src/app/startup/
  - packages/app/src/app/service-guard/
  - packages/app/src/pages/auth/
- description: Client-side encryption and key storage in the local-first runtime.
  paths:
  - packages/runtime/src/crypto/
  - packages/runtime/src/key-vault/
- description: API server application services, domain types, routes and HTTP handlers for workspaces, invitations, members, local accounts, master-password reset and the Push API.
  paths:
  - packages/server/internal/application/
  - packages/server/internal/domain/
  - packages/server/internal/adapter/driving/http/handler/
  - packages/server/internal/adapter/driving/http/routes/
  - packages/server/internal/config/
- description: Python SDK for the Push API.
  paths:
  - packages/sdk-python/
- description: Local database schema and migrations backing the mapped entities.
  paths:
  - packages/core/src/database/
exclusions:
- description: Marketing and documentation website code.
  paths:
  - packages/website/
- description: Shared lint configuration, CI workflows, build and release scripts, runner infrastructure and translation tooling.
  paths:
  - packages/eslint-config/
  - .github/
  - scripts/
  - infra/
  - i18n/
- description: 'Sync diagnostics page and feature: developer diagnostics of the sync engine, not product behavior.'
  paths:
  - packages/app/src/features/sync-diagnostics/
  - packages/app/src/pages/settings/SyncStatusPage.tsx
unmapped:
- description: 'Bank sync and its relay — left out: a beta integration whose consent and data flow are owned by the external providers Enable Banking and SimpleFIN.'
  paths:
  - packages/core/src/services/bank-sync/
  - packages/app/src/features/bank-sync/
  - packages/app/src/pages/settings/bank-sync/
  - packages/server/internal/adapter/driving/http/handler/bank_relay.go
- description: 'AI assistant and chat — left out: an optional assistant on local or cloud language models that the README and docs do not list among the product''s features.'
  paths:
  - packages/core/src/services/chat/
  - packages/app/src/features/chat/
  - packages/app/src/features/ai/
  - packages/core/src/services/llm-settings/
  - packages/app/src/pages/settings/ai/
- description: 'Warranty tracking — left out: a side tool the README and docs do not list among the product''s features.'
  paths:
  - packages/core/src/services/warranties/
  - packages/app/src/pages/warranties/
- description: 'Admin console, subscriptions and account profile settings — left out: internal administration and billing handled with the identity and payment providers.'
  paths:
  - packages/app/src/features/admin/
  - packages/app/src/pages/admin/
  - packages/app/src/features/subscription/
  - packages/app/src/pages/settings/subscription/
  - packages/app/src/pages/settings/AccountSettingsPage.tsx
- description: 'Self-host command line — left out: operator tooling for running an instance, outside the product people budget in.'
  paths:
  - packages/server/cmd/
- description: 'Onboarding flow — left out: a guided wrapper over capabilities the model already describes.'
  paths:
  - packages/app/src/pages/onboarding/
  - packages/app/src/features/onboarding/
- description: 'Home dashboard, navigation widgets and command palette — left out: summary views and shortcuts over data and abilities the model already covers.'
  paths:
  - packages/app/src/pages/dashboard/
  - packages/app/src/widgets/
- description: 'Appearance, about, feedback and app-update screens — left out: cosmetic preferences and peripheral app chrome.'
  paths:
  - packages/app/src/pages/settings/AppearancePage.tsx
  - packages/app/src/pages/settings/AboutPage.tsx
  - packages/app/src/features/feedback/
  - packages/app/src/features/app-update/
limitations:
- description: 'Sync transport, snapshot upload and offline queue: conflict and catch-up behavior between devices could not be established statically.'
  paths:
  - packages/runtime/src/sync-transport/
  - packages/runtime/src/database-sync/
  - packages/runtime/src/offline-queue/
---

# Coverage
