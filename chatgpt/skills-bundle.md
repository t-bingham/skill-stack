# skill-stack — full skill bundle (ChatGPT)

Upload as a Project / Custom GPT knowledge file. Invoke skills by name per project-instructions.md; open the matching section below and follow it.


---

---
name: arena
description: Run N competing attempts at the same task in parallel, then keep the best â€” or merge the best parts. Use for one hard problem with several plausible approaches. Try new things.
---

# arena

Several takes on one problem. Keep what wins.

- Define the task and the judging criterion up front (speed, clarity, correctness â€” pick).
- Launch competing attempts in parallel, each a real working solution.
- Judge against the criterion with evidence, not taste. Prove each actually works.
- Keep the winner, or merge the strongest parts. Throw the rest away without sentiment.



---

---
name: attack-the-premise
description: After two or more fixes that share an assumption have failed, stop fixing and test the assumption itself. Use when you're stuck in a loop of near-misses.
---

# attack-the-premise

Two failed fixes on one assumption means the assumption is the bug.

- Stop patching. Write down what you've been assuming is true.
- Prove it with evidence â€” print it, log it, check it directly. Don't reason about it; observe it.
- The wrong layer, the wrong file, a cached build, a different process â€” the surprise is usually in the premise, not the code.
- Once the premise breaks, the real fix is obvious.



---

---
name: autonomous-run
description: Playbook to drive a long task to completion without stopping. Set the goal, loop, verify, don't block. Use for work that will take many steps unattended.
---

# autonomous-run (playbook)

1. Write the success criterion as something you can check (`prove-it-works`).
2. Open a todo list; work it top to bottom. Never block on the human (`never-block-on-the-human`).
3. After each unit: verify, commit, continue (`sequence-verifiable-units`).
4. Stuck twice on one assumption? `attack-the-premise`. Hit a true wall? Record state, take the best path, keep moving.
5. Stop only at the criterion or an irreversible/out-of-repo gate. Report the decisions made.



---

---
name: autopilot-full
description: Playbook to take one unit of work all the way to merged, unattended. The default end-to-end run. Use when told to just ship it.
---

# autopilot-full (playbook)

1. Build the change (`feature`/`bug-fix`/`refactoring` as fits).
2. Prove it on the real artifact (`prove-it-works`).
3. Stress-test the diff with a different model (`interrogate`).
4. Open the PR (`file-pr`), babysit to green (`babysit-pr`).
5. Merge (full send). Confirm live. Report the decisions.

Stop before merge only if the task said merge-ready, or at an irreversible/out-of-repo gate.



---

---
name: babysit
description: Playbook to drive a PR or stack to merge-ready â€” resolve conflicts, answer review threads, fix real CI findings. Use when a PR exists and needs to get to green and merged.
---

# babysit (playbook)

1. Rebase/resolve conflicts against the base.
2. Watch CI. On failure, fix the real finding â€” not a retry, not a skip (`fix-root-causes`).
3. Triage review/bot comments: fix the substantive ones, reply to the rest (`leaving-pr-comments`). Ignore noise.
4. Re-prove anything you changed.
5. Merge when green (full send), or stop at merge-ready if the task said so.



---

---
name: babysit-pr
description: Watch a PR through CI and review bots and fix the real findings. Use after opening a PR, to drive it to green. Needs an authenticated gh (or equivalent).
---

# babysit-pr

Sit with the PR until it's green, then send it.

- Poll CI. On red, read the actual failure and fix the root cause â€” not a re-run, not a skip.
- Triage bot/review comments: fix substantive ones, reply to the rest, ignore noise (`leaving-pr-comments`).
- Rebase on conflicts; re-prove anything you touched.
- Merge when green (full send), or hold at merge-ready if the task said so.



---

---
name: blast-radius
description: Find what else a change could break, backed by running code â€” not a guess. Use before a change to shared or load-bearing code.
---

# blast-radius

Before you touch it, find everything that leans on it.

- Find all callers and dependents â€” search, don't assume. Include dynamic/indirect uses.
- For each, decide: unaffected, needs updating, or needs testing.
- Confirm the risky ones against the running system, don't reason in the abstract.
- Output: the list, grouped by risk. Now the change is informed, not blind.



