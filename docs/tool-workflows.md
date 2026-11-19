# Response Menu workflows

**Current offline workflows, reviewed 2026-11-17.** The tool-owned instructions below pin the reviewed public main revisions. Availability on main is separate from release tags, live provider or native acquisition qualification, and producer/consumer compatibility. Use the [release ledger](release-validation.md) for recorded baselines and acceptance evidence, keeping historical entries tied to their exact revisions. Each tool owns its code, CLI, dependencies, evidence and installation; none requires a sibling checkout. These runbooks select work and handoffs, not executable menu commands or permission to collect live data.

## Choose the question, not the whole suite

| Tool / evidence owner | Question | Accepted input for these offline workflows | Output / local writes | Target effects and limits |
| --- | --- | --- | --- | --- |
| BEC / BEC agent | What email/account activity is supported for this account and incident window? | Existing approved provider exports and saved tenant-bound cases; optional mailbox snapshot through the separate incident-companion path | New local case, evidence-linked timeline/report or search output, with preserved original bytes; a snapshot companion does not automatically populate the ordinary timeline | Offline only here. No message-body fetching, URL following, arbitrary GAM execution or live Purview search-job creation |
| Flapjacks / M365 audit agent | What organization-wide M365 control posture was observed at collection time, and what could not be assessed? | Synthetic fixtures or already collected configuration snapshots for supported checks; local prototypes kept separate from public capabilities | Local evidence/report for selected controls and optional target-bound mailbox snapshot export | No live sign-in/collection in these workflows; no grants, remediation, rule changes, enrollment or configuration writes |
| CrumbTrail / Windows triage agent | What do supplied Windows events show, with what gaps? | Approved staged JSON/JSONL or explicitly supplied exported EVTX using the tool's supported local parser | Local case, preserved source records, chronology, findings and report | No ambient live-log default, remote hunt, agent deployment or endpoint acquisition in these workflows |
| HashBrown / Acquisition agent | Do existing evidence bytes match a reference, and what custody was recorded? | Existing generic artifacts or already acquired images; registration does not require acquisition | Explicit local registry/custody output and detached handoff manifest | No live capture, RAM driver, provisioning or endpoint operations. Case verification can write local journals/logs; detached verification is a distinct workflow |
| GPO Grits | What do exported on-premises Group Policy records establish? | GPO report XML, optional inheritance JSON and RSoP logging XML | Local HTML and JSON, with source fields and SHA-256 hashes | Offline file review with separate declaration, precedence and target evidence |
| Response Menu / Roadmap agent | Which independent tool and acceptance gate fits the task? | Sanitized owner handoffs and pinned release facts | Planning documents and local validation records | No runtime, shared store, dispatcher, installer or live-service calls |

