---
id: 3a8f1c6d-e4b2-4d90-a7f5-9c3e6b1d8a42
tags:
  - "#dashboard"
  - "#read-only"
---

```dataviewjs
function formatName(p) {
  return p.file.name.replace(/^\(Spec\)\s*/, '');
}

function statusIcon(status) {
  const icons = {
    'draft': '📝',
    'proposed': '📋',
    'ratified': '✅',
    'stable': '🔒',
    'amended': '✏️',
    'deprecated': '⚠️',
    'superseded': '🔄'
  };
  return icons[status] || '📝';
}

// Only root specs (no dot notation = no sub-specs)
const allSpecs = dv.pages('#spec/spec').where(p => p.file.path.startsWith('Mesh/'));
const rootSpecs = allSpecs.where(p => !p.file.name.includes(' . '));
const sections = allSpecs.where(p => p.file.name.includes(' . '));

// Active Specs (draft, proposed, ratified, stable, amended)
dv.header(1, "Active");
const active = rootSpecs.where(p =>
  ['draft', 'proposed', 'ratified', 'stable', 'amended'].includes(p.status)
).array().sort((a, b) => a.file.name.localeCompare(b.file.name));

if (active.length === 0) {
  dv.paragraph("*None*");
} else {
  dv.table(["Spec", "Status", "Version", "Sections"],
    active.map(p => {
      const children = sections.where(s =>
        s.file.folder === p.file.folder
      ).array();
      return [
        dv.fileLink(p.file.path, false, formatName(p)),
        statusIcon(p.status) + " " + (p.status || "—"),
        p.version || "—",
        children.length > 0 ? children.length : "—"
      ];
    })
  );
}

// Deprecated / Superseded
dv.header(1, "Archived");
const archived = rootSpecs.where(p =>
  ['deprecated', 'superseded'].includes(p.status)
).array().sort((a, b) => a.file.name.localeCompare(b.file.name));

if (archived.length === 0) {
  dv.paragraph("*None*");
} else {
  dv.table(["Spec", "Status", "Superseded By"],
    archived.map(p => [
      dv.fileLink(p.file.path, false, formatName(p)),
      statusIcon(p.status) + " " + (p.status || "—"),
      p["superseded-by"] || "—"
    ])
  );
}
```