---

---
name: boundary-discipline
description: Guard at the edges of the system; keep the core pure. Validation, IO, and side effects live at boundaries, not threaded through business logic. Use when designing modules or untangling IO-soaked code.
---

# boundary-discipline

Dirty at the edges, pure in the middle.

- Do validation, auth, IO, and serialization at the boundary. The core takes clean types and returns values.
- Business logic should be testable with no network, DB, clock, or filesystem.
- Inject side-effecting dependencies; don't reach for globals from the core.
- A function deep in the core doing IO is a smell â€” push it out.



---

---
name: bug-fix
description: Playbook for broken behavior. Reproduce, root-cause, fix, prove. Use for any defect.
---

# bug-fix (playbook)

1. Reproduce. Capture the failing evidence (input â†’ wrong output). No repro, no fix.
2. Root-cause: trace to the first place state went wrong (`fix-root-causes`). If fixes keep failing, `attack-the-premise`.
3. Fix there, smallest change (`laziness-protocol`).
4. Prove the same path now passes (`prove-it-works`). Add a behavior test if it pays (`test-behavior-not-implementation`).
5. Send it (`sendmode` defaults).



---

---
name: build-the-lever
description: When a task is repetitive or large, build a tool â€” script, codemod, generator â€” instead of grinding by hand. Use when you're about to do the same edit many times.
---

# build-the-lever

Don't do by hand what a tool can do a hundred times.

- Editing the same pattern across many files? Write the codemod.
- Checking the same thing repeatedly? Write the script and run it.
- The lever is reusable, reviewable, and doesn't get bored or miss one.
- Rule of thumb: if the manual pass takes longer than building the tool, build the tool.



---

---
name: correct
description: Mine history for a repeated mistake and fix it at the highest level that works â€” ideally so it can't recur. Use when you notice the same error keeps happening.
---

# correct

Same mistake twice is a process bug, not a typo.

- Find the pattern: where and how often it recurs.
- Fix every instance at once â€” build the lever if there are many (`build-the-lever`).
- Then raise the fix: a lint, test, type, or CI check so it can't come back (`encode-lessons`).
- Lowest-level fix clears today; highest-level fix clears forever. Aim high.



---

---
name: council
description: Get review from several models across providers and loop until they converge. Use for high-stakes changes where one reviewer isn't enough. Heavier than interrogate.
---

# council

Several independent reviewers, loop to agreement.

- Send the change to 2â€“3 models from different providers. Independence is the point â€” don't let them see each other first.
- Collect findings; keep only what's reproducible (`interrogate` discipline).
- Fix, then re-review. Loop until they converge with nothing substantive left.
- Reserve for high-stakes diffs â€” it's expensive. Most changes only need `interrogate`.



---

---
name: encode-lessons
description: Turn a lesson learned into a lint, test, type, or script â€” not a note nobody reads. Make the mistake impossible to repeat. Use after a bug or a review catch that could recur.
---

# encode-lessons

A rule in your head is forgotten. A rule in the build is enforced.

- Just fixed a recurring mistake? Encode it: a lint rule, a test, a type that forbids it, a CI check.
- Prefer the mechanism that fails loudly and early over documentation.
- If it can't be automated, put it in `AGENTS.md`/`CLAUDE.md` where the agent reads it â€” not a buried comment.
- The goal: the next person (or agent) can't make the same mistake without the build complaining.



---

---
name: experience-first
description: Weigh decisions by the user's experience, not implementation convenience. The felt result wins over what's easy to build. Use on any user-facing change.
---

# experience-first

The user feels the outcome, not your architecture.

- Start from the experience you want, work back to the code â€” not the other way.
- Latency, clarity, and the error case are the product. Don't ship a fast path with a broken failure path.
- "Harder to build" is not a reason to degrade it. Find another way.
- Sweat the default, the empty state, and the first run â€” that's what people actually hit.



---

---
name: feature
description: Playbook for new or changed behavior. Model the data, build the thinnest working slice, prove it, expand. Use for any feature work.
---

