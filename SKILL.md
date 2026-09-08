---
name: cra-monitoring-workbench
description: Structure clinical monitoring visit notes into CRA Compass-compatible action items, visit checklists, monitoring summaries, and follow-up letters. Use for CRA site-visit preparation, issue normalization, action tracking, or report drafting; do not use as a substitute for medical, safety, regulatory, or qualified-person review.
---

# CRA Monitoring Workbench

Turn scattered monitoring material into one reusable, traceable set of facts. Preserve the user's study terminology, monitoring plan, SOP requirements, and source-of-truth records.

## Choose the output

- For visit preparation, produce a center-specific checklist ordered by participant safety, critical data/processes, and time-sensitive records.
- For raw notes, normalize each distinct finding into one action item. Do not merge findings that need different owners, evidence, or due dates.
- For reporting, draft a concise monitoring summary or follow-up letter from the same normalized actions.
- For CRA Compass import, read [references/data-format.md](references/data-format.md) and return a valid JSON object or file.

## Normalize findings

Capture only supported facts:

- center ID;
- subject ID only when necessary, using the study identifier rather than a name;
- category;
- objective finding;
- risk level;
- owner;
- due date;
- status;
- evidence needed to close the item.

Separate observation from interpretation. If severity, owner, deadline, or closure evidence is missing, mark it as `待确认` in prose or use the data-format fallback rather than inventing it.

Use these default categories when they fit: `SAE/安全性`, `知情同意`, `方案偏离`, `研究药物`, `必备文件`, `数据查询`. Add a study-specific category only when the existing set would obscure meaning.

Order work as follows:

1. participant safety and urgent reporting;
2. informed consent and participant rights;
3. eligibility, endpoints, and major protocol deviations;
4. investigational product accountability and temperature excursions;
5. essential records, training, and routine data queries.

## Draft responsibly

- Use neutral, audit-ready language and distinguish observed facts, requested action, owner, and target date.
- Do not claim compliance, causal assessment, medical significance, or final closure without supporting evidence.
- Do not insert direct identifiers, credentials, or unnecessary health information.
- Treat generated reports and risk ordering as drafts requiring qualified review against the protocol, monitoring plan, SOPs, source records, and applicable requirements.
- Never silently alter imported source data. List assumptions and unresolved fields.

## Return a useful handoff

Provide the requested artifact first, followed by a short `待确认` section when information is missing. When creating CRA Compass JSON, validate its top-level keys, issue statuses, dates, and unique IDs before delivery.
