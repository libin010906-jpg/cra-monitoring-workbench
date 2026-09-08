# CRA Monitoring Workbench

A Codex skill for turning clinical monitoring notes into traceable, review-ready CRA work products.

## Capabilities

- Build site-specific visit preparation checklists.
- Normalize raw findings into separate action items.
- Track category, owner, due date, status, and closure evidence.
- Draft monitoring summaries and follow-up letters.
- Produce schema v2 JSON that can be imported into CRA Compass.

## Install

Ask Codex:

```text
Install the skill from https://github.com/libin010906-jpg/cra-monitoring-workbench
```

Or download this repository and place the folder in your Codex skills directory.

## Use

```text
Use $cra-monitoring-workbench to turn these site-visit notes into action items and a follow-up letter.
```

## Safety boundary

Do not include participant names, contact details, medical-record numbers, or national identifiers. Use study subject IDs only. Outputs are drafts and require qualified review against the protocol, monitoring plan, SOPs, source records, and applicable requirements.