# feature (playbook)

1. Name the behavior and the data shape it needs (`foundational-thinking`, `model-the-domain`).
2. Design from the user's experience back (`experience-first`).
3. Build the thinnest end-to-end slice that runs. Prove it works on the real artifact.
4. Expand to the full behavior in verifiable units (`sequence-verifiable-units`).
5. Stress-test the diff (`interrogate`), then send it.



---

---
name: file-pr
description: Open a short PR that leads with the problem, not an inventory of changes. Use whenever you open a pull request.
---

# file-pr

Lead with why. The diff speaks for the what.

- First line: the problem this solves or the behavior it adds. One sentence.
- Then the approach, briefly â€” and any decision a reviewer would question.
- Skip the file-by-file list; the diff shows it. Link the issue if there is one.
- Keep it short enough to read in 30 seconds. Format comments cleanly (`leaving-pr-comments`).



---

---
name: fix-root-causes
description: Fix the first place the system went wrong, not the symptom downstream. Trace back before patching. Use on every bug.
---

# fix-root-causes

Patch the symptom and it comes back wearing a hat.

- Trace to the first point where state or data went wrong. Fix it there.
- A guard that papers over a bad value is a bandage â€” find who produced the bad value.
- If you must patch downstream for now, say so and leave the root cause named, not hidden.
- One real fix removes a class of bugs; ten symptom patches add ten code paths.



---

---
name: foundational-thinking
description: Choose the core types and data structures before writing logic. Get the shape right and the code falls out. Use at the start of any feature or redesign.
---

# foundational-thinking

Data structures first. Logic is downstream of them.

- Name the core entities and their shapes before any function.
- Pick the representation that makes the common operation trivial and the illegal state impossible.
- If the logic is getting tangled, the data model is wrong â€” fix that, not the logic.
- Sketch the types, check they compose, then build.



---

---
name: full-send
description: Take a change from working tree to merged in one unbroken run â€” prove, review, file, babysit, merge. The default autonomy level. Use when told to ship it end to end.
---

# full-send

All the way to merged, no stops.

1. Prove it works on the real artifact (`prove-it-works`).
2. Stress-test the diff (`interrogate`).
3. File the PR (`file-pr`).
4. Babysit to green (`babysit-pr`).
5. Merge. Confirm live. Report decisions made.

Stop only at an irreversible/out-of-repo gate, or if the task asked for merge-ready instead of merged.



---

---
name: guard-the-context-window
description: Route bulk work (wide searches, log trawls, file dumps) to subagents and keep only the summary in the main thread. Protect the main context for decisions. Use on any task with heavy reading or fan-out.
---

# guard-the-context-window

The main thread is for deciding. Send the grunt work elsewhere.

- Wide searches, large-file reads, log/trace trawls â†’ a subagent that returns the conclusion, not the dump.
- Independent slices â†’ parallel workers (see `swarm`), each reporting a summary.
- Keep the main context holding the plan and the findings, not raw output.
- Ask for the answer, not the material to read yourself.



---

---
name: how
description: Walk through how a subsystem actually works, from the running code. Use to understand a mechanism before changing it.
---

# how

Explain the mechanism from the code, not the docs.

- Trace the real path end to end: entry â†’ the work â†’ the result.
- Name the key types and where state lives (`model-the-domain` lens).
- Confirm against the running system where you can (`prove-it-works`).
- Output: the walkthrough with file:line anchors. No changes.



---

---
name: interrogate
description: Have a different model try to break your diff; keep only findings proven by running code. Adversarial review on every non-trivial change. Use before sending anything that matters.
---

# interrogate

Build with one mind, break with another.

- Hand the diff to a different model with one job: find what's wrong.
- Demand a repro for each finding â€” run it. Keep only what's proven; discard speculation.
- Fix the real findings at the root (`fix-root-causes`).
- A clean interrogation is your green light to send. A noisy one that proves nothing is noise.



---

---
name: investigation
description: Playbook for read-only questions about how or why code works. Answer from the running system and the source, not guesses. Use when the task is to understand, not change.
---

# investigation (playbook)

