# Workstream and Iteration Plan

- **Identifier:** PLAN-2026-02-11
- **Version:** v0.1.0
- **Date:** 2026-02-11
- **Status:** Active
- **Author:** Conductor

---

## Context

This plan is produced from a full scan of all 12 active repos on 2026-02-11.
It consolidates 59 issues (24 core module, 3 CLI, 9 Librarian, 6 Journalist,
5 Architect, 5 DevOps, 3 Dev, 2 Historian, 1 QA, 1 AppSec, 1 Conductor)
into coherent Workstreams and a prioritised first Iteration.

Stakeholder priorities (from the 2026-02-10 interview):
- "We need to ship" -- working software over planning artefacts.
- Librarian is "one of the most important roles" -- knowledge coherence matters.
- QA tooling and visualisation are valued, not deferred indefinitely.
- The Journalist news site and issuesFS.ai domain are near-term goals.

---

## Workstreams

### WS-1: Core Platform Stability

**Theme:** Fix confirmed bugs, finish outstanding Phase-2 tasks in the core
`Issues-FS` library and CLI so that every other role can rely on a solid
foundation.

| Source Repo | Issue | Status | Summary |
|-------------|-------|--------|---------|
| Issues-FS | Bug-4 | confirmed | `type_to_label_prefix` uses raw `str`, no `_type_safe` decorator |
| Issues-FS | Bug-5 | confirmed | Three divergent label generation algorithms produce incompatible formats |
| Issues-FS | Bug-6 | confirmed | `parse_label_to_type` false-positive on shorter type prefixes |
| Issues-FS | Bug-8 | confirmed | MGraph implementation does not leverage Type_Safe correctly |
| Issues-FS | Task-5 | todo | Hierarchical path resolution endpoint (B14) |
| Issues-FS | Task-9 | todo | MGraphDB schema and domain layer design (B18) |
| Issues-FS | Task-10 | todo | MGraphDB sync service (B19) |
| Issues-FS | Task-11 | todo | MGraphDB query endpoints (B20) |
| Issues-FS | Task-12 | todo | Graph visualisation endpoints (B21) |
| Issues-FS | Task-14 | todo | Gather and catalogue all LLM guidance docs |
| Issues-FS | Task-15 | todo | Define code comment traceability conventions |
| Issues-FS__CLI | Bug-1 | confirmed | `issues-fs list` returns empty despite issues on disk |
| Issues-FS__CLI | Task-1 | backlog | Test CLI from terminal |
| Issues-FS__CLI | Feature-1 | proposed | Add `issues-fs validate` command |

**Owner:** Dev (implementation), QA (verification), Architect (design decisions on MGraph layer).
**Why first:** Everything else depends on a working core and CLI. The CLI Bug-1 (double-path residual) and the four confirmed type-safety bugs block reliable cross-repo scanning, which the Conductor, Librarian, and Journalist all need.

---

### WS-2: Knowledge Coherence and Documentation

**Theme:** Get the Librarian fully operational -- cataloguing, classifying,
and cross-referencing project knowledge so that it does not degrade as the
ecosystem grows.

| Source Repo | Issue | Status | Summary |
|-------------|-------|--------|---------|
| Librarian | Feature-1 | proposed | Librarian Bootstrap (umbrella) |
| Librarian | Feature-2 | proposed | Classify `to_classify/` docs folder |
| Librarian | Bug-1 | backlog | Issues-FS__Docs not creating tags on dev commits |
| Librarian | Task-1 | backlog | Add `issues-fs-cli` dependency to all repos |
| Librarian | Task-2 | backlog | Catalog debrief: Double-Path Bug Fix (P0) |
| Librarian | Task-3 | backlog | Catalog stakeholder interview and LinkedIn article |
| Librarian | Task-4 | backlog | Respond to stakeholder interview from Librarian perspective |
| Librarian | Task-5 | backlog | Catalog all role responses to stakeholder interview |

**Owner:** Librarian (primary), DevOps (CI fix for tags), Conductor (coordination of cross-role responses).
**Why important:** The stakeholder named the Librarian "one of the most important roles." The `to_classify/` folder currently holds key architecture and philosophy documents in an unstructured heap. Cataloguing the double-path bug fix and the stakeholder interview creates the first real entries in the project knowledge graph.

---

### WS-3: Public Presence -- News Site and Domain

**Theme:** Ship the Journalist news site at `news.issuesFS.ai` and lay the
groundwork for the broader `issuesFS.ai` domain architecture.

| Source Repo | Issue | Status | Summary |
|-------------|-------|--------|---------|
| Architect | Task-4 | **done** | Revert ADR-001 to Jekyll (stakeholder decision) |
| Architect | Task-5 | **done** | Design domain architecture for issuesFS.ai (ADR-002) |
| Dev | Task-3 | **done** | Implement Jekyll news site per ADR-001 |
| DevOps | Task-4 | **done** | Deploy GitHub Pages for news site |
| Journalist | Task-1 | backlog | Write article: P0 Double-Path Bug Fix ships |
| Journalist | Task-2 | backlog | Create daily news bulletin for 2026-02-10 |
| Journalist | Task-5 | backlog | Write synthesis article from all role interview responses |
| Journalist | Task-6 | backlog | Create index page linking all interview resources |

