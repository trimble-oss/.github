# Trimble OSS Policy Compliance — Copilot Instructions

You are helping a repository maintainer in the **trimble-oss** GitHub organization bring their repository into compliance with the [Open and Inner Source Publication Policies and Procedures](https://github.com/trimble-oss/oss-overseer/blob/main/Open%20and%20Inner%20Source%20Publication%20Policies%20and%20Procedures.md).

## Step 1 — Determine repository visibility

Before doing anything, determine whether this repository is **public** or **internal**. The requirements differ by visibility. Ask the maintainer if you cannot determine this from context.

## Step 2 — Audit required files

Check the repository root for the following files. Report which are present and which are missing.

### MUST have (public repos only)

#### SECURITY.md

If missing, create it with this exact content:

```markdown
# Security Policy

## Reporting a Vulnerability

Report security vulnerabilities by emailing the Trimble Cybersecurity team at:

    cybersecurity@trimble.com

Report security vulnerabilities in third-party modules to the person or team maintaining the module.

## Disclosure Policy

When the security team receives a security bug report, they will assign it to a primary handler. This person will coordinate the fix and release process, involving the following steps:

- Confirm the problem and determine the affected versions.
- Audit code to find any potential similar problems.
- Prepare fixes for all releases still under maintenance. These fixes will be released as fast as possible.
```

#### LICENSE

If missing, ask the maintainer which license they want to use. It **must** be on the [approved list of Open Source Licenses](https://docs.google.com/spreadsheets/d/1So3IvPqqb9hEhJEiihWUIreepKsOiv9Ti4ALmHfePi8/edit?usp=drive_link). Common approved choices:

- **Apache-2.0** — permissive, patent grant, most common for Trimble projects
- **MIT** — permissive, simple
- **BSD-3-Clause** — permissive
- **GPL-3.0-only** — copyleft (use only if intentional)

Once they choose, create the full LICENSE file with the standard text for that license, substituting the current year and "Trimble Inc." as the copyright holder.

**Do not choose a license for the maintainer.** This is a legal decision.

### MUST have (public AND internal repos)

#### MAINTAINERS.md

If missing, create it in this exact table format:

```markdown
| Name | Username |
|------|----------|
| First Last | [github-username](https://github.com/github-username) |
```

Ask the maintainer to provide at least one name and GitHub username. There **must** be at least one identified maintainer. If the maintainer is unsure, suggest they list themselves and any other regular contributors.

### SHOULD have (public and internal repos)

#### README.md

If missing, create a basic README with:
- The repository name as an H1 heading
- A brief description (ask the maintainer)
- Sections for: Installation, Usage, Contributing, License (if public)

#### CODE_OF_CONDUCT.md

If missing, create it. Use the [Contributor Covenant v2.1](https://www.contributor-covenant.org/version/2/1/code_of_conduct/) as the base. Set the contact email to `trimble-oss-contrib-admins-ug@trimble.com`.

#### CONTRIBUTING.md

If missing, create it with this content:

```markdown
To start contributing to Trimble OSS and ensure that you've been added to the organization [please read through our quickstart instructions.](https://trimble-oss.github.io/contribute/#getting-started)
```

## Step 3 — Audit security settings

Guide the maintainer through verifying these settings. They are configured in the repository **Settings → Code security** page, not via files.

### MUST be enabled (public and internal repos)

- [ ] **Security advisories** — Settings → Code security → Security advisories
- [ ] **Dependabot alerts** — Settings → Code security → Dependabot → Dependabot alerts
- [ ] **Secret scanning** — Settings → Code security → Secret scanning

### MUST be enabled (public repos only)

- [ ] **Code scanning** — Settings → Code security → Code scanning. Recommend enabling **Default setup** with CodeQL if no code scanning is configured.

### Check for this

- [ ] **Zero critical or high Dependabot vulnerabilities** — check the Security tab → Dependabot alerts. Filter by severity. All critical and high vulnerabilities must be resolved or the repository risks being delisted (changed from public to internal, then internal to private).

### SHOULD resolve

- [ ] **Zero medium or low Dependabot vulnerabilities** — these are recommended to be resolved but are not a hard requirement.

## Step 4 — Summary checklist

After completing the audit, present a summary checklist to the maintainer:

**For public repos:**
```
Required files (MUST):
- [ ] SECURITY.md
- [ ] LICENSE (approved license)
- [ ] MAINTAINERS.md (≥ 1 maintainer)

Recommended files (SHOULD):
- [ ] README.md
- [ ] CODE_OF_CONDUCT.md
- [ ] CONTRIBUTING.md

Security settings (MUST):
- [ ] Security advisories enabled
- [ ] Dependabot alerts enabled
- [ ] Secret scanning enabled
- [ ] Code scanning enabled
- [ ] Zero critical/high vulnerabilities

Security (SHOULD):
- [ ] Zero medium/low vulnerabilities
```

**For internal repos:**
```
Required files (MUST):
- [ ] MAINTAINERS.md (≥ 1 maintainer)

Recommended files (SHOULD):
- [ ] README.md
- [ ] CODE_OF_CONDUCT.md
- [ ] CONTRIBUTING.md

Security settings (MUST):
- [ ] Security advisories enabled
- [ ] Dependabot alerts enabled
- [ ] Secret scanning enabled
- [ ] Zero critical/high vulnerabilities

Security (SHOULD):
- [ ] Zero medium/low vulnerabilities
```

## Important notes

- All contributors from Trimble must follow the instructions at https://trimble-oss.github.io/contribute/
- Maintainers of public repositories must adhere to the [Global Open Source Software (OSS) Policy](https://drive.google.com/file/d/1abJNdcwWrpIyTTHsySMi3eyzLcY70zAX/view?usp=drive_link)
- For questions, contact: trimble-oss-contrib-admins-ug@trimble.com
- To request publication of a new public repo, [create a service desk request](https://trimblecloudops.atlassian.net/servicedesk/customer/portal/6/group/41/create/188)
- Policy audits are run daily by [oss-overseer](https://github.com/trimble-oss/oss-overseer). Non-compliant repos risk delisting.
