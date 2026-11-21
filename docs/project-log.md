# Project log

## 2026-11-21 — Phase 0: Architecture planning

**Status:** Planning; no infrastructure changes performed.

**Agreed baseline:** Standalone Proxmox VE; Terraform on the management workstation for VM lifecycle; PowerShell for guest and AD configuration; DC01 and FS01 as mandatory Windows Server VMs; CLIENT01 optional. Internal NVMe is the initial live VM storage. External removable storage may be assessed for backups, not critical running VMs.

**Repository requirements:** Public documentation must not identify the physical host's manufacturer/model or other sensitive hardware details. Commit messages use `component: summary`. All content and visual diagrams require approval before committing.

**Next checkpoint:** Read-only physical host and storage assessment, followed by finalised Proxmox installation plan.

**Verification evidence:** No installation or operational validation evidence yet. Document actual results only after checks are executed.

## Milestone status

| Phase | Status | Evidence |
|---|---|---|
| 0 — Planning | In progress | Proposed architecture, design decisions and risks |
| 1 — Proxmox platform | Not started | — |
| 2 — Guest baseline | Not started | — |
| 3 — Terraform automation | Not started | — |
| 4 — Active Directory and DNS | Not started | — |
| 5 — Identity, file services and GPO | Not started | — |
| 6 — Operations and recovery | Not started | — |
| 7 — Release | Not started | — |
