# DevBoard — Deep Product & Market Research

**Owner / Content Creator:** Sandeep Barupal  
**Copyright:** © 2026 Sandeep Barupal. All rights reserved, except third-party materials under their respective terms.  
**Research status:** Deep-research baseline v1.0 — desk research, pending customer validation.

## 1. Product thesis
DevBoard is an internal developer portal / platform engineering workspace. It should reduce developer cognitive load by making services, ownership, documentation, operational health and approved self-service actions discoverable in one place. It should not become a decorative link directory.

## 2. Category landscape
Internal developer platforms commonly combine a software catalog, templates/scaffolding, documentation, scorecards, integrations and self-service workflows. Backstage is an extensible open-source framework; managed alternatives emphasize reduced maintenance and faster setup; platform orchestrators focus more on environment provisioning. A key build-vs-buy choice is whether DevBoard is a portal, an orchestrator, or a deliberate combination. Sources: [Backstage docs](https://backstage.io/docs/), [Backstage technical overview](https://backstage.io/docs/overview/technical-overview/), [Humanitec IDP overview](https://humanitec.com/internal-developer-portal).

## 3. Competitive comparison framework
| Reference | Category | Strength to study | Trade-off / research question |
|---|---|---|---|
| Backstage | Open-source developer portal framework | Extensibility, software catalog, plugin ecosystem | Who owns upgrades, plugins, deployment and UX consistency? |
| Port / Cortex / OpsLevel | Managed portal / catalog / scorecards | Faster adoption, governance and service maturity workflows | Pricing, integration coverage, data model flexibility, lock-in |
| Humanitec | Platform orchestration | Standardized deployment and environment provisioning | How tightly should portal workflows couple to infrastructure provisioning? |
| GitHub / GitLab | Source and CI/CD platforms | Existing developer workflows and identity | DevBoard should integrate rather than duplicate repository and pipeline systems |

Do not treat this table as a scored vendor ranking; perform dated product-by-product tests before selecting vendors.

## 4. Users and jobs
- Developer: find the right service, owner, docs, runbook and deploy path.
- Platform engineer: publish safe golden paths and reusable templates.
- Service owner: maintain metadata, operational readiness and dependencies.
- Security/compliance: apply controls without forcing every team through manual tickets.
- Engineering leader: identify orphaned services, maturity gaps and delivery friction.

## 5. Feature specification
### P0
- Software catalog: service, API, library, job, website, owner, lifecycle, repo, docs and dependencies.
- Search and filters; owner resolution; stale metadata and orphaned-service warnings.
- Templates with validated inputs, preview, generated repo and post-creation checks.
- Documentation links and runbook discovery.
- SSO/OIDC, role-based access, audit log and admin console.
- Integrations with Git provider and CI status; health is explicitly marked stale when data is old.
### P1
- Scorecards with versioned policies and waivers; evidence links for each check.
- Dependency graph and blast-radius view.
- Self-service environment request with approval, quota and expiry.
- Golden paths with template versions, migration notes and adoption analytics.
### P2
- Policy-as-code, developer environment provisioning, AI-assisted service discovery and change impact analysis.

## 6. Page map
Home; Software Catalog; Service Detail; APIs; Dependencies Graph; Templates; Create Component wizard; Documentation; Scorecards; Self-Service Actions; Integrations; Activity/Audit; Team Ownership; Admin; Settings.

## 7. Architecture
Build a metadata ingestion layer, canonical catalog schema, integration adapters, search index, workflow engine, policy evaluator, API service and web UI. Keep source-of-truth metadata in version control where feasible; record provenance and sync time. Plugins should be isolated and permission-scoped. Template execution must run in controlled workers with allow-listed actions, short-lived credentials and logs.

## 8. Security and governance
Protect repository tokens; least privilege; tenant and team scoping; prevent template injection; require approval for privileged actions; audit generated repositories and provisioning; secret scanning for generated output; explicit permission boundaries between catalog read and infrastructure write actions.

## 9. Success metrics
Time to first successful service; catalog ownership coverage; percentage of services with current docs/runbooks; template completion rate; median time to provision a standard environment; failed self-service actions; developer satisfaction; adoption by team. Avoid vanity metrics like catalog page views without workflow completion.

## 10. Validation plan and risks
Risks: stale catalog, plugin sprawl, complex setup, low adoption, scorecards used punitively, dangerous self-service actions. Interview developers and platform teams; observe a new-service creation end-to-end; measure how often users leave the portal to find owner/docs/pipeline. Test the product as a workflow, not just a dashboard.

## 11. References
- [Backstage documentation](https://backstage.io/docs/)
- [Software Catalog](https://backstage.io/docs/features/software-catalog/)
- [Backstage technical overview](https://backstage.io/docs/overview/technical-overview/)
- [Humanitec internal developer portal](https://humanitec.com/internal-developer-portal)
- [GitHub Codespaces documentation](https://docs.github.com/en/codespaces)

## 12. Next work
Create a dated matrix of 5–8 platforms, test catalog/template/scorecard workflows, validate integration coverage, and turn MVP features into user stories with permission-specific acceptance criteria.