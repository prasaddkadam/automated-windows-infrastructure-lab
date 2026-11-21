# Design decisions and repository standards

This file records the agreed design and collaboration conventions. Changes require review before committing.

## ADR-001 — Single-node Proxmox VE

**Decision:** Replace the existing standalone ESXi environment with Proxmox VE on the existing bare metal host. **Why:** A small single-node lab can practise VM administration and API-based provisioning without a paid virtualisation management layer or cluster complexity. **Trade-off:** One host and one internal disk are failure domains; backups and recovery evidence are mandatory.

## ADR-002 — Separate provisioning and Windows configuration

**Decision:** Terraform provisions Proxmox resources; PowerShell configures Windows guest roles, AD DS, DNS, file services and identities. **Why:** Clear separation of desired infrastructure from OS/service configuration simplifies verification and troubleshooting. **Trade-off:** Deployment needs explicit guest readiness and ordering checks.

## ADR-003 — Minimum viable Windows infrastructure

**Decision:** Start with DC01 and FS01. CLIENT01 is optional after measured resource headroom. No separate Linux automation VM or clustering in v1.0.0. **Why:** The physical machine has limited internal disk capacity; completion matters more than breadth.

## ADR-004 — Public repository information controls

**Decision:** Refer to the physical computer only as **Bare Metal Host**. Never publish the original equipment manufacturer or model, serial numbers, hardware asset identifiers, identifiable screenshots, real user data, secrets, live Terraform state or actual private network assignments. **Why:** Avoid disclosure of the physical host's origin and environment-specific details. Sanitise scripts, logs and diagrams before publication.

## ADR-005 — Visual diagrams

**Decision:** Store approved, self-contained SVG architecture diagrams under `docs/diagrams/` and embed them in Markdown. Prefer clear dark-theme layouts, visible labels, consistent spacing and accessible text. Diagrams are architecture-only: no project phase, date, milestone, deployment status or temporary progress badges. **Why:** SVG is scalable, diffable and renders on GitHub. **Control:** Review both the visual rendering and raw SVG for unwanted text or links before committing. Avoid remote assets and scripts in SVGs.

## ADR-006 — Commit format and approval gate

**Decision:** Commit messages follow **`component: concise description`**, for example `docs: establish project foundation and architecture`, `terraform: add VM lifecycle configuration`, or `powershell: add AD identity checks`. Do **not** use `feat(terraform):` or similar Conventional Commits scopes. **Control:** Present planned files, content and diagrams for explicit user review and approval **before each commit**.

## ADR-007 — Minimal Git workflow

**Decision:** `main` represents an approved working baseline; use descriptively named branches for implementation where warranted. Record milestones and exceptions in the project log. **Why:** A traceable, reviewable portfolio with manageable overhead.

## Open decisions

- Exact Proxmox version, filesystem/installer partition sizes, update repository selection and NIC compatibility.
- Real home LAN addressing and final lab DNS namespace (not for public commits).
- Windows Server edition/evaluation terms, initial template size, guest drivers and cloning mechanism.
- Proxmox Terraform provider/version and scoped API authentication model.
- Backup destination, retention and supported AD restoration runbook.