1. State the exact question in one line.
2. Find the real code path â€” search, don't assume. Route wide reads to a subagent (`guard-the-context-window`).
3. Confirm against the running system where you can: log it, run it, read the actual output.
4. Answer with evidence â€” file:line and observed behavior. No change, no PR.



---

---
name: kickoff
description: Start a new project. Choose the tech stack and shape from what the project needs, not habit. Decide fast, keep it reversible, start building. Use at project zero, before any stack is assumed.
---

# kickoff

The stack is a choice made now, for this project â€” not a default carried in.

## Decide
- State the real constraints, one line each: users, scale, offline?, data shape, deadline, who maintains it.
- Pick the stack that serves those, not the one you know best. Bias to what ships fastest and stays changeable.
- Boring, proven tech for the core; spend the novelty budget on the one or two things that are the point.
- Record the choices and the why in the project's `AGENTS.md` / `CLAUDE.md`. One paragraph.

## Then
- Scaffold the thinnest end-to-end slice that runs. Prove it works. Ship from there.
- Don't gold-plate setup. Reversible beats perfect â€” you'll break and replace parts.



---

---
name: laziness-protocol
description: Bias toward deletion and the smallest change that works. Before adding code, ask what can be removed. Use on every feature, fix, or refactor.
---

# laziness-protocol

The best code is no code. The second best is less.

- Default to the smallest change. A big diff needs a reason.
- Before writing, look for what to delete. Dead branches, unused options, redundant layers.
- Don't add a case for a problem you don't have yet.
- Reuse before you build. Copy-paste twice is fine; the third time, extract.



---

---
name: leaving-pr-comments
description: Format comments an agent posts on a PR on your behalf. Clear, scoped, actionable. Used automatically by file-pr, babysit-pr, modernize, and takeover.
---

# leaving-pr-comments

An agent is posting as you. Make the comments worth reading.

- One point per comment, anchored to the line it's about.
- Say what and why, and the suggested change. No vague "consider refactoring."
- Mark severity honestly: blocking vs nit. Don't dress a nit as a blocker.
- Skip praise-noise and restating the diff. If there's nothing substantive, post nothing.
- Plain, direct voice â€” no hedging, no filler.



---

---
name: make-operations-idempotent
description: Design operations to converge to the same end state no matter how many times they run or where a partial run stopped. Use for retries, sync, migrations, and anything that can run twice.
---

# make-operations-idempotent

Running it twice should equal running it once.

- Key writes by identity so a retry updates instead of duplicating.
- Make each step check-then-act: skip what's already done, finish what isn't.
- A half-finished run must be safe to re-run from the top.
- Prefer "set to X" over "increment" wherever you can't guarantee exactly-once.



---

---
name: minimize-reader-load
description: Cut the layers and hidden state a reader must hold to follow the code. Optimize for the next person reading it cold. Use when writing or reviewing anything non-trivial.
---

# minimize-reader-load

Code is read far more than written. Spend the effort there.

- Keep related logic together; don't scatter one decision across files.
- No hidden state. What affects behavior should be visible at the call site.
- Name for what it does, not how. Delete comments that restate the code; keep the ones that explain why.
- Fewer indirections. Each hop the reader follows is a cost.



---

---
name: model-the-domain
description: Encode the domain in types and structures, not in scattered conditionals. Make the code mirror the real problem. Use when logic is drifting into special cases and flags.
---

# model-the-domain

If the domain has three kinds of thing, the code should too.

- Turn clusters of booleans and string flags into named states/variants.
- A branch that keeps reappearing is a missing type â€” introduce it.
- The rules of the domain belong in the structure, so invalid combinations can't be built.
- When the model is right, new requirements slot in; when it fights you, remodel.



---

---
name: modernize
description: Rebase an old PR/branch onto current main and decide whether it should still exist. Use for stale work that may be outdated or already solved.
---

# modernize

Old branches rot. Check before reviving.

1. Rebase onto current main. See what conflicts and why.
2. Ask the real question: is this still needed, or did the world move past it? Kill it if obsolete â€” don't revive dead work.
3. If it survives, bring it to current conventions (`outcome-oriented-execution`), re-prove it.
4. Then send it (`full-send`).



