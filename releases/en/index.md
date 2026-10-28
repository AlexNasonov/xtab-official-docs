---
title: "Overview of the current version"
description: "xtab 0.2.0 — tables for working together in the browser, on your own server and without access to the internet."
version: "v0.2.0"
lang: "en"
---

**xtab 0.2.0** — tables for working together in the browser, on your own server and without access to the internet. The second internal version: views, filters, search, data exchange with Excel and an English interface.

- Login by invitation, password and password reset link; invitations and roles in workspaces and bases are given through the API for now.
- Workspaces, bases and tables; jump to a base, table or record with Ctrl+K.
- A grid of hundreds of thousands of records: fast scrolling, the primary field pinned on the left, editing right in the cell.
- Twelve types of fields: single line text, long text, number, checkbox, single select, date, date and time, autonumber and system fields.
- Views of a table: their own visible fields, column widths and row height, filters with condition groups, sorting, grouping, record colours, summaries under columns.
- Search in a view (Ctrl+F).
- Range selection, copying and pasting from Excel and Google Sheets, fill down, undo and redo.
- Import of tables and records from CSV and Excel, export of a view to CSV and Excel.
- A whole record in its own window: press Space or click the row number.
- Changes by other people show up at once, without reloading the page.
- Russian and English interface, light and dark themes.
- REST API with an OpenAPI specification.
- Delivered as a single executable and Docker Compose; works in a closed network.
