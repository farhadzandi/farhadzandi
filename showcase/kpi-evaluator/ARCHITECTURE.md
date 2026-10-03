# KPI Evaluator — Architecture Notes

## Functional domains

```mermaid
mindmap
  root((KPI Evaluator))
    Governance
      Roles
      Approval
      Audit
      Archive
    Evaluation
      Templates
      Sections
      KPIs
      Mandatory Rules
      Thresholds
      Weights
    Master Data
      Organizations
      Contractors
      Projects
    Operations
      Import
      Compare
      Export
      Backup
      Restore
    AI Assistance
      Summary
      Anomaly Detection
      Trend Analysis
      Natural Language Query
```

## Separation of concerns

The product is easier to maintain when split into distinct layers:

1. **Presentation layer** — forms, dashboards, evaluation screens.
2. **Application layer** — workflows, permissions, orchestration.
3. **Domain layer** — KPI scoring, validation rules, approval state.
4. **Persistence layer** — users, templates, evaluations, audit history.
5. **Integration layer** — SMTP, file import/export, optional AI providers.

## Suggested entities

- User
- Role
- Organization
- Contractor
- Project
- EvaluationTemplate
- EvaluationSection
- KPI
- Evaluation
- EvaluationItem
- Evidence
- Approval
- AuditLog
- ExportJob
- AIConfiguration

## Governance states

```mermaid
stateDiagram-v2
    [*] --> Draft
    Draft --> InProgress
    InProgress --> Submitted
    Submitted --> Approved
    Submitted --> Returned
    Returned --> InProgress
    Approved --> Archived
```
