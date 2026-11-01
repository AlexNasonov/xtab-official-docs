---
title: "Permissions"
description: "What each role can do in a workspace and in a base. Columns: R — read only, Cm — commenter, E — editor, Cr — creator, O — owner; each next role includes the rights of the previous one."
version: "v0.3.0"
lang: "en"
---

What each role can do in a workspace and in a base. Columns: R — read only, Cm — commenter, E — editor, Cr — creator, O — owner; each next role includes the rights of the previous one. ✓ — allowed, — — not allowed.

## Workspace

| Action | R | Cm | E | Cr | O |
|---|---|---|---|---|---|
| See the workspace and its bases | ✓ | ✓ | ✓ | ✓ | ✓ |
| Create a base | — | — | — | ✓ | ✓ |
| Rename the workspace | — | — | — | — | ✓ |
| Manage the members of the workspace | — | — | — | ✓¹ | ✓ |
| Delete and restore the workspace | — | — | — | — | ✓ |

## Base and structure

| Action | R | Cm | E | Cr | O |
|---|---|---|---|---|---|
| Open the base, see its tables and fields | ✓ | ✓ | ✓ | ✓ | ✓ |
| Rename the base, change its icon | — | — | — | ✓ | ✓ |
| Manage the members of the base | — | — | — | ✓¹ | ✓ |
| Delete and restore the base | — | — | — | — | ✓ |
| Create, change, delete a table | — | — | — | ✓ | ✓ |
| Create, change, delete a field; change the type of a field | — | — | — | ✓ | ✓ |
| Import into a new table | — | — | — | ✓ | ✓ |

## Views and forms

| Action | R | Cm | E | Cr | O |
|---|---|---|---|---|---|
| See shared views | ✓ | ✓ | ✓ | ✓ | ✓ |
| Filter and sort for a while without saving | ✓ | ✓ | ✓ | ✓ | ✓ |
| Create, change, delete a shared view | — | — | — | ✓ | ✓ |

## Records and attachments

| Action | R | Cm | E | Cr | O |
|---|---|---|---|---|---|
| Read records | ✓ | ✓ | ✓ | ✓ | ✓ |
| Create, change, delete a record; drag a row | — | — | ✓ | ✓ | ✓ |
| Import into an existing table (without creating fields) | — | — | ✓ | ✓ | ✓ |
| Export a view to CSV / XLSX | ✓² | ✓² | ✓² | ✓² | ✓² |

## Notes

1. A creator invites people and changes roles up to Editor; only an owner gives the roles Creator and Owner.
2. A bulk export asks to confirm the identity again and is written to the audit log; the policy of the organization may forbid export to the roles below Editor.