**Status note (2026-02-11):** The infrastructure and architecture for WS-3 is
complete. ADR-001 (Jekyll, Accepted), ADR-002 (issuesFS.ai domain architecture),
the Jekyll site build, and GitHub Pages deployment are all done. The news site
is live at `https://owasp-sbot.github.io/Issues-FS__Dev__Role__Journalist/`.
Custom domain (`news.issuesFS.ai`) is deferred. Remaining items are Journalist
content tasks, two of which (Task-5, Task-6) are blocked on WS-4 role responses.

**Owner:** Journalist (remaining content).
**Why important:** The stakeholder wants to ship. The news site is live and the first externally visible artefact. Content (double-path bug fix article, stakeholder interview synthesis) is ready to be written.

---

### WS-4: Stakeholder Interview Response Cycle

**Theme:** Complete the coordinated 10-role response to the stakeholder
interview, then synthesise and publish.

| Source Repo | Issue | Status | Summary |
|-------------|-------|--------|---------|
| Conductor | Task-1 | backlog | Respond from Conductor perspective |
| Dev | Task-2 | backlog | Respond from Dev perspective |
| Architect | Task-3 | backlog | Respond from Architect perspective |
| QA | Task-1 | backlog | Respond from QA perspective |
| AppSec | Task-1 | backlog | Respond from AppSec perspective |
| DevOps | Task-2 | backlog | Respond from DevOps perspective |
| Librarian | Task-4 | backlog | Respond from Librarian perspective |
| Historian | Task-1 | backlog | Respond from Historian perspective |
| Historian | Task-2 | backlog | Capture narrative arc of interview and responses |
| Journalist | Task-5 | backlog | Write synthesis article (depends on all 9 responses) |
| Journalist | Task-6 | backlog | Create index page (depends on synthesis) |
| Librarian | Task-5 | backlog | Catalog all role responses (depends on all 9 responses) |

**Owner:** Each role writes its own response; Conductor coordinates; Journalist synthesises; Librarian catalogues.
**Why important:** This is the first multi-role coordination exercise. Successfully completing it validates the entire role-based workflow and produces a compelling public narrative. It is also a prerequisite for content on the news site.

---

### WS-5: Infrastructure and Housekeeping

**Theme:** Clean up post-merge debris, fix CI inconsistencies, and ensure
the repo ecosystem is healthy.

| Source Repo | Issue | Status | Summary |
|-------------|-------|--------|---------|
| DevOps | Task-5 | backlog | Post-merge review: leftover branches, tag/commit mapping, .gitmodules mismatch |
| Librarian | Bug-1 | backlog | Issues-FS__Docs not creating tags on dev commits |
| Librarian | Task-1 | backlog | Add `issues-fs-cli` dependency to all repos |

**Owner:** DevOps (branch cleanup, CI fixes), Librarian (dependency rollout).
**Why important:** Twelve leftover `claude/*` branches across six repos, a `.gitmodules` branch mismatch in 12 repos, and missing CI tags create noise and confusion. This is not urgent but grows more expensive to fix the longer it is deferred.

---

## Iteration 1: "Ship and Stabilise"

**Goal:** Fix the critical bugs that block reliable operation, complete the
stakeholder interview responses, and get the Librarian producing real
catalogue entries.

**Duration:** One focused work cycle (target: 2-3 sessions).

### Iteration 1 Items

#### 1. Fix CLI double-path residual (WS-1)

- **What:** Investigate and resolve CLI Bug-1 (`issues-fs list` returning empty on some repos). The P0 double-path bug was fixed in the core library; verify the fix propagates fully to the CLI.
- **Owner:** Dev
- **Dependencies:** None (can start immediately).
- **Definition of Done:** `issues-fs list` returns correct results in all 12 scanned repos. CLI Bug-1 status updated to `resolved`.

#### 2. Fix confirmed type-safety bugs (WS-1)

- **What:** Resolve Bug-4 (raw `str` in `type_to_label_prefix`), Bug-5 (divergent label algorithms), Bug-6 (`parse_label_to_type` false-positive). These three are related and should be fixed together.
- **Owner:** Dev
- **Dependencies:** None (can start immediately, parallel with item 1).
- **Definition of Done:** All three bugs resolved. All existing tests pass. QA verifies label generation is consistent across all code paths.

#### 3. Complete all 9 role interview responses (WS-4)

- **What:** Each role that has not yet responded writes its response to the stakeholder interview transcript.
- **Owner:** Each role (Conductor, Dev, Architect, QA, AppSec, DevOps, Librarian, Historian).
- **Dependencies:** Interview transcript already exists. No technical blockers.
- **Definition of Done:** Each role repo contains a response document. Corresponding task updated to `done`.

#### 4. Librarian: Catalog the Double-Path Bug Fix debrief (WS-2)

