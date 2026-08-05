# Alan Hardesty

**Systems Engineer — Microsoft 365 tenant consolidation and defensible data preservation.**
20+ years in infrastructure and automation.

I work on the unglamorous half of corporate acquisitions: what happens to the Microsoft 365
tenant being absorbed. Moving thousands of users into the acquiring tenant without breaking
their access, and proving to the legal team that everything under hold was preserved before
the old tenant is switched off.

Both halves are automation problems, and both fail in ways that are expensive to discover late.

---

### Post-acquisition tenant consolidation

Users do not move in one operation. They move in batches, through a sequence of permission
grants, coexistence changes, and source-side revocations that have to happen in the right
order — inventory access before you change it, provision the target before you revoke the
source, and never do both in the same pass.

**→ [m365-admin-scripts](https://github.com/AlanHardesty/m365-admin-scripts)** — a four-phase
tenant-to-tenant migration runbook, plus the Exchange and SharePoint tooling used to make the
cutover decisions.

### Defensible preservation

Before a tenant can be deleted, everything under legal hold has to come out of it —
completely, verifiably, and in a form attorneys can rely on. That means multi-terabyte exports
through the Purview eDiscovery API, jobs that run server-side for twelve hours, downloads that
have to survive interruption, and mailboxes whose owning accounts were deleted years ago but
whose data is still legally required.

**→ [purview-ediscovery-export](https://github.com/AlanHardesty/purview-ediscovery-export)** —
automated legal hold export via Microsoft Graph. Resumable collections, byte-range resumable
downloads, and a working path for inactive mailboxes with no directory identity.

---

### How I work

- **Automate what attorneys and PMs would otherwise do by hand.** If a compliance workflow
  depends on someone clicking through a portal correctly every time, it is not defensible.
- **Build for resume, not for success.** Anything that runs for hours will be interrupted.
  State on disk, re-runnable operations, and no step that redoes work already completed.
- **Answer questions from data.** Migration and decommission decisions need evidence about
  what is actually in the tenant, not assumptions about what should be.
- **Write it down as you go.** On a project with no upstream technical direction, the decision
  record is what keeps the work defensible six months later.

### Working with

`PowerShell` · `Microsoft Graph API` · `Exchange Online` · `SharePoint Online / PnP` ·
`Microsoft Purview eDiscovery (Premium)` · `Entra ID` · `Microsoft Teams` · `Azure` ·
`Python` · `Generative AI`

---

B.S. Electronic Engineering ·
[LinkedIn](https://www.linkedin.com/in/alan-hardesty-51064343) ·
[alanhardesty.info](https://alanhardesty.info)