---

---
name: multi-phase-plan
description: Playbook for work that spans phases or stacked PRs. Sequence the phases, keep each shippable, track state. Use when one change is too big to land at once.
---

# multi-phase-plan (playbook)

1. Break into phases that each land green and add value on their own.
2. Order by dependency; each phase builds on merged work, not a pending branch.
3. For stacked PRs, keep the stack rebased and land bottom-up (`shipping`).
4. Track phase state somewhere durable so the plan survives a restart or handoff.
5. Prove each phase before starting the next.



---

---
name: never-block-on-the-human
description: Meta-principle. Proceed and present verified results instead of pausing to ask. Stop only for irreversible or out-of-repo acts. Replaces "ask first / plan first" â€” a crutch for weaker models.
---

# never-block-on-the-human

Asking permission was for models that couldn't recover. Proceed, verify, show the work.

## Do
- Make the call and move. Two readings? Pick the stronger, name it in one line, proceed.
- Resolve ambiguity by reading and running code, not by asking.
- Present finished, verified work. Put decisions in the summary â€” cheap to review, trivial to revert.

## Stop only when hard to undo or out-of-repo
Force-push a shared branch Â· push to a remote you don't own Â· delete user/prod data Â· prod deploy Â· spend money Â· reach a human outside the session.

## Never
- "Should I proceed?" â€” just do it.
- A plan-approval gate before work you can do, then verify.
- Asking a preference you can infer from the code or `AGENTS.md`.



---

---
name: opening-a-pr
description: Playbook to open a ready PR from ordered commits. Invoked at the end of other playbooks. Use when the work is green and needs a PR.
---

# opening-a-pr (playbook)

1. Confirm the branch is green and commits are clean, one logical change each (`sequence-verifiable-units`).
2. Write the PR problem-first: what was broken/needed and why, then what changed (`file-pr`).
3. Keep it short. Lead with the problem, not an inventory of the diff.
4. Open it, then babysit (`babysit-pr`).



---

---
name: orchestrate
description: Playbook for a multi-day or multi-stream effort run by one coordinator with subagent fleets. Plan the streams, delegate, integrate. Use for work too big for one linear pass.
---

# orchestrate (playbook)

1. Split the work into independent streams with clear interfaces between them.
2. One coordinator holds the plan and the integration points; it doesn't do the grunt work.
3. Delegate each stream to a worker (`swarm` for parallel slices); each returns a summary, not a dump (`guard-the-context-window`).
4. Integrate as streams land; keep the main build green throughout.
5. Track state so the effort survives a restart (`multi-phase-plan`).



---

---
name: outcome-oriented-execution
description: In migrations and refactors, converge on the target design directly â€” no throwaway compatibility shims. Change the callers, then delete the old thing. Use for any migration or large change.
---

# outcome-oriented-execution

Aim at the end state. Don't build scaffolding you'll tear down.

- Decide the target shape, then move everything to it. No parallel old/new paths left standing.
- Migrate callers, then delete the legacy API in the same change â€” don't leave a compat layer "for safety."
- One real cutover beats a long limbo of both worlds.
- If the change is too big for one cut, sequence it (see `sequence-verifiable-units`) â€” but each step still lands on the target, not a shim.



---

---
name: perf
description: Playbook for measured slowness. Measure, find the real cost, fix, re-measure against baseline. Use when something is slow â€” never optimize on a hunch.
---

# perf (playbook)

1. Measure first. Get a baseline number on the real workload. No number, no work.
2. Profile to the actual hot path. The bottleneck is rarely where you'd guess.
3. Fix the dominant cost. Ignore the rest until it dominates.
4. Re-measure vs baseline. Rule out measurement artifacts before trusting the win (warm cache, noise, wrong input).
5. Keep the benchmark so the win can't silently regress.



---

---
name: prototype
description: Playbook for a throwaway sketch to settle a design or empirical question. Fast and dirty, one question, then delete. Use when you need to learn something, not ship it.
---

# prototype (playbook)

