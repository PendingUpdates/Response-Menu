# Setup and prerequisites

## Reading Response Menu

No runtime installation, Python, PowerShell, Microsoft account, tenant access or provider credentials are needed to read these planning documents. Open the repository on GitHub or read a downloaded copy in a Markdown/text viewer. Response Menu is not an executable launcher and does not install the other tools.

## Working with a local copy

Git is needed only for cloning and version-control operations, not for reading a downloaded copy. Verify availability with `git --version`. Clone into a new destination rather than replacing an existing working tree:

```text
git clone https://github.com/PendingUpdates/Response-Menu.git
cd Response-Menu
git status --short
git rev-parse HEAD
```

If a checkout already exists, use it and preserve its local edits; do not repeat the clone over it. Read [repository instructions](../AGENTS.md) before editing. A local checkout does not authorize publishing, live collection or changes to sibling repositories.

## Optional local documentation validation

Use **Python 3.11 or newer** because the check uses the standard-library `tomllib` module. No pip packages or response-tool installations are required. Hosted [documentation CI](../.github/workflows/docs.yml) uses **Python 3.12 on Linux**; a local check on another supported Python/OS is not a hosted CI result.

Select an installed interpreter and verify it before running the check. Examples: `python3.11 --version` on macOS/Linux, or `py -3.12 --version` on Windows. Do not assume that `python3` is recent enough; macOS may resolve it to Python 3.9. An import error for `tomllib` means this interpreter is too old for this check, not that a response-tool dependency is missing.

From the repository root, launch your selected Python interpreter (for example `python3.11` or `py -3.12`) and run this source check:

```python
import pathlib, re, tomllib
root = pathlib.Path.cwd()
assert (root / ".github/workflows/docs.yml").is_file(), "Run from repository root"
for file in root.rglob("*.md"):
    # Match destinations independently so linked images include both targets.
    for href in re.findall(r"\]\(([^)]+)\)", file.read_text(encoding="utf-8")):
        if "://" not in href and not href.startswith("#"):
            target = (file.parent / href.split("#")[0]).resolve()
            assert target.is_relative_to(root) and target.exists(), (file, href)

for file in (root / ".codex").rglob("*.toml"):
    tomllib.loads(file.read_text(encoding="utf-8"))

print("Local links and agent configuration passed.")
```

Then, in the shell, run `git diff --check` to check diff whitespace. The authoritative check source is the linked CI workflow; keep this example aligned with it. These checks validate local Markdown file targets and TOML syntax, not external URLs, Markdown anchors, sibling code, live permissions, tenant security or interoperability.

## Independent tool prerequisites

Install only the tool needed, following that tool's own setup instructions for the exact revision you choose. Response Menu adds no common runtime or credentials. The [workflow menu](tool-workflows.md) links the reviewed tool instructions, and the [release ledger](release-validation.md) distinguishes published baselines from uncommitted local work.

| Tool | Runtime / scope overview |
| --- | --- |
| BEC | Independent Python application for email/account incident evidence; optional provider dependencies and authentication are separate from offline use |
| Flapjacks | Independent PowerShell application for Microsoft 365 tenant posture; Python is not its prerequisite; live Microsoft sessions/permissions are separate from synthetic or offline evaluation |
| CrumbTrail | Independent Python application for Windows-event triage; optional EVTX parsing tools are required only for the documented parsing workflow |
| GPO Grits | Python 3.9 or newer and the standard library. The offline auditor reads administrator-supplied on-premises Group Policy reports and writes local HTML and JSON. |
| HashBrown | Independent Python application for evidence integrity/custody and separately scoped acquisition; offline existing-evidence work does not require live acquisition setup |

No installation, provider sign-in, permission grant, endpoint capture or remediation is performed by these instructions. Local evidence/report writes must remain explicit and preserve original inputs; see the workflow boundary before running any tool.