Tool-owned instructions at the reviewed public main revisions: [BEC README](https://github.com/PendingUpdates/BEC/blob/2d9f59dbe388d54e5243b1dc004e9ede9d0705f7/README.md), [Flapjacks overview](https://github.com/PendingUpdates/Flapjacks/blob/5d7904c521113d53a9f8d3a60e0f84574f34e1d4/README.md), [Flapjacks Audit / Pull Logs](https://github.com/PendingUpdates/Flapjacks/blob/5d7904c521113d53a9f8d3a60e0f84574f34e1d4/terminal/README.md), [CrumbTrail README](https://github.com/PendingUpdates/CrumbTrail/blob/d1dcb1fc559a6baae5a3d91e8a45bdf5bcbee9d1/README.md), [HashBrown README](https://github.com/PendingUpdates/HashBrown/blob/5eb2c195f9937199e1152e4a6e02ed5b846deb82/README.md).

## Target-read-only is not zero filesystem writes

Preserve source bytes and work from permitted copies. Local evidence directories, derived reports, hashes and custody records are intentional writes, each with explicit destinations and overwrite behavior. A tenant read can still require authentication/consent and incur provider-side activity; “read-only” never authorizes it implicitly. These offline workflows exclude server-side search-job creation, remote capture, driver/agent staging and all remediation. Do not follow URLs or execute commands embedded in evidence. Never transfer private evidence to public repositories or production PendingUpdates.

## Bounded runbooks

### Phishing / account investigation

1. Establish tenant, exact account, incident window, available sources and known gaps from approved exports. Keep Entra distinct from on-premises AD DS.
2. Use BEC's documented offline import, verification and report paths for per-incident activity and timelines. Label observed activity separately from interpretation.
3. If a compatible Flapjacks snapshot is supplied, use BEC's separate mailbox-state import and incident-companion path. It does not automatically populate the ordinary timeline. Verify tenant/mailbox binding and preserve acquisition time, byte hash, evidence class and source/record pointer. Require paired fixture evidence for the exact producer/consumer revisions; the presence of both implementations on main is not a compatibility guarantee.
4. Show present mailbox rules separately from historical create/update/delete events. Today's absence does not establish deletion or historic absence; today's presence does not prove presence during the incident. Denied/partial coverage is not an empty successful result.
5. Write derived output to an explicit local destination. Optional HashBrown registration must not become a prerequisite for BEC use.

### M365 configuration audit

1. Use Flapjacks Audit for selected organization-wide M365 configuration and control posture observed at collection time. Audit and the narrower Pull Logs workflow are available on public main; record the exact revision and keep local prototypes separate from public capabilities. Route per-incident account activity and timelines to BEC.
2. For each audit control, report a stable ID, observed value, reference policy/version where applicable, evidence pointer and pass/gap/not-applicable/not-assessed disposition. Keep permission, licensing and collection gaps separate from configuration findings. Do not score unknown as compliant.
3. Use only synthetic/existing data for these offline workflows. A later live lab needs designated tenant/scope and separate authorization; no automatic grants or corrective actions.
4. Export optional mailbox state only with exact target binding and truthful evidence class. Current configuration does not establish historical activity. Pull Logs is narrower than the legacy historical audit collection and is not a claim of BEC coverage parity; preserve the legacy collector until replacement parity is verified. Optional snapshot compatibility requires its own paired acceptance.

### On-premises Group Policy audit

1. Export the relevant Group Policy reports on an administration workstation and copy them to the reviewing computer. [GPO Grits setup and export instructions](https://github.com/PendingUpdates/GPO-Grits#run-your-first-audit)
2. From the extracted GPO Grits folder, run `py -3 grits.py audit --gpo domain.xml --out grits-report` on Windows. Open `grits-report/report.html` to review computer minimum password length and user screen saver timeout.
3. Include a saved inheritance snapshot for the domain or OU to see link precedence. Include a logging RSoP report to review a value observed on a named target. Missing or ambiguous evidence appears as **Not assessed**.

### Endpoint-event triage

1. Supply explicit exported files and supported host/source context. Retain complete original EVTX separately from derived output.
2. Run the tool's offline validation and chronology/session interpretation. Test boundary events, reused IDs and ambiguous roles before drawing account/process associations.
3. Report missing channels, source precision and coverage; parser success and a clean timeline do not establish a clean endpoint. Broader W2 remains open.
4. Optionally hand off existing source and derived artifacts for custody, retaining classification and parent references. Do not initiate collection from the menu.

### Existing-evidence handoff

1. Identify existing evidence, scope, producer, original/derived class, acquisition bounds and partial status. HashBrown supports generic existing-artifact registration as well as already acquired images; no acquisition is required to register supplied files. Physical-disk and live RAM capture remain separately unqualified until their documented lab gates pass.
2. Use the tool-owned supported workflow to hash selected files and create a detached manifest. Record any local case/journal writes separately.
3. Transfer evidence through an approved channel and verify at the recipient against the manifest, optionally with an independent reference hash. A manifest does not automatically copy the evidence files.
4. Retain partial states and failures. Matching hashes demonstrate agreement with reference bytes, not authenticity, complete acquisition or chain-of-custody trust by themselves.

## Optional mailbox snapshot v1

**Optional file contract, not a mandatory suite schema or a compatibility promise for every version.** Flapjacks produces a JSON file; BEC consumes it independently through its separate incident companion. Public implementation availability does not replace paired revision/fixture acceptance. No shared runtime library, database or sibling import. Required envelope:

```json
{
  "schema": "response-menu.mailbox-snapshot.v1",
  "tenant_id": "00000000-0000-0000-0000-000000000001",
  "mailbox_upn": "analyst@example.test",
  "acquired_at": "2026-11-16T00:00:00Z",
  "synthetic": true,
  "evidence_class": "reserialized-source-objects",
  "sources": {
    "inbox_rules": {"status": "collected", "records": []},
    "forwarding": {"status": "denied", "records": []},
    "delegates": {"status": "unavailable", "records": []}
  }
}
```

- `tenant_id`: GUID, matched to the destination case; `mailbox_upn`: lowercase exact UPN, not a broad search or display-name match.
- `acquired_at`: ISO UTC acquisition time, distinct from historical event time; `synthetic`: boolean, carried through outputs.
- `evidence_class`: exactly `reserialized-source-objects`. Preserve source objects honestly; do not call these original HTTP response bytes.
- Each required source (`inbox_rules`, `forwarding`, `delegates`) has a `records` array and `status` of `collected`, `partial`, `denied` or `unavailable`. Do not coerce inaccessible or missing coverage to successfully collected empty data.
- BEC ingest computes and preserves the hash of supplied file bytes plus the source and record pointer. For example, `sources.inbox_rules.records[0]` identifies the first inbox-rule record. Original vs derived classification and transformation context must survive reporting.
- Reject mismatched tenant/mailbox and unbound live data. Synthetic test data must remain unmistakably synthetic. No self-reported “safe” marker permits live collection.
- Record field vocabulary and producer/consumer compatibility must be proven with the same bounded synthetic fixture before advancement. Do not infer a wider provider event schema from this envelope.

Acceptance packet: exact producer/consumer revisions, fixture byte hash, commands, record pointers, preserved target/acquisition facts and actual outcomes. Include hidden/still-present, delegate-created and subsequently deleted rule scenarios, denied/partial coverage, wrong tenant/mailbox, malformed input, tampering and snapshot-time/event-time differences. Failed and not-run checks stay visible. BEC and Flapjacks do not need each other for their primary standalone workflows. Resolve reuse/licensing separately before copying implementation code.
