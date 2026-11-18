# Roadmap

Status snapshot: 2026-11-17, from coordinator-verified public revisions and owner handoffs. Implementation on main, package versions, release tags, exercised checks, and qualification are separate claims. No fixed delivery dates are promised before designated targets, expected facts, and the support matrices are known.

## Status and boundaries

The current public revisions are listed below. No Git tags or GitHub Releases were observed in the coordinator's 2026-11-17 check; code on main does not by itself establish a package release or acceptance of every milestone condition. Each tool keeps its own version sequence. Exact build, test and CI evidence belongs in the [release validation ledger](docs/release-validation.md); the November 16 wheel and native checks below remain historical evidence for their pinned builds.

BEC remains email/account focused. CrumbTrail remains offline/local; remote orchestration is deferred. HashBrown owns acquisition and custody in its own package. Live tenant qualification, exported-EVTX acceptance across supported systems, and actual RAM/physical-disk capture remain open. Offline releases do not close those lab gates.

`BEC` owns per-incident email/account evidence and timelines. `Flapjacks` owns selected organization-wide Microsoft 365 configuration and control-posture checks in PowerShell. `CrumbTrail` owns Windows event triage. `HashBrown` owns disk/RAM acquisition, integrity, and custody. `Response-Menu` owns planning documents. Every executable project must be independently installable and have its own code, CLI, tests, CI, fixtures, and dependency declarations. Flapjacks is not a Python package or a replacement for BEC historical investigation. None may import or require another project at runtime.

Keep functionality within its owner. Email provider clients stay in BEC; Windows event interpretation stays in CrumbTrail; acquisition and binary transfer stay in HashBrown. Future work consumes the relevant owner handoff. There is no shared engine or continuing synchronization of mixed-purpose implementations.

## Current capabilities on public main

Use the [tool workflows](docs/tool-workflows.md) for inputs, outputs, side effects and handoffs. These formerly local-review milestones now have implementations on public main at the revisions below. Publication does not close their remaining acceptance gates. Owner packets must identify the tested revision, inputs, commands, results and limits before the [ledger](docs/release-validation.md) records a stronger validation claim.

