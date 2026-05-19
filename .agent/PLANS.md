# Codex Execution Plans (ExecPlans)

This document describes the requirements for an execution plan ("ExecPlan"), a design document that a coding agent can follow to deliver a working feature or system change.

Treat the reader as a complete beginner to this repository. They have only the current working tree and the single ExecPlan file you provide. There is no memory of prior plans and no external context.

## How To Use ExecPlans And PLANS.md

When authoring an executable specification, follow this file carefully. If this file is not in your current context, refresh your memory by reading the entire file. Be thorough in reading and re-reading source material so the specification is accurate. When creating a spec, start from the skeleton and flesh it out as you research.

When implementing an ExecPlan, do not prompt the user for "next steps". Proceed to the next milestone. Keep all sections up to date. Add or split entries in the progress list at every stopping point to state the progress made and the next steps. Resolve ambiguities autonomously where the repository context makes the answer clear.

When discussing an ExecPlan, record decisions in a log inside the spec. It should be clear why any change to the specification was made. ExecPlans are living documents, and it should always be possible to restart from only the ExecPlan and the current working tree.

When researching a design with challenging requirements or significant unknowns, use milestones to implement proof-of-concepts or small prototype implementations that validate whether the proposal is feasible. Read relevant source code and include prototype results to guide the full implementation.

## Non-Negotiable Requirements

- Every ExecPlan must be fully self-contained. In its current form, it must contain all knowledge and instructions needed for a novice to succeed.
- Every ExecPlan is a living document. Contributors must revise it as progress is made, discoveries occur, and decisions are finalized. Each revision must remain fully self-contained.
- Every ExecPlan must enable a complete novice to implement the feature end-to-end without prior knowledge of this repository.
- Every ExecPlan must produce demonstrably working behavior, not merely code changes that satisfy a narrow definition.
- Every ExecPlan must define every term of art in plain language, or avoid that term.

Purpose and intent come first. Begin by explaining why the work matters from a user's perspective: what someone can do after this change that they could not do before, and how to see it working.

The agent executing the plan can list files, read files, search, run the project, and run tests. It does not know prior context and cannot infer meaning from earlier conversations. Repeat every assumption you rely on. Do not point to external blogs or documentation as required context. If knowledge is required, embed it in the plan in your own words. If an ExecPlan builds on a prior checked-in ExecPlan, incorporate it by reference. If the prior plan is not checked in, include all relevant context directly.

## Formatting

Each ExecPlan presented in chat must be one single fenced code block labeled `md` that begins and ends with triple backticks. Do not nest additional triple-backtick code fences inside. When commands, transcripts, diffs, or code are needed, present them as indented blocks inside the single fence.

When writing an ExecPlan to a Markdown file where the content of the file is only the ExecPlan, omit the triple backticks.

Use two blank lines after every heading. Use normal Markdown headings with `#`, `##`, and so on. Write in plain prose. Prefer sentences over lists. Avoid checklists, tables, and long enumerations unless brevity would obscure meaning. Checklists are permitted in the `Progress` section, where they are mandatory. Narrative sections should remain prose-first.

## Guidelines

Self-containment and plain language are paramount. If you introduce a phrase that is not ordinary English, define it immediately and explain how it appears in this repository by naming the relevant files or commands.

Avoid common failure modes. Do not rely on undefined jargon. Do not define a feature so narrowly that the resulting code compiles but does nothing meaningful. Do not outsource key decisions to the reader. When ambiguity exists, resolve it in the plan and explain why. Over-explain user-visible effects and keep incidental implementation details as small as possible.

Anchor the plan with observable outcomes. State what the user can do after implementation, the commands to run, and the outputs they should see. Acceptance should be phrased as behavior a human can verify. If a change is internal, explain how its impact can still be demonstrated by tests, logs, CLI output, or a small scenario.

Specify repository context explicitly. Name files with repository-relative paths. Name functions and modules precisely when they matter. Describe where new files should be created. If touching multiple areas, include a short orientation paragraph explaining how the parts fit together.

Be idempotent and safe. Steps should be safe to run multiple times without causing damage or drift. If a step can fail halfway, include how to retry or adapt. If a destructive operation is necessary, spell out backups or safe fallbacks. Prefer additive, testable changes that can be validated as work proceeds.

Validation is not optional. Include instructions to run tests, start the system if applicable, and observe useful behavior. Include expected outputs and error messages so a novice can tell success from failure. State the exact test commands for this project's toolchain and how to interpret the results.