1. Write the one question it must answer. That's the only success criterion.
2. Build the fastest thing that answers it. Skip tests, error handling, polish â€” it's throwaway.
3. Get the answer. Record it.
4. Delete the prototype, or mark it clearly as throwaway. Don't let it become the product.
5. Start the real build from the answer (`feature` / `kickoff`).



---

---
name: prove-it-works
description: Done = runtime evidence against the real artifact, not "the diff looks right." The bar for every task. Tests earn their place where they pay; not a ritual.
---

# prove-it-works

Not done until you've watched it work on the real thing.

## Bar
- Run the real artifact: start it, hit the endpoint, drive the UI, replay the broken input.
- Observe user-visible behavior, not a proxy. Assert behavior, not implementation.
- Bug: reproduce first (capture the failing evidence), then show the path passes.
- Perf: measure vs baseline; rule out measurement artifacts before trusting the number.

## Tests
- Write one when it pays: load-bearing, easy to regress, cheap to assert.
- One behavior test beats three implementation tests.



---

---
name: refactoring
description: Playbook for behavior-preserving structural change. Pin behavior with tests, change shape, prove nothing moved. Use when restructuring without changing what the code does.
---

# refactoring (playbook)

1. Pin current behavior: ensure tests cover it, or add behavior tests first (`test-behavior-not-implementation`).
2. Subtract before adding (`subtract-before-you-add`). Delete what the new shape makes dead.
3. Change structure in small units; green after each (`sequence-verifiable-units`).
4. Converge on the target shape â€” no compat shims left (`outcome-oriented-execution`).
5. Prove behavior is identical. If a test changed, you changed behavior â€” stop.



---

---
name: reflect
description: After a long or hard task, capture the recipe that worked as a skill edit â€” so next time is faster. Use at the end of work that taught you a repeatable approach.
---

# reflect

A task you solved once should be cheaper the next time.

- Name the approach that actually worked, stripped of the dead ends.
- If it's reusable, write or edit a skill to encode it (`encode-lessons`).
- If it's a rule, put it where the agent reads it (`AGENTS.md`), not a comment.
- Keep it short â€” the recipe, not the diary.



---

---
name: sendmode
description: Entry point for any non-trivial task. Routes to a playbook and sets the operating defaults â€” go deep, parallelise, prove it against the real artifact, carry it to merged. Use at the start of anything bigger than a one-line edit.
---

# sendmode

Entry skill. Capable model, trusted operator. *Send* = all the way, no hanging.

## Defaults (override only if the task says so)

- **Full send.** Code â†’ verify â†’ PR â†’ merge, no approval stops. Confirm only irreversible / out-of-repo acts: force-push a shared branch, push to a remote you don't own, destructive ops on non-local data, deleting user data, prod deploys, spending money.
- **Fearless parallelism.** Independent slices â†’ `swarm`. Competing approaches â†’ `arena`. Every non-trivial diff â†’ `interrogate`. Keep bulk work off-thread â†’ `guard-the-context-window`.
- **Prove it works.** Runtime evidence on the real artifact â†’ `prove-it-works`.
- **Never block.** Proceed and present â†’ `never-block-on-the-human`.

## Route

| Task | Playbook |
|---|---|
| how / why code works | `investigation` |
| broken behavior | `bug-fix` |
| measured slowness | `perf` |
| new / changed behavior | `feature` |
| behavior-preserving cleanup | `refactoring` |
| settle a design question | `prototype` |
| pixel-exact UI | `visual-parity` |
| drive a PR to merged | `autopilot-full` |
| resume another agent's work | `session-pickup` |
| multi-day effort | `orchestrate` |
| new project, no stack yet | `kickoff` |

Load the principle skills the playbook names.



---

---
name: sequence-verifiable-units
description: Break work into small steps that can each be verified and committed on their own. Every commit leaves the tree green. Use on any task bigger than a single change.
---

# sequence-verifiable-units

Small, provable steps. Never a pile of half-done.

- Each step compiles, passes, and could ship on its own.
- One logical change per commit. If the message needs "and," split it.
- Order so dependencies land first; nothing depends on a later step.
- Verify each unit before the next (see `prove-it-works`). A broken middle step is a broken build.