| Milestone | Single owner / public revision | Responder outcome / deliverable | Prerequisites, remaining tests and handoff |
| --- | --- | --- | --- |
| E5: current mailbox state beside historical activity | BEC agent / [2d9f59d](https://github.com/PendingUpdates/BEC/tree/2d9f59dbe388d54e5243b1dc004e9ede9d0705f7) | Optional offline mailbox snapshot v1 import with source pointers and byte hash; a separate incident companion, not an automatic input to ordinary timelines. Keep event time distinct from snapshot time | Exact tenant/mailbox binding and mismatch, tamper and denied/partial coverage evidence; shared synthetic fixture and both peer revisions before any interoperability claim. Owner sends commands/results to coordinator; live E2 stays open |
| F1: configuration audit and snapshot export | M365 audit agent / [5d7904c](https://github.com/PendingUpdates/Flapjacks/tree/5d7904c521113d53a9f8d3a60e0f84574f34e1d4) | Public Audit and Pull Logs, selected organization-wide M365 posture checks, stable control IDs and optional snapshot export | Owner supplies exact-revision PowerShell results and workload/permission limits; fixture acceptance by BEC is required before compatibility claims. Keep unmapped, prototype and unassessed controls distinct; live workload qualification remains separate |
| W3: offline event correctness | Windows triage agent / [d1dcb1f](https://github.com/PendingUpdates/CrumbTrail/tree/d1dcb1fc559a6baae5a3d91e8a45bdf5bcbee9d1) | Offline/local boundary-aware findings, session association and explicit event inputs | Owner hands off exact-revision ID-reuse, logoff/startup, ambiguous-role and source-preservation results, plus remaining resource/native acceptance gaps. Broader W2 stays open; no remote orchestration |
| A5: generic existing-evidence registration | Acquisition agent / [5eb2c19](https://github.com/PendingUpdates/HashBrown/tree/5eb2c195f9937199e1152e4a6e02ed5b846deb82) | Public optional custody registration and verification of existing artifacts, without acquiring them | Owner supplies scope/original-vs-derived metadata and tamper, partial, unsafe-path and interrupted-handoff evidence; distinguish local case writes from detached checks. Physical-disk/RAM A2 stays open |
| R1: workflow menu and evidence ledger | Roadmap agent / [99cd089](https://github.com/PendingUpdates/Response-Menu/tree/99cd08945122c4f8f4b2ed4258ea010db4f42705) | Public Flapjacks lineup, bounded runbooks, optional contract and separated validation statuses | Documentation updates need full reread, local Markdown links, TOML and diff checks, then a coordinator handoff with owner-provided claims and exact revisions. New local edits are not published by this status table |

This roadmap does not authorize live targets, security/configuration changes, production integration, publishing or repository renames. Live read permission and platform qualification require separate designated scope. No launcher or shared runtime is introduced.

## Historical published baseline: 2026-11-16

These version numbers and acceptance results describe the pinned builds in the [November 16 ledger](docs/release-validation.md#recorded-published-baseline), not every later main revision. The bounded changes provide useful work without live credentials or a capture VM. Each has one owner and uses only its own repository, code, and evidence format.

| Milestone | Single owner | Implemented responder outcome | Evidence and boundary |
| --- | --- | --- | --- |
| E4: search saved email evidence | BEC agent | BEC 0.8.0: read-only, evidence-linked indicator search in a saved tenant-bound case | Reviewed/published; fresh base-wheel smoke and full suite passed. Search coverage and integrity limitations remain distinct from live-provider qualification |
| A4: portable evidence handoff | Acquisition agent | HashBrown 0.3.0: freshly hash selected committed images into a detached handoff, then verify after relocation without the source case | Reviewed/published; fresh-wheel suite/smoke passed with recorded Windows platform skips. Partial status and custody limits remain explicit; no automatic image copying or capture qualification |
| W2 precision subgate | Windows triage agent | CrumbTrail 0.3.0: exact BinXML SystemTime integer ticks, a registered sidecar, and 100 ns window/order/session behavior | Published; independent wheel/native checks passed. System 1/1 and Security 181/181 have 0 ns differences. All eight former failures closed with the 1,000 ns threshold unchanged; real single-tick/adjacent-window checks passed |

CrumbTrail's exact extraction uses its pinned optional `python-evtx==0.8.1` extra. Native raw results remain immutable; the registered sidecar carries exact values. Portable validation needs neither the original source file nor that parser. Source and collector copies remained unchanged in exercised checks. This is CrumbTrail's own format and dependency, not a toolkit-wide schema or runtime.

The [November 16 offline iteration record](docs/offline-evidence-iteration.md) separates implemented behavior, exercised results, and release evidence for that baseline. Earlier comparison/session/preflight work remains in the [offline release history](docs/current-iteration.md); the [0.2.1 lab history](docs/lab-iteration.md) preserves the former precision failure with an explicit closure pointer.

## Remaining qualification priorities

Offline features do not need the absent E2/A2 resources and do not satisfy those live gates. Keep prepared lab helpers available without substituting an ambient account, host, device, or destination for a designated target.

| Gate | Single owner | Current state | Remaining exit evidence |
| --- | --- | --- | --- |
| E2: live email qualification | BEC agent | **NOT EXECUTED**; no designated tenant/account/window/native expected-event inputs | Exercise designated scope and compare actual permissions, retention, pagination, source coverage, and collected evidence with expected facts |
| W2: Windows/Sysmon and responder acceptance | Windows triage agent | Precision subgate passed on the exercised System/Security files; broader gate remains open | Declared OS/channel matrix, telemetry/session behavior, throughput, and responder signoff. Do not generalize a two-source precision result to every event source |
| A2: native disk/RAM qualification | Acquisition agent | Physical capture **NOT EXECUTED**; qualification `not_granted` | Designated VM/device/destination, actual capture, and human independent-reader/content/extent validation, with read errors, compatibility, interruption, and throughput documented |

Hashes verify bytes against a recorded reference; detached handoff and preserved custody metadata do not prove acquisition completeness or authenticity. E2/A2 designation requests are unchanged. Each project releases independently; the coordinator owns Git, CI, publication, and the authoritative ledger. No shared package, schema, installer, or evidence store is introduced.

## Responder outcomes first

BEC should help explain a specific email/account incident using available provider evidence and a reviewable timeline/report. Flapjacks should help an operator assess selected organization-wide M365 controls and see unsupported or unassessed areas; configuration posture alone does not establish what happened in an incident. CrumbTrail should help a responder understand observable Windows events, the affected host/account context, and what telemetry is missing. HashBrown should make it clear what was requested, what was obtained, whether transferred bytes verified, and what custody actions occurred.

Preserve distinctions between observation, hypothesis, and analyst confirmation. An empty result is not evidence of an uncompromised system when telemetry is absent, inaccessible, expired, or unsupported. Acquisition completeness, transfer integrity, and parser success are different claims.

## Later projects require a value gate

Memory analysis and disk/file timeline parsing belong in later **separate repositories**, each with its own owner and runtime. Before starting either, require a concrete responder question, a usable reference image with known facts, a bounded compatibility matrix, a prototype result that answers the question, and a maintainer able to support the dependency stack.

Volatility 3 is a candidate for memory analysis; its documentation separates analysis from acquisition, and Windows symbol resolution may require prepared offline dependencies. Plaso is a candidate for disk/file timelines; its tools extract and post-process events using their own storage format. These are reuse candidates, not integrations already implemented or requirements imposed on BEC, CrumbTrail, or HashBrown. [Volatility acquisition boundary](https://volatility3.readthedocs.io/en/latest/getting-started-linux-tutorial.html), [symbol handling](https://volatility3.readthedocs.io/en/latest/symbol-tables.html), [Plaso user guide](https://plaso.readthedocs.io/en/latest/sources/user/Users-Guide.html)

Optional file interchange can be proposed only when a real consumer exists. Preserve original evidence, source IDs, timestamps, hashes, and producer versions where applicable, but let each tool keep its own format and standalone use. Any proposed mapping needs its own small examples and compatibility tests. Do not create a mandatory shared schema library, database, case service, or evidence store.

## Capacity and acceptance language

Allow at most three active worker agents plus the coordinator. No recursive delegation. Each worker stays inside its assigned repository, consumes the supplied fact packet, and requests a targeted handoff instead of repeating whole-repository or ecosystem discovery. Start one bulk acquisition or analysis experiment per lab host/worker until measurements justify a different limit. Use repository-local fixtures and explicit storage/time budgets.

Use these labels consistently: **planned** (design only), **implemented** (code exists), **fixture validated** (bounded deterministic tests passed), **lab qualified** (declared live configurations exercised), and **field evaluated** (a specific build reviewed during an authorized real investigation). Record separate labels for separate capabilities. Mock tests never automatically advance a feature to lab qualified.

Fleet management, automated containment, ransomware execution, decryptors, a central incident-response platform, broad connectors, and automatic AI conclusions are outside this roadmap. Background polling, model/API loops, and unattended agent daemons are also excluded.
