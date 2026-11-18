# Response Menu

![Pixel-art diner with animated monitor charts and pixel steam](docs/assets/Response-Menu-Banner.gif)

[View the still banner](docs/assets/Response-Menu-Banner.png)

A menu of independent incident-response and security-posture tools. Choose the tool for your task; each has its own installation, permissions, evidence format and reporting.

**Response Menu contains documentation only.** It is not a launcher or shared installer, and installing one tool does not require the others.

## Pick a tool

[![BEC: bacon, egg and cheese sandwich](docs/assets/BEC.png)](https://github.com/PendingUpdates/BEC) [![CrumbTrail: toast](docs/assets/CrumbTrail.png)](https://github.com/PendingUpdates/CrumbTrail) [![HashBrown: hash brown](docs/assets/HashBrown.png)](https://github.com/PendingUpdates/HashBrown) [![Flapjacks: pancakes](docs/assets/Flapjacks.png)](https://github.com/PendingUpdates/Flapjacks) [![Pallette Clenser: fruit bowl](docs/assets/Pallette-Clenser-Tile.png)](https://github.com/PendingUpdates/Pallette-Clenser)

| Tool | What it is for |
| --- | --- |
| [BEC](https://github.com/PendingUpdates/BEC) | Investigate email and account compromise with evidence-linked reporting. |
| [Flapjacks](https://github.com/PendingUpdates/Flapjacks) | Review Microsoft 365 tenant configuration and security posture, with explicit coverage gaps. |
| [CrumbTrail](https://github.com/PendingUpdates/CrumbTrail) | Build Windows event timelines and surface useful observations. |
| [HashBrown](https://github.com/PendingUpdates/HashBrown) | Track evidence, integrity and custody; use its separate acquisition workflow when collection is needed. |
| [Pallette Clenser](https://github.com/PendingUpdates/Pallette-Clenser) | Synthetic-only application-ownership audit planner; no host scanning, real-product detection or removal. |

## Getting started

1. Open the tool's repository and follow its README and setup instructions.
2. Install only that tool's prerequisites. BEC, CrumbTrail and HashBrown use independent Python packages; Flapjacks uses PowerShell and does not require Python.
3. Review the permissions for the mode you intend to use. Offline work with saved evidence does not require cloud credentials.
4. Use the [workflow menu](docs/tool-workflows.md) for task-specific guidance and evidence handoffs.

See [setup and prerequisites](docs/setup.md) for working with Response Menu itself. No suite installation is required.

## Permissions at a glance

Reading Response Menu requires no Microsoft 365, Google Workspace, Active Directory or endpoint administrator access. There is no shared service account or suite-wide permission grant.

| Tool | Microsoft 365 | Google Workspace | On-premises Active Directory | Local or host access |
| --- | --- | --- | --- | --- |
| [Flapjacks](https://github.com/PendingUpdates/Flapjacks) | Approved delegated Graph reads and, for applicable checks, matching Exchange/Purview sessions. Identity-only sign-in does not unlock the audit scopes. | Not used. | Not used; Microsoft Entra is separate. | PowerShell and access to the checkout; write only if saving local results. [Authentication and setup](https://github.com/PendingUpdates/Flapjacks/blob/main/terminal/docs/AUTHENTICATION.md) |
| [BEC](https://github.com/PendingUpdates/BEC) | Admin-consented Graph **application** permissions for the chosen live collectors, with separate trace provisioning where applicable. | Delegated service account and an authorized reports admin for Admin SDK audit reports; no Gmail mailbox access scope. | No native collector; no AD privileges required. | Read supplied exports and write the local case; no provider credentials for offline work. [Microsoft setup](https://github.com/PendingUpdates/BEC/blob/main/docs/security.md) · [Workspace setup](https://github.com/PendingUpdates/BEC/blob/main/docs/workspace.md) |
| [CrumbTrail](https://github.com/PendingUpdates/CrumbTrail) | No cloud permissions. | Not used. | No directory bind or cloud API permissions. | Access to the input Windows artifacts and local output. Collecting protected source artifacts separately may require channel- or host-specific access. |
| [HashBrown](https://github.com/PendingUpdates/HashBrown) | No cloud permissions. | Not used. | Not used. | Existing-evidence registration requires local file access. Direct acquisition is a separate workflow with its own platform prerequisites; don't grant acquisition privileges merely to work with existing evidence. |
| [Pallette Clenser](https://github.com/PendingUpdates/Pallette-Clenser) | Not used. | Not used. | Not used. | Python standard library and supplied synthetic fixtures only; no administrator access, cloud credentials or live collection. |

Provision only the permissions for the mode you plan to use. Each tool's README and setup docs provide its exact scopes, roles, licensing and supported platforms. A source that could not be read is a coverage gap, not a passing security check.

## Documentation and contributors

- [Tool workflows](docs/tool-workflows.md)
- [Setup and prerequisites](docs/setup.md)
- [Project roadmap](ROADMAP.md)
- [Release and development records](docs/release-validation.md)

To work with a tool's Codex agent, open that tool's repository and follow its `AGENTS.md` and agent brief. These are reusable instructions, not always-running processes. Response Menu owns the planning work only; see [contributor instructions](AGENTS.md) and the [roadmap agent brief](agents/roadmap.md).
