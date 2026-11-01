---
title: "Overview of the current version"
description: "xtab 0.3.0 — tables for working together in the browser, on your own server and without access to the internet. The third internal version: links between tables, formulas and attachments."
version: "v0.3.0"
lang: "en"
---

**xtab 0.3.0** — tables for working together in the browser, on your own server and without access to the internet. The third internal version: links between tables, formulas and attachments.

- Login by invitation, password and password reset link; invitations and roles in workspaces and bases are given through the API for now.
- Workspaces, bases and tables; jump to a base, table or record with Ctrl+K.
- A grid of hundreds of thousands of records: fast scrolling, the primary field pinned on the left, editing right in the cell.
- 28 types of fields: text, email, URL, phone number, numbers, currency, percent, duration, rating, checkbox, selects, users, dates, attachments and system fields.
- Links between tables with lookups, counts and rollups over the linked records.
- Formulas in the style of Excel and Airtable: suggestions as you type, mistakes shown in place, a recount on every change.
- Attachments: files in cells, image thumbnails in the table, PDFs viewed right inside xtab.
- Views of a table: their own visible fields, column widths and row height, filters with condition groups, sorting, grouping, record colours, summaries under columns.
- Search in a view (Ctrl+F).
- Range selection, copying and pasting from Excel and Google Sheets, fill down, undo and redo.
- Import of tables and records from CSV and Excel, export of a view to CSV and Excel.
- A whole record in its own window: press Space or click the row number.
- Changes by other people show up at once, without reloading the page.
- Russian and English interface, light and dark themes.
- REST API with an OpenAPI specification.
- Delivered as a single executable and Docker Compose; works in a closed network.