- **What:** Catalog the Dev debrief (`debrief__2026-02-10__double-path-bug-fix.md`) as a primary source. Cross-reference with the CLI assessment. This is the Librarian's first real cataloguing action.
- **Owner:** Librarian
- **Dependencies:** None (source document already exists).
- **Definition of Done:** Catalog entry created. Cross-references to CLI assessment documented. Librarian Task-2 updated to `done`.

#### 5. Librarian: Catalog the stakeholder interview (WS-2)

- **What:** Catalog the ChatGPT voice brief, raw transcript, and LinkedIn article as primary sources. Tag and cross-reference.
- **Owner:** Librarian
- **Dependencies:** None (source documents already exist).
- **Definition of Done:** All three artefacts catalogued. Librarian Task-3 updated to `done`.

#### 6. ~~Architect: Finalise ADR-001 as Jekyll (WS-3)~~ **DONE**

- **Status:** Completed prior to this plan. ADR-001 accepted as Jekyll, ADR-002 (domain architecture) also completed. Jekyll site built and deployed. News site live at GitHub Pages.
- **Implication:** The Dev Task-3 and DevOps Task-4 items listed in the backlog below are also done. Iteration 2 WS-3 work reduces to Journalist content only.

---

### Iteration 1 -- Not Included (Backlog)

The following items are important but deferred to Iteration 2 or later:

| Item | Workstream | Reason for Deferral |
|------|------------|---------------------|
| Bug-8: MGraph Type_Safe rework | WS-1 | Depends on design clarity from Task-9 (MGraphDB schema design) |
| Task-5: Hierarchical path resolution (B14) | WS-1 | Lower priority than bug fixes |
| Task-9 -- Task-12: MGraphDB layer (B18-B21) | WS-1 | Multi-task chain; needs Architect input on schema first |
| Task-14, Task-15: LLM docs and traceability | WS-1 | Process improvement, not a shipping blocker |
| Feature-2: Classify to_classify docs | WS-2 | Valuable but large; Librarian should build cataloguing muscle on smaller items first |
| ~~Dev Task-3: Build Jekyll news site~~ | WS-3 | **DONE** -- site built and deployed |
| ~~DevOps Task-4: Deploy GitHub Pages~~ | WS-3 | **DONE** -- live at GitHub Pages |
| ~~Architect Task-5: issuesFS.ai domain architecture~~ | WS-3 | **DONE** -- ADR-002 accepted |
| Journalist Task-1, Task-2: Articles | WS-3 | Site is live; content can be published now |
| Journalist Task-5, Task-6: Synthesis and index | WS-4 | Blocked by all 9 role responses completing |
| Librarian Task-5: Catalog all responses | WS-4 | Blocked by all 9 role responses completing |
| DevOps Task-5: Post-merge cleanup | WS-5 | Important hygiene but not blocking any current work |
| CLI Feature-1: `issues-fs validate` | WS-1 | Nice-to-have, not needed for current operations |

---

## Dependency Graph (Iteration 1)

```
[Item 1: Fix CLI Bug-1] ──────────────────────────────────> (enables reliable scanning)
[Item 2: Fix type-safety bugs] ───────────────────────────> (enables correct label handling)
[Item 3: All 9 role interview responses] ─────────────────> (enables Journalist synthesis in Iteration 2)
[Item 4: Catalog bug fix debrief] ────────────────────────> (Librarian first real catalogue entry)
[Item 5: Catalog stakeholder interview] ──────────────────> (Librarian builds cross-reference practice)
[Item 6: Finalise ADR-001 Jekyll] ────> [Iteration 2: Dev builds site] ────> [Iteration 2: DevOps deploys]
```

Items 1-5 are independent and can be worked in parallel.
Item 6 is independent but unblocks the WS-3 chain in Iteration 2.

---

## Success Criteria for Iteration 1

1. `issues-fs list` works correctly across all repos (CLI Bug-1 resolved).
2. Label generation is consistent -- no divergent algorithms (Bug-4, Bug-5, Bug-6 resolved).
3. All 9 role interview responses exist in their respective repos.
4. The Librarian has produced at least two catalogue entries (bug fix debrief, stakeholder interview).
5. ~~ADR-001 is finalised as Jekyll/Accepted, unblocking the news site build.~~ **DONE** -- ADR-001 accepted, site live.

---

## Iteration 2 Preview (Not Scheduled)

- ~~**Build and deploy the Jekyll news site**~~ **DONE** -- live at GitHub Pages.
- **Journalist publishes first articles** (site is ready, content can go live now).
- **MGraphDB schema design** (Architect leads Task-9, unblocking Tasks 10-12).
- **Journalist synthesis article** (depends on all 9 role responses from Iteration 1).
- **Classify to_classify docs** (Librarian Feature-2).
- **Post-merge branch and tag cleanup** (DevOps Task-5).
- ~~**issuesFS.ai domain architecture ADR** (Architect Task-5).~~ **DONE** -- ADR-002 accepted.
- **Configure custom domain** `news.issuesFS.ai` (DNS CNAME + GitHub Pages settings).

---

*Produced by the Conductor role on 2026-02-11 from a full scan of the Issues-FS ecosystem.*
