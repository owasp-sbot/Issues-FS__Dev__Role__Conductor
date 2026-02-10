# Issues-FS Ecosystem: Roadmap and Next Steps

**Author:** Conductor Role
**Date:** 2026-02-09
**Status:** Draft

---

## 1. Current State Assessment

### 1.1 Ecosystem Topology

17 repositories organized as git submodules under `Issues-FS__Dev` (v0.2.10):

| Category | Count | Repos |
|----------|-------|-------|
| **Modules** | 6 | Issues-FS, CLI, Service, Service Client Python, Service UI, Docs |
| **Role repos** | 10 | Conductor, Architect, Dev, QA, DevOps, Librarian, AppSec, Cartographer, Historian, Journalist |
| **Human repos** | 1 | Dinis Cruz |

### 1.2 Module Maturity

| Module | Version | Test Coverage | Maturity |
|--------|---------|--------------|----------|
| **Issues-FS** (core) | v0.4.5 | 457 tests, all pass | **Production-grade core** |
| **Issues-FS__CLI** | v0.2.2 | 92 tests, all pass | **Functional but has critical bug** |
| **Issues-FS__Service** | v0.2.2 | 20 test files, untestable locally | **Functional REST API** |
| **Service Client** | v0.2.2 | Minimal | **Skeletal -- needs assessment** |
| **Service UI** | v0.1.9 | 4 test files | **Active dogfooding target** |
| **Docs** | v0.1.4 | Minimal | **Content-rich but disorganized** |

### 1.3 Key Findings

**Strengths:**
1. Core architecture is solid (v0.4.5, 457 passing tests)
2. CI infrastructure is comprehensive (9/10 role repos have 3-file pipeline)
3. All 10 roles have well-defined ROLE.md files
4. Dogfooding is happening (Service UI has 58 issue data files)
5. Design documentation is extensive

**Weaknesses:**
1. **Critical: `issues-fs list` returns no results** despite issues existing on disk
2. Service Client Python appears hollow (schemas missing)
3. 9 of 12 repos have empty issue trackers
4. Docs `to_classify/` backlog is growing
5. Role coordination system (Handoff, Decision, Blocker) is not in use
6. QA role repo is structurally incomplete

---

## 2. Recommended Next Phase: "Make the Foundation Reliable"

**Phase Name:** Foundation Hardening (v0.5.0 target)

**Phase Goal:** Every module's core functionality works reliably, issues are tracked in every active repo, the CLI can scan the full ecosystem, and the first cross-role coordination workflow is executed end-to-end.

**Principle:** _A Conductor cannot orchestrate what it cannot observe. An ecosystem cannot coordinate through issues if the issue tooling does not work._

---

## 3. Prioritized Roadmap

### 3.1 Near-Term (Next 1-2 Sprints) -- "Fix and Verify"

| Priority | Item | Owner | Acceptance Criteria |
|----------|------|-------|-------------------|
| **P0** | **Fix `issues-fs list` CLI bug** | Dev | `issues-fs list` returns issues for repos with data in `.issues/data/` |
| **P0** | **Assess Service Client Python schemas** | Architect | Determine where API schemas live, update project brief |
| **P1** | **Complete QA role repo structure** | DevOps | CI pipelines, package structure matching other role repos |
| **P1** | **Reconcile `to_refactor-in/` in core** | Dev + Architect | Either integrate or explicitly archive |
| **P2** | **Track issues in every active module** | All roles | Zero-issue repos for active codebases is a process gap |

### 3.2 Mid-Term (Sprints 3-5) -- "Coordinate and Connect"

| Priority | Item | Owner | Acceptance Criteria |
|----------|------|-------|-------------------|
| **P1** | **Add `issues-fs scan` command** | Dev | CLI iterates submodules, produces consolidated issue summary |
| **P1** | **Execute first end-to-end Handoff** | Conductor | Task flows Conductor -> Dev -> QA -> DevOps -> Librarian |
| **P1** | **Classify Docs `to_classify/` backlog** | Librarian | All documents moved, archived, or tagged |
| **P2** | **Add cross-repo issue linking** | Dev + Architect | Issues reference issues in other repos |
| **P2** | **Establish sprint planning cadence** | Conductor | Weekly plans with goals, tasks, outcomes |

### 3.3 Long-Term (Sprints 6-10) -- "Scale and Enrich"

| Priority | Item | Owner |
|----------|------|-------|
| **P2** | Build Issues-FS__Lexicon | Architect + Dev |
| **P2** | MGraph-DB cross-repo index | Dev |
| **P2** | GitHub sync service | Dev + DevOps |
| **P3** | Activate remaining roles (AppSec, Cartographer, Historian, Journalist) | Conductor |
| **P3** | Semantic text architecture | Architect + Dev |

---

## 4. Key Risks

| Risk | Severity | Mitigation |
|------|----------|------------|
| **CLI bug blocks all automation** | High | Fix first. Without working `issues-fs list`, Conductor cannot automate scanning. |
| **Schema location ambiguity** | High | Clarify before any cross-module development. |
| **Role coordination stays theoretical** | Medium | Force-execute the first Handoff even if it feels premature. |
| **Docs entropy** | Medium | Classify before adding. Make classification a gate for ingestion. |
| **Single-human bottleneck** | Medium | Conductor should batch escalations with clear recommendations. |

### Dependency Chain

```
issues-fs list fix (P0)
    |-- issues-fs scan command (Mid-term)
    |   |-- Conductor automation
    |   +-- MGraph-DB cross-repo index (Long-term)
    +-- Issue tracking in all repos (P2)
        +-- First end-to-end Handoff (Mid-term)
            |-- Sprint planning cadence
            +-- Role activation (Long-term)
```

---

## 5. Suggested Development Cadence

### Weekly Sprint Structure

| Day | Activity | Owner |
|-----|----------|-------|
| **Monday** | Sprint planning: scan ecosystem, propose goals | Conductor |
| **Mon-Thu** | Execution via Handoff issues | Assigned roles |
| **Thursday** | Mid-sprint check for blockers | Conductor |
| **Friday** | Sprint close: status report, close issues | Conductor + Librarian |

### Version Milestones

| Milestone | Target | Key Deliverables |
|-----------|--------|-----------------|
| **v0.4.6** | Sprint 1-2 | CLI fix, schema assessment, QA repo structure |
| **v0.5.0** | Sprint 3-4 | `issues-fs scan`, first Handoff, docs classified |
| **v0.5.5** | Sprint 5-6 | Cross-repo linking, sprint planning established |
| **v0.6.0** | Sprint 7-10 | Lexicon MVP, MGraph-DB index, GitHub sync prototype |

---

## 6. Immediate Next Actions

1. **Create Blocker issue** in CLI repo for `issues-fs list` bug (assign to Dev, P0)
2. **Create Decision issue** for Architect to assess Service Client Python schemas
3. **Create Task issue** for DevOps to complete QA role repo structure
4. **Create Handoff** from Conductor to Librarian for `to_classify/` classification
5. **Create Task** in Conductor repo to establish weekly sprint cadence

These five actions constitute the first real activation of the role coordination system.

---

*Issues-FS Ecosystem Roadmap v1.0 -- Date: 2026-02-09 -- Role: Conductor -- Next Review: 2026-02-16*
