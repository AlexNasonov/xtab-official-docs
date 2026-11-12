---
title: "Overview of the current version"
description: "xtab 0.8.0 — tables for working together in the browser, on your own server and without access to the internet."
version: "v0.8.0"
lang: "en"
---

**xtab 0.8.0** — tables for working together in the browser, on your own server and without access to the internet. The eighth internal version, functionally complete: running it on your own server — a license, backups with a restore to any moment, the administration panel of the installation, observability; accepted for 500 concurrent users.

- Login by invitation, password and password reset link; a second factor — an authenticator app and recovery codes, passkeys; login through the provider of the organization (OpenID Connect, Active Directory through Keycloak of the delivery).
- Profile: photo, name, time zone, a new password and e-mail, one's own sessions, an export of one's own data.
- The panel of the administrator: members with blocking, second factor reset and deletion on request, groups, access, policies of passwords and the second factor, the permission matrix, organization settings.
- An audit log with filters and export, sealed into a signed chain, archived and delivered to SIEM; built-in security alerts.
- Workspaces, bases and tables; jump to a base, table or record with Ctrl+K.
- Access to workspaces and bases right in the interface: members, roles, invitations, roles of groups.
- A grid of hundreds of thousands of records: fast scrolling, the primary field pinned on the left, editing right in the cell.
- 29 types of fields: text (rich text too), email, URL, phone number, numbers, currency, percent, duration, rating, checkbox, selects, users, dates, attachments and system fields.
- Links between tables with lookups, counts and rollups over the linked records.
- Formulas in the style of Excel and Airtable: suggestions as you type, mistakes shown in place, a recount on every change.
- Attachments: files in cells, image thumbnails in the table, PDFs viewed right inside xtab.
- Views of a table: grid, kanban and form; their own visible fields, filters with condition groups, sorting, grouping, record colours, summaries under columns.
- Forms to collect records: inside xtab and by a public link without signing in, protected from robots, with files attached.
- Search in a view (Ctrl+F).
- Range selection, copying and pasting from Excel and Google Sheets, fill down, undo and redo.
- Import of tables and records from CSV and Excel, export of a view to CSV and Excel.
- Interfaces: pages of grids, lists, kanbans, record cards, forms, numbers, texts, buttons and filters over a base; a builder with layouts, a draft and its publication; access to a single interface without access to its base.
- Automations: when a record is created, changes, begins to meet a condition or comes from a form — update the record, create a record in another table, send an email or an HTTP request; a run log with running again.
- Copies of a table, a base and a workspace with their data, links, files and views.
- A whole record in its own window: press Space or click the row number.
- Changes by other people show up at once, without reloading the page.
- Russian and English interface, light and dark themes.
- REST API with an OpenAPI specification: access by API tokens with permissions and rate limits, service accounts for integrations.
- Delivered as a single executable and Docker Compose; works in a closed network; installation, update, rollback and restore of the database with one command of the installer; Debian 12 and Debian 13.
- Operations: a license with a trial, backups with a restore to any moment and a weekly drill, the administration panel of the installation, moving and upkeep, dashboards and alerts.
- Accessibility: screen readers and a zoom of the interface up to 200 %.
