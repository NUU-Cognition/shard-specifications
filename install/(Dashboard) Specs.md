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
    'approved': '✅',
    'implemented': '🏁'
  };
  return icons[status] || '📝';
}

// Only root specs (no dot notation = no sub-specs)
const allSpecs = dv.pages('#spec/spec').where(p => p.file.path.startsWith('Mesh/'));
const rootSpecs = allSpecs.where(p => !p.file.name.includes(' . '));
const sections = allSpecs.where(p => p.file.name.includes(' . '));

// Active Specs (draft, approved)
dv.header(1, "Active");
const active = rootSpecs.where(p =>
  ['draft', 'approved'].includes(p.status)
).array().sort((a, b) => a.file.name.localeCompare(b.file.name));

if (active.length === 0) {
  dv.paragraph("*None*");
} else {
  dv.table(["Spec", "Status", "Sections"],
    active.map(p => {
      const children = sections.where(s =>
        s.file.folder === p.file.folder
      ).array();
      return [
        dv.fileLink(p.file.path, false, formatName(p)),
        statusIcon(p.status) + " " + (p.status || "—"),
        children.length > 0 ? children.length : "—"
      ];
    })
  );
}

// Implemented
dv.header(1, "Implemented");
const implemented = rootSpecs.where(p =>
  p.status === 'implemented'
).array().sort((a, b) => a.file.name.localeCompare(b.file.name));

if (implemented.length === 0) {
  dv.paragraph("*None*");
} else {
  dv.table(["Spec", "Sections"],
    implemented.map(p => {
      const children = sections.where(s =>
        s.file.folder === p.file.folder
      ).array();
      return [
        dv.fileLink(p.file.path, false, formatName(p)),
        children.length > 0 ? children.length : "—"
      ];
    })
  );
}
```
