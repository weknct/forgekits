---
name: phase-detection
description: Use to determine which SDLC phase a software project is currently in and what the next action should be — invoke when the user asks "what phase am I in?", "what's next?", or needs the project's lifecycle state assessed from its files and status markers.
---

# Skill: Phase Detection

## Purpose
Detect the current phase of a software project within the 9-phase SDLC and recommend the next concrete action. This is the deterministic detection logic behind the Forge Guide orchestrator, usable on its own whenever you need to answer "where are we and what's next?"

## When to Use
- The user asks "what's next?", "what should I do?", or "what phase am I in?"
- At the start of a working session, to orient before recommending work.
- Whenever you need to assess project lifecycle state from the files on disk.

## The 9 Phases

```
0 Setup → 1 Genesis → 2 Discovery → 2b POC (optional) → 3 PRD → 4 Backlog → 5 Sprint Planning → 6 Sprint Execution → 7 Sprint Review → 8 Delivery & Maintenance
```

## Detection Algorithm

Evaluate these conditions top-to-bottom. The **first match wins** — that is the current phase. Always inspect the actual project files and their status markers rather than guessing.

| Order | Phase | Detect when… | Recommend next |
|------|-------|--------------|----------------|
| 1 | **0 Setup** | No progress tracker exists, or project config has no project-specific content | Create folder structure + progress tracker; set project name/status |
| 2 | **1 Genesis** | No genesis document exists (only a template). *If the user has a BRD, intake it and skip toward PRD.* | Capture problem, solution, key features, constraints |
| 3 | **2 Discovery** | Genesis exists; no completed discovery interview (or one marked in-progress) | Run a structured discovery interview |
| 4 | **2b POC** (optional) | Discovery complete, a spike/POC task is flagged, no PRD yet | Timebox a spike to validate the risky assumption; document findings |
| 5 | **3 PRD** | Discovery findings exist; no PRD drafted | Draft the PRD; capture architecture decisions |
| 6 | **4 Backlog** | PRD exists; backlog has no story/epic items | Break PRD into Epics → Features → User Stories with sequence ordering |
| 7 | **5 Sprint Planning** | Backlog has stories; no sprint created | Review backlog health, check Definition of Ready, create + commit a sprint |
| 8 | **6 Sprint Execution** | An active sprint exists | Show sprint status; pick up next story; log bugs; update status |
| 9 | **7 Sprint Review** | All sprint stories Done or carried over | Record velocity; run retrospective; capture actions; return to planning |
| 10 | **8 Delivery & Maintenance** | Multiple sprints complete; product deployed | Triage bugs; plan maintenance; update changelog; stakeholder reports; watch for EOL |

## Sub-States to Check

- **BRD shortcut:** If the user already has a Business Requirements Document, much of Genesis and Discovery can be bypassed — intake the BRD and advance toward PRD.
- **Async discovery in flight:** In Discovery, if interview answers have been returned offline, the next action is to import them; if a batch is outstanding, flag its age.
- **Optional POC:** If no spike/POC task exists, Phase 2b is skipped automatically — go straight from Discovery to PRD.

## Output Format

When invoked, produce:
1. **Current Phase:** the first matching phase, with a one-line reason (which evidence matched).
2. **Completed:** a short list of what's already done.
3. **Next Action:** the single highest-value next step for this phase.
4. **Offer:** ask whether to execute that next step now.
