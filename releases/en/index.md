---
title: "Overview of the current version"
description: "xtab 0.9.0 — tables for working together in the browser, on your own server and without access to the internet."
version: "v0.9.0"
lang: "en"
---

**xtab 0.9.0** — tables for working together in the browser, on your own server and without access to the internet. The ninth version — improvements after the pilot; functionally complete: running it on your own server — a license, backups with a restore to any moment, the administration panel of the installation, observability; accepted for 500 concurrent users.

- Sign-in by invitation, password and password reset link; a second factor — an authenticator app and recovery codes, passkeys; sign-in through the provider of the organization (OpenID Connect, Active Directory through Keycloak of the delivery).
- Profile: photo, name, time zone, a new password and e-mail, one's own sessions, an export of one's own data.
- The panel of the administrator: members with blocking, second factor reset and deletion on request, groups, access, policies of passwords, sessions and the second factor, the permission matrix, organization settings; announcements of the administrator of the installation by a banner for every user.
- An audit log with filters and export, sealed into a signed chain, archived and delivered to SIEM; built-in security alerts.
- Workspaces, bases and tables; one order of the tabs of tables and of the views for everyone; a table opens in the view last chosen in it, a base — in the table last opened; an «All tables» menu and tabs hidden for oneself; jump to a base, table or record with Ctrl+K.
- Access to workspaces and bases right in the interface: members, roles, invitations, roles of groups.
- A grid of hundreds of thousands of records: fast scrolling, the primary field pinned on the left, editing right in the cell, a manual order of records by dragging; linked records, people and choices are picked from a drop-down list with a search; the menus of a cell and of a field from the keyboard too.
- 29 types of fields: text (rich text too), email, URL, phone number, numbers, currency, percent, duration, rating, checkbox, selects, users, dates, attachments and system fields; a number, currency or percent format for formulas, lookups and rollups too; dates with or without the time.
- Links between tables with an inverse field, a condition of choosing records, lookups, counts and rollups over the linked records.
- Formulas in the style of Excel and Airtable: suggestions as you type, mistakes shown in place, a recount on every change.
- Attachments: files in cells, image thumbnails in the table, PDFs viewed right inside xtab.
- Views of a table: grid, kanban and form; their own visible fields, filters with condition groups, sorting, grouping (by a link — in the order of the records of the linked table too), record colours, summaries under columns; a new record takes the values of the filter.
- Forms to collect records: inside xtab and by a public link without signing in, protected from robots, with files attached.
- Search in a view (Ctrl+F).
- Range selection, copying and pasting from Excel and Google Sheets, fill down, undo and redo.
- Import of tables and records from CSV and Excel, export of a view to CSV and Excel.
- Interfaces: pages of grids, lists, kanbans, record cards, forms to create and change records, numbers, texts, buttons and filters over a base — in rows and columns; sorting, a manual order of records and column widths in grids and lists; a form of a new record keeps to the filters of its element; buttons open a form and delete a record; a builder with layouts, an order of pages and fields, a preview on the real data, a draft that saves itself and its publication; access to a single interface without access to its base.
- Automations: up to five triggers — a record is created, changes, begins to meet a condition, comes from a form, a button of an interface is pressed; steps — update the record, create a record in another table, send an email or an HTTP request and take values of its answer into the next steps; a trial run on a record before turning on; a run log with running again and the reasons of failures in words; duplicating an automation.
- Copies of a table, a base and a workspace with their data, links, files and views.
- A whole record in its own window: press Space or click the row number.
- Changes by other people show up at once, without reloading the page.
- Russian and English interface, light and dark themes.
- REST API with an OpenAPI specification: access by API tokens with permissions and rate limits, service accounts for integrations.
- Delivered as a single executable and Docker Compose; works in a closed network; installation, update, rollback and restore of the database with one command of the installer; Debian 12 and Debian 13.
- Operations: a license with a trial, backups with a restore to any moment and a weekly drill, the administration panel of the installation, moving and upkeep, dashboards and alerts.
- Accessibility: screen readers and a zoom of the interface up to 200 %.