---

---
name: session-pickup
description: Playbook to resume or take over another agent's in-flight work. Rebuild context from the artifacts, then continue. Use when inheriting a branch, PR, or paused task.
---

# session-pickup (playbook)

1. Rebuild context from what exists: the branch diff, commits, PR thread, todo list, notes. Not from memory.
2. Establish the current state â€” what's done, what's green, what's broken. Run it (`prove-it-works`).
3. Find where it was heading; confirm that's still right.
4. Continue from there in verifiable units. Keep the original credit/authorship.



---

---
name: setup
description: Configure the stack for a project or machine â€” which models fill which roles, and any project rules. Use once per project/machine, or when changing model roles.
---

# setup

Pick the roles once; write them where the agent reads them.

- Assign models to roles: builder (deep work), reviewer (interrogate/council), cheap worker (swarm slices, bulk reads).
- Record them in the project's `AGENTS.md`/`CLAUDE.md`, not in a skill file â€” so skill updates don't overwrite your config.
- Note any project rule the agent must always follow there too.
- Keep it one short block. Revisit when a better model lands (try new things).



---

---
name: shipping
description: Playbook to land a green change. Verify, land bottom-up, confirm it's live. Use when work is done and needs to go out.
---

# shipping (playbook)

1. Confirm green: everything proven on the real artifact (`prove-it-works`), CI clean.
2. For a stack of changes, land bottom-up â€” each must be green before the one above it.
3. Open the PR problem-first (`file-pr`); babysit through CI and bots (`babysit-pr`); merge (full send).
4. Confirm it's actually live where it matters, not just merged.



---

---
name: subtract-before-you-add
description: Remove dead weight before building on top of it. Clear the ground first so the new work lands clean. Use before extending a messy or crowded area of code.
---

# subtract-before-you-add

Don't build on a pile. Clear it first.

- Delete what the new work makes obsolete â€” in the same change, not "later."
- Collapse near-duplicate paths into one before adding a third.
- Remove the abstraction that only ever had one caller.
- If subtracting first makes the add trivial, that's the signal you're on the right path.



---

---
name: swarm
description: Run N parallel workers on different independent slices of one task, then aggregate. Use when work splits cleanly into pieces that don't depend on each other.
---

# swarm

Many workers, different slices, one report.

- Split the task into slices with no shared state and clear interfaces.
- Launch a worker per slice in parallel. Each verifies its own slice (`prove-it-works`) and returns a summary, not a dump (`guard-the-context-window`).
- Integrate the results; resolve interface mismatches at the seams.
- If slices turn out to depend on each other, it wasn't a swarm â€” re-split or sequence it.



---

---
name: takeover
description: Finish someone else's PR, branch, or agent thread and keep their credit. Use when inheriting unfinished work that needs to land.
---

# takeover

Pick up their work, land it, leave the credit theirs.

1. Rebuild context from the branch, commits, and PR thread (`session-pickup`).
2. Establish what's done and what's broken; run it (`prove-it-works`).
3. Finish in verifiable units; modernize stale parts if needed (`modernize`).
4. Preserve original authorship â€” add yourself as co-author, don't overwrite them.
5. Send it (`full-send`).



---

---
name: tdd
description: Failing test first, then the code to pass it. Use when the behavior is well-specified and you want the test to drive the design. Opt-in â€” the default bar is prove-it-works, not test-first.
---

# tdd

Red, green, done. Use it where it pays.

1. Write the test for the behavior. Watch it fail for the right reason.
2. Write the least code to pass it (`laziness-protocol`).
3. Refactor with the test holding you (`refactoring`).
- Assert behavior, not implementation (`test-behavior-not-implementation`).
- Reach for this when the spec is clear. For exploratory or UI work, `prototype` then `prove-it-works` instead â€” don't force test-first.



---

---
name: teach
description: Build one clear explanation of a subsystem â€” how it works plus why it's that way â€” with a diagram. Use when you need to really understand or hand off an area.
---

# teach

How + why, fused into one explanation someone could learn from.

