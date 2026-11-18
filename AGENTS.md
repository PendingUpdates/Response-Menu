# Instructions for this repository

## Scope

Response-Menu is documentation-only planning for independent tools. Its owner is the roadmap agent. Maintain the README, roadmap, bounded agent briefs, and handoff documentation. Follow the current user/coordinator assignment; do not change other repositories.

Do not add a toolkit executable, runtime package, shared engine, dispatcher, orchestration runtime, shared installer, submodules, or a mandatory common evidence store. Do not introduce a shared dependency required by BEC, Flapjacks, CrumbTrail, or HashBrown. Optional file-based interchange is a proposal until separately justified and tested.

The intended ownership is:

- BEC agent: `PendingUpdates/BEC`, email/account compromise only.
- M365 audit agent: `PendingUpdates/Flapjacks`, selected organization-wide Microsoft 365 configuration and control posture only.
- Windows triage agent: `PendingUpdates/CrumbTrail`, Windows event triage only.
- Acquisition agent: `PendingUpdates/HashBrown`, disk/RAM acquisition, integrity, and custody only.
- Roadmap agent: `PendingUpdates/Response-Menu`, planning documents only.

Git operations, publication, licensing, and CI changes belong to the coordinator unless explicitly reassigned. Do not make production changes or run endpoint acquisition from a planning task.

## Coordination

Use at most three active worker agents plus one coordinator across the work. Do not spawn subagents or delegate recursively. Do not run polling loops, background model/API processes, or agent daemons. The coordinator explicitly assigns bounded tasks and collects their results.

Read the supplied fact packet and relevant handoff first. Do not broadly inspect another repository, repeat its provider/acquisition research, or rediscover the whole ecosystem. Request a specific missing fact from its owner. Record the answer and its provenance in the handoff, then continue within scope.

Use [docs/agent-handoffs.md](docs/agent-handoffs.md) for completion and blocked-work packets. Keep packets brief. Include exact revisions and test evidence where available; distinguish inherited claims from checks performed by the current owner.

## Planning and validation

Every milestone needs one accountable owner, a responder outcome, deliverables, prerequisites, tests, and a handoff. Each executable tool must own its own code, CLI, dependency declarations, tests, CI, and local fixtures and install without the other repositories.

The earlier combined implementation's 71 passing tests and fixture transfer exercise are historical baseline evidence. Do not claim standalone projects passed until their owners or coordinator provide results. Live RAM driver/device capture and physical-disk acquisition remain untested until documented real lab checks establish otherwise. Hash verification alone does not establish acquisition completeness.

For documentation changes, reread the affected documents in full, check local links and scope/status consistency, and report any unresolved assumptions. Do not run unrelated tool test suites or manufacture passing checks. Use primary official references for new technical recommendations; reuse existing verified references when they suffice.

## Windows shell use

Prefer RTK for supported verbose external commands; use PowerShell cmdlets and unsupported commands normally. Use targeted `rg` searches and bounded reads for orientation, then full relevant text for exact edits and final review. Preserve machine-readable output when it is consumed by a program. If a failed command provides a saved-output path, inspect it before rerunning. Do not infer hook activation from configuration alone.
