---
title: "Fields"
description: "Every field has a type, and its icon is shown in the column header."
version: "v0.8.0"
lang: "en"
order: 5
---

Every field has a type, and its icon is shown in the column header.

- **Text and contacts:** single line text, long text, email, URL, phone number.
- **Numbers:** number, currency, percent, duration, rating.
- **Choices:** checkbox, single select, multiple select, user.
- **Dates:** date, date and time.
- **Links between tables:** link, lookup, count, rollup.
- **Calculations:** formula.
- **Files:** attachments.
- **Filled in by the system:** autonumber, created or last modified time, created or last modified by.

**A new field at the end of the table:** click **+** to the right of the last column, enter a name, choose a type and click **Create field**.

![A new field](img/new-field.png)

**The menu of a field:** click the header of its column.

![The menu of a field](img/field-menu.png)

- **Edit field** — a new name, the options of a list (one per line), the number of decimal places, or the text of a formula.
- **Insert field left** or **right** — a new field next to this one.
- **Make the primary field** — the field becomes the first column and the name of the record: its value is what links, the quick switcher and the record title show. A formula can be the primary field too.
- **Hide field** — the column disappears from this view; the data stays.
- **Delete field** — the field is deleted with all its values after you confirm. The primary field cannot be deleted.

**Default and validation** — a section of the **Edit field** window. The default goes into a new record: a text or a number, **Today** and **Now** for dates, **The one who creates the record** for a user field, **Checked** for a checkbox. Validation does not let a wrong value be saved: **At least** and **At most** for numbers, **Length from** and **Length up to** for text, **Pattern** — for example, `[A-Z]{2}-\d{3}` for a code like "AB-123". In **Message on error** write what the person should fix.

![Default and validation](img/field-rules.png)

**Change the type of the field** — a section of the same window. Choose the **New type**: xtab checks the values and shows whether all of them are kept or how many become empty, with examples. Click **Change the type**: the values move in the background, and the field cannot be changed meanwhile. A change of type cannot be undone — if important values do not convert, create a new field instead.

![Changing the type of a field](img/field-type.png)