Capture evidence. When steps produce terminal output, diffs, or logs, include concise examples focused on what proves success.

## Milestones

Milestones are narrative, not bureaucracy. Each milestone should describe the scope, what will exist at the end that did not exist before, the commands to run, and the acceptance expected.

Each milestone must be independently verifiable and incrementally implement the overall goal of the ExecPlan.

## Living Plans And Design Decisions

ExecPlans are living documents. As key design decisions are made, update the plan to record both the decision and the thinking behind it. Record all decisions in the `Decision Log` section.

ExecPlans must contain and maintain these sections:

- `Progress`
- `Surprises & Discoveries`
- `Decision Log`
- `Outcomes & Retrospective`

These sections are not optional.

When unexpected behavior, bugs, performance tradeoffs, or CI problems shape the approach, capture those observations in `Surprises & Discoveries` with short evidence snippets.

If the implementation changes direction, document why in `Decision Log` and reflect the implications in `Progress`.

At completion of a major task or the full plan, write an `Outcomes & Retrospective` entry summarizing what was achieved, what remains, and lessons learned.

## Prototyping Milestones And Parallel Implementations

It is acceptable and often useful to include explicit prototyping milestones when they reduce risk for a larger change. Keep prototypes additive and testable. Clearly label the scope as prototyping, describe how to run and observe results, and state the criteria for promoting or discarding the prototype.

Parallel implementations are acceptable when they reduce risk or keep tests passing during a migration. Describe how to validate both paths and how to retire one safely.

## Skeleton Of A Good ExecPlan

Use this skeleton when creating a new ExecPlan.

    # <Short, action-oriented description>

    This ExecPlan is a living document. The sections `Progress`, `Surprises & Discoveries`, `Decision Log`, and `Outcomes & Retrospective` must be kept up to date as work proceeds.

    This plan follows `.agent/PLANS.md` from the repository root.

    ## Purpose / Big Picture

    Explain what someone gains after this change and how they can see it working. State the user-visible behavior you will enable.

    ## Progress

    Use a list with checkboxes to summarize granular steps. Every stopping point must be documented here.

    - [x] (2026-05-19 12:00Z) Example completed step.
    - [ ] Example incomplete step.

    ## Surprises & Discoveries

    Document unexpected behaviors, bugs, optimizations, or insights discovered during implementation. Provide concise evidence.

    - Observation: ...
      Evidence: ...

    ## Decision Log

    Record every decision made while working on the plan in this format:

    - Decision: ...
      Rationale: ...
      Date/Author: ...

    ## Outcomes & Retrospective

    Summarize outcomes, gaps, and lessons learned at major milestones or at completion. Compare the result against the original purpose.

    ## Context And Orientation

    Describe the current state relevant to this task as if the reader knows nothing. Name the key files and modules by repository-relative path. Define any non-obvious term. Do not refer to prior plans unless they are checked in and explicitly referenced.

    ## Plan Of Work

    Describe the sequence of edits and additions in prose. For each edit, name the file and location when that precision matters. Keep the plan concrete and minimal.

    ## Concrete Steps

    State the exact commands to run and where to run them. When a command generates important output, show a short expected transcript.

    ## Validation And Acceptance

    Describe how to exercise the system and what to observe. Phrase acceptance as behavior with specific inputs and outputs. If tests are involved, say which command to run and what result to expect.

    ## Idempotence And Recovery

    Explain which steps can be repeated safely. If a step is risky, provide a safe retry or rollback path. Keep the environment clean after completion.

    ## Artifacts And Notes

    Include the most important transcripts, diffs, or snippets as indented examples. Keep them concise and focused on what proves success.

    ## Interfaces And Dependencies

    Be prescriptive. Name the libraries, modules, services, types, functions, or command interfaces that must exist at the end of the milestone. Explain why they are used.

## Repository-Specific Notes For qa-learning-lab

This repository uses Node.js, Playwright, JavaScript, TypeScript, SQL, Docker, Kubernetes, GitHub Actions, and GitLab CI.

For this project, common validation commands are:

    npm run test:chromium
    npm run test:api -- --project=chromium
    npm run test:ui -- --project=chromium

The project is mirrored to both GitHub and GitLab. Completed work should be pushed to both remotes only when the user approves:

    git push origin main
    git push gitlab main

UI tests should remain stable in CI. Prefer Playwright route mocks over depending on public websites from CI runners. API tests may use public practice APIs when that is the learning goal.

## Revision Notes

- 2026-05-19: Added project-local PLANS.md so future ExecPlans can be created and maintained from checked-in instructions.
