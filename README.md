# Response Menu

<p align="center"><img src="docs/assets/Response-Menu-Banner.gif" alt="Pixel diner counter with breakfast dishes, monitor charts and animated coffee steam"></p>

<p align="center"><a href="docs/assets/Response-Menu-Banner.png">Still banner</a></p>

## The counter menu

**What brought you in?** Pick a category, then open the tool that fits. The tools work independently; Response Menu is their documentation menu. There is no shared installer or suite-wide permission grant.

<details open>
<summary><strong>Investigate · 3 tools</strong> — work an incident or handle evidence</summary>

<a href="https://github.com/PendingUpdates/BEC"><img src="docs/assets/BEC.png" alt="Bacon, egg and cheese sandwich; open BEC" width="108" height="94"></a> <a href="https://github.com/PendingUpdates/CrumbTrail"><img src="docs/assets/CrumbTrail.png" alt="Toast; open CrumbTrail" width="108" height="94"></a> <a href="https://github.com/PendingUpdates/HashBrown"><img src="docs/assets/HashBrown.png" alt="Golden rectangular hash brown; open HashBrown" width="108"></a>

- **[BEC](https://github.com/PendingUpdates/BEC)** — Investigate email and account compromise using live Microsoft 365 or Google Workspace data, or analyze saved evidence offline.
- **[CrumbTrail](https://github.com/PendingUpdates/CrumbTrail)** — Build timelines from supplied Windows event logs and exports, or practice triage with the synthetic lab.
- **[HashBrown](https://github.com/PendingUpdates/HashBrown)** — Import existing disk or memory images and track their hashes and custody. A separate prototype registers supplied files. Native disk and RAM capture through Velociraptor still needs platform qualification.

</details>

---

<details open>
<summary><strong>Audit &amp; plan · 3 tools</strong> — review posture or plan cleanup</summary>

<a href="https://github.com/PendingUpdates/Flapjacks"><img src="docs/assets/Flapjacks.png" alt="Pancakes; open Flapjacks" width="108" height="94"></a> <a href="https://github.com/PendingUpdates/Pallette-Clenser"><img src="docs/assets/Pallette-Clenser.png" alt="Fruit bowl; open Pallette Clenser" width="108"></a> <a href="https://github.com/PendingUpdates/GPO-Grits"><img src="docs/assets/GPO-Grits.png" alt="Grits bowl and spoon; open GPO Grits" width="108"></a>

- **[Flapjacks](https://github.com/PendingUpdates/Flapjacks)** — Review the security posture of a live Microsoft 365 tenant, or explore the audit with the synthetic demo. Reports identify coverage gaps.
- **[Pallette Clenser](https://github.com/PendingUpdates/Pallette-Clenser)** — Audit and plan potentially unwanted app cleanup. The current launcher accepts only supplied test inventories and cannot scan a host or remove apps.
- **[GPO Grits](https://github.com/PendingUpdates/GPO-Grits)** — Audit on-premises Active Directory Group Policy from exported reports. Review declared settings, OU link precedence, and values observed for a specific target.

</details>

## Before you order

Open the chosen tool’s README for setup and mode-specific permissions. Each tool installs independently; BEC and Flapjacks do not require each other.

[Workflows](docs/tool-workflows.md) · [Getting started](#getting-started) · [Setup](docs/setup.md) · [Permissions](#permissions-at-a-glance) · [Development](#documentation-and-contributors)

## Getting started

1. Open the tool's repository and follow its README and setup instructions.
2. Install only that tool's prerequisites. BEC, CrumbTrail and HashBrown use independent Python packages. GPO Grits runs from an extracted folder with Python 3.9 or newer and the standard library. Pallette Clenser uses Python 3.11 or newer and the standard library. Flapjacks uses PowerShell and does not require Python.
3. Review the permissions for the mode you intend to use. Offline work with saved evidence does not require cloud credentials.
4. Use the [workflow menu](docs/tool-workflows.md) for task-specific guidance and evidence handoffs.

See [setup and prerequisites](docs/setup.md) for working with Response Menu itself. No suite installation is required.

## Permissions at a glance

Reading Response Menu requires no Microsoft 365, Google Workspace, Active Directory or endpoint administrator access. There is no shared service account or suite-wide permission grant.

### [Flapjacks](https://github.com/PendingUpdates/Flapjacks)

- **Microsoft 365:** Approved delegated Graph reads and, for applicable checks, matching Exchange/Purview sessions. Identity-only sign-in does not unlock the audit scopes.
- **Google Workspace:** Not used.
- **On-premises Active Directory:** Not used; Microsoft Entra is separate.
- **Local or host access:** PowerShell and access to the checkout; write only if saving local results. [Authentication and setup](https://github.com/PendingUpdates/Flapjacks/blob/main/terminal/docs/AUTHENTICATION.md)

### [GPO Grits](https://github.com/PendingUpdates/GPO-Grits)

The offline auditor needs read access to the exported Group Policy files and write access to a new local report folder. An administrator exports the evidence separately using Windows Group Policy tools. [On-premises Group Policy workflow](docs/tool-workflows.md#on-premises-group-policy-audit)

### [BEC](https://github.com/PendingUpdates/BEC)

- **Microsoft 365:** Admin-consented Graph **application** permissions for the chosen live collectors, with separate trace provisioning where applicable.
- **Google Workspace:** Delegated service account and an authorized reports admin for Admin SDK audit reports; no Gmail mailbox access scope.
- **On-premises Active Directory:** No native collector; no AD privileges required.
- **Local or host access:** Read supplied exports and write the local case; no provider credentials for offline work. [Microsoft setup](https://github.com/PendingUpdates/BEC/blob/main/docs/security.md) · [Workspace setup](https://github.com/PendingUpdates/BEC/blob/main/docs/workspace.md)

### [CrumbTrail](https://github.com/PendingUpdates/CrumbTrail)

- **Microsoft 365:** No cloud permissions.
- **Google Workspace:** Not used.
- **On-premises Active Directory:** No directory bind or cloud API permissions.
- **Local or host access:** Access to the input Windows artifacts and local output. Collecting protected source artifacts separately may require channel- or host-specific access.

### [HashBrown](https://github.com/PendingUpdates/HashBrown)

- **Microsoft 365:** No cloud permissions.
- **Google Workspace:** Not used.
- **On-premises Active Directory:** Not used.
- **Local or host access:** Existing-evidence registration requires local file access. Direct acquisition is a separate workflow with its own platform prerequisites; don't grant acquisition privileges merely to work with existing evidence.

### [Pallette Clenser](https://github.com/PendingUpdates/Pallette-Clenser)

- **Microsoft 365:** Not used.
- **Google Workspace:** Not used.
- **On-premises Active Directory:** Not used.
- **Local or host access:** Python standard library and supplied synthetic fixtures only; no administrator access, cloud credentials or live collection.

Provision only the permissions for the mode you plan to use. Each tool's README and setup docs provide its exact scopes, roles, licensing and supported platforms. A source that could not be read is a coverage gap, not a passing security check.

## Documentation and contributors

- [Tool workflows](docs/tool-workflows.md)
- [Setup and prerequisites](docs/setup.md)
- [Project roadmap](ROADMAP.md)
- [Release and development records](docs/release-validation.md)

To work with a tool's Codex agent, open that tool's repository and follow its `AGENTS.md` and agent brief. These are reusable instructions, not always-running processes. Response Menu owns the planning work only; see [contributor instructions](AGENTS.md) and the [roadmap agent brief](agents/roadmap.md).