- Run `how` (mechanism) and `why` (reasoning); combine, don't staple.
- Draw the shape â€” a diagram of the parts and the flow between them.
- Lead with the mental model, then the detail. Cut what doesn't serve understanding (`minimize-reader-load`).
- Ground every claim in the code or history.



---

---
name: technical-writing
description: A layered standard for docs, RFCs, READMEs, PR descriptions, and commit messages. Most important thing first, detail below. Use when writing any technical document.
---

# technical-writing

Layer it: the reader stops when they've got what they need.

- Top: the one thing â€” what this is / what changed / what to do. One or two sentences.
- Next: the shape â€” the few things that matter, in order of importance.
- Bottom: detail and edge cases, for whoever reads that far.
- Concrete over abstract; example over description. Then `unslop` it.
- Commit messages: imperative subject, why in the body if it's not obvious.



---

---
name: test-behavior-not-implementation
description: Assert user-observable behavior, not internal structure. Tests should survive a refactor. Use when writing any test.
---

# test-behavior-not-implementation

Test what it does, not how it does it.

- Assert on inputs and outputs the user or caller sees â€” not private methods, call counts, or internal state.
- A refactor that keeps behavior should not break a single test.
- Mock only true boundaries (network, clock). Don't mock the thing under test.
- If a test knows the implementation, it's a change-detector, not a safety net â€” rewrite it.



---

---
name: type-system-discipline
description: Make illegal states unrepresentable and parse input at the boundary into trusted types. The t3 "end-to-end types" ethos, stack-independent. Use wherever untrusted data enters or invalid states are possible.
---

# type-system-discipline

Push correctness into the type system so the compiler does the checking.

- Make illegal states unrepresentable. If two fields can't both be set, don't let them.
- Parse, don't validate: at the boundary, turn raw input into a trusted type once. Inside, assume it's valid.
- No escape hatches (`any`, casts, ignores) past the boundary without a one-line reason.
- Let types flow end to end â€” one source of truth for a shape, derived everywhere else, never re-declared.



---

---
name: unslop
description: Strip AI tells and filler from prose â€” docs, PR text, commit messages, comments. Use before anything you write goes out.
---

# unslop

Cut the tells. Say it plain.

- Delete filler: "it's important to note," "in order to," "simply," "robust," "seamless," "leverage," "delve."
- No hedging stacks ("might possibly help to consider"). State it.
- Kill the intro and the recap. Lead with the point.
- Vary nothing for the sake of it; shorter wins. Read it aloud â€” if it sounds like a brochure, rewrite.



---

---
name: visual-parity
description: Playbook for pixel-exact UI equivalence between two implementations or against a design. Compare rendered output directly, don't eyeball. Use when a UI must match a reference.
---

# visual-parity (playbook)

1. Get both rendered: the reference and your version, same viewport and state.
2. Compare directly â€” screenshot diff or overlay, not from memory.
3. Fix the largest visible delta first; re-render; repeat.
4. Check the states that aren't the happy path: hover, empty, error, long content, narrow width.
5. Done when the diff is noise. Prove it with the side-by-side.



---

---
name: why
description: Explain why something was built this way, from commit and PR history. Use before changing code whose reasoning isn't obvious â€” don't undo a decision blind.
---

# why

The code says what. History says why.

- Read the commit that introduced it and the PR around it. Look for the problem it solved.
- Check for a fix-commit lineage â€” what broke before this existed.
- Separate real constraint from accident. Some "why" is just the day it was written.
- Output: the reason, with the commit/PR as evidence. Now you can change it knowingly.



---

---
name: worktree-cleanup
description: Playbook to prune merged or abandoned worktrees and stale branches, safety-gated. Use when the workspace is cluttered with old worktrees/branches.
---

# worktree-cleanup (playbook)

1. List worktrees and branches with their state: merged, abandoned, active.
2. Confirm each candidate is truly done â€” merged upstream or explicitly dead. Never guess.
3. Remove only the confirmed-safe ones. Stop and ask on anything with unmerged work (out-of-repo / hard-to-undo).
4. Leave active and uncertain worktrees untouched. Report what was pruned.

