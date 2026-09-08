# CRA Compass data format

Use schema version 2 for importable workspaces. All dates use `YYYY-MM-DD`; `updatedAt` uses ISO 8601. IDs are unique within their collection. Never place participant names, initials, contact details, medical-record numbers, or national identifiers in the file.

```json
{
  "schemaVersion": 2,
  "projects": [{ "id": "STUDY-01", "name": "研究名称", "protocol": "PRO-01", "phase": "III期", "sponsor": "申办方", "status": "进行中" }],
  "sites": [{ "id": "SITE-001", "projectId": "STUDY-01", "name": "示例中心", "city": "上海", "target": 20, "contact": "CRC", "phone": "", "notes": "", "risk": 0, "nextVisit": "", "enrollment": "0/20", "queryRate": "待录入" }],
  "visits": [],
  "subjects": [],
  "issues": [],
  "documents": [],
  "complianceChecks": [],
  "checklists": { "SITE-001": [] },
  "updatedAt": "2026-09-07T00:00:00.000Z"
}
```

References must resolve: every site uses an existing `projectId`; visit, subject, issue, document, compliance check, and checklist keys use an existing site ID; an issue `visitId` or `subject`, when present, must resolve within that site.

Allowed values:

- project status: `筹备`, `进行中`, `已关闭`;
- visit type: `启动访视`, `常规监查`, `关闭访视`, `远程监查`;
- visit status: `计划中`, `准备中`, `已完成`, `已取消`;
- subject status: `筛选中`, `在组`, `随访中`, `已完成`, `退出`, `筛选失败`;
- issue severity: `紧急`, `高`, `中`, `低`;
- issue status: `待处理`, `等待中心`, `已关闭`;
- document status: `有效`, `待更新`, `缺失`, `已归档`;
- check status: `待检查`, `符合`, `待跟进`, `不适用`.

Issue example:

```json
{
  "id": "ISS-2001",
  "site": "SITE-001",
  "visitId": "VIS-001",
  "subject": "001-008",
  "category": "方案偏离",
  "detail": "V4 检查超出访视窗，待完成影响评估",
  "severity": "中",
  "owner": "中心研究者",
  "due": "2026-09-12",
  "status": "等待中心",
  "created": "2026-09-07",
  "rootCause": "待确认",
  "correctiveAction": "补充偏离记录和影响评估",
  "preventiveAction": "待确认"
}
```

Use `待确认` only for required text when a directly importable file is requested. Ask the qualified user to choose unknown severity and deadlines. Do not infer closure or compliance. The app recalculates `risk`; export it as 0. Editable local history is not a validated audit trail.

