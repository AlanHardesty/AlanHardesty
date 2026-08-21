# Alan Hardesty

**Systems Engineer — Microsoft 365 tenant consolidation and defensible data preservation.**
20+ years in infrastructure and automation.

I work on the unglamorous half of corporate acquisitions: what happens to the Microsoft 365
tenant being absorbed. Moving thousands of users into the acquiring tenant without breaking
their access, and proving to the legal team that everything under hold was preserved before
the old tenant is switched off.

Both halves are automation problems, and both fail in ways that are expensive to discover late.

---

## What I do

**Tenant-to-tenant migration.** Users don't move in one operation. They move in batches,
through a sequence of permission grants, coexistence changes, and source-side revocations that
have to happen in the right order — inventory access before you change it, provision the target
before you revoke the source, and never do both in the same pass. Get the order wrong and
people lose access to things they still need, usually a week after anyone was watching.

**Defensible preservation.** Before a tenant can be deleted, everything under legal hold has to
come out of it — completely, verifiably, and in a form attorneys can rely on. Multi-terabyte
exports through the Purview eDiscovery API, collections that run server-side for twelve hours,
downloads that have to survive interruption, and mailboxes whose owning accounts were deleted
years ago but whose contents are still legally required.

**Tenant reporting that decisions can rest on.** Cutover and decommission choices need evidence
about what is actually in a tenant — which mailboxes are live, which are forwarding and where,
which are on hold, which shared mailboxes still have delegates. At enterprise scale that is its
own engineering problem, because the obvious implementation doesn't finish inside a
privileged-access window.

---

## Repositories

### [purview-ediscovery-export](https://github.com/AlanHardesty/purview-ediscovery-export)

End-to-end legal hold export via the Microsoft Graph eDiscovery API, built for a tenant
decommission with a multi-terabyte hold estate.

The interesting parts are the failure modes: collections that run server-side for hours and
have to survive the client dying, byte-range resumable downloads for files that fail partway
through, and a working path for inactive mailboxes whose Entra ID accounts no longer exist —
where the identity is gone but the data is still on hold. The README documents the API
behaviour that isn't obvious from the docs, including the search-scoping mistake that makes a
collection gather every custodian in the case instead of the one you asked for.

### [m365-admin-scripts](https://github.com/AlanHardesty/m365-admin-scripts)

A **four-phase tenant-to-tenant migration runbook** — the sequence, the reasoning, and what
breaks when the order is wrong — plus the Exchange and SharePoint tooling used to make the
cutover decisions.

The runbook is documentation rather than code, deliberately. The migration implementation was
client-specific and isn't mine to publish; the phase structure and the operational reasoning
are transferable, and they're the part that takes a migration to learn. The reporting scripts
alongside it are the ones I use to answer questions from data rather than assumption.

---

## How I work

- **Automate what attorneys and project managers would otherwise do by hand.** If a compliance
  workflow depends on someone clicking through a portal correctly every time, it isn't
  defensible.
- **Build for resume, not for success.** Anything that runs for hours will be interrupted.
  State on disk, re-runnable operations, and no step that redoes work already completed.
- **Answer questions from data.** I'd rather spend an afternoon building the report than a
  month acting on an assumption about what's in the tenant.
- **Write the decision record as you go.** Six months later, "why was it done this way" is a
  question someone will ask — often a lawyer, sometimes an auditor, occasionally me.
- **Say what's uncertain.** An export that returned nothing might be a bug or might be an
  accurate result. Knowing which, and being able to show the difference, is the job.

---

## Working with

`PowerShell` · `Microsoft Graph API` · `Exchange Online` · `SharePoint Online / PnP` ·
`Microsoft Purview eDiscovery (Premium)` · `Entra ID` · `Microsoft Teams` · `Azure` ·
`Python` · `Generative AI`

---

Available for work on tenant consolidation, decommissioning, and eDiscovery or legal hold
export — as a specialist alongside a migration team, or end to end.

B.S. Electronic Engineering ·
[LinkedIn](https://www.linkedin.com/in/alan-hardesty-51064343) ·
[alanhardesty.info](https://alanhardesty.info)
