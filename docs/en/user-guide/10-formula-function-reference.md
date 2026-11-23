---
title: "Formula function reference"
description: "Function names are in English, arguments are separated by commas, fields go in braces and texts in double quotes. Square brackets mark the arguments you may leave out."
version: "v0.9.0"
lang: "en"
order: 10
---

Function names are in English, arguments are separated by commas, fields go in braces and texts in double quotes. Square brackets mark the arguments you may leave out.

**Operators:**

- `+`, `-`, `*`, `/` — arithmetic on numbers: `{Price} * {Quantity}`; the function `DATEADD` moves dates;
- `&` — joins texts: `{Name} & " — " & {Quantity}`;
- `=`, `!=` (or `<>`), `<`, `<=`, `>`, `>=` — comparisons, true or false: `{Price} > 1000`;
- parentheses set the order: `({Price} + 100) * 2`.


The results of the examples are for a record where {Name} is «Oak table», {Price} is 1234.5, {Quantity} is 3, {Date} is March 13, 2026, {Deadline} is March 20, 2026, 15:30, {Tags} are «Urgent» and «Important», {Done} is checked, {Scores} is a lookup of 4, 5 and 3, {Data} is a JSON text; today is March 16, 2026, 12:00 in Moscow. Numbers and dates of the results are written plainly: the table shows them in the format of your language.

## Logic and errors

| Function | What it does | Example | Result |
|---|---|---|---|
| `AND(condition1, condition2, …)` | true when every condition is true | `AND({Done}, {Price} > 1000)` | `TRUE`, checkbox |
| `BLANK()` | a blank value | `IF({Done}, BLANK(), {Price})` | (blank), number |
| `ERROR([text])` | an error value | `IF({Price} > 1000, ERROR("check the price"), {Price})` | `#USER`, number |
| `FALSE()` | false | `FALSE()` | `FALSE`, checkbox |
| `IF(condition, then, [else])` | one value when the condition is true, another when it is not | `IF({Price} > 1000, "expensive", "cheap")` | `expensive`, text |
| `IFERROR(value, fallback)` | the value, or the fallback when it is an error | `IFERROR({Price} / 0, 0)` | `0`, number |
| `IFS(condition1, value1, …)` | the value of the first true condition | `IFS({Quantity} > 5, "many", {Quantity} > 0, "some")` | `some`, text |
| `ISBLANK(value)` | true when the value is blank | `ISBLANK({Name})` | `FALSE`, checkbox |
| `ISERROR(value)` | true when the value is an error | `ISERROR({Price} / 0)` | `TRUE`, checkbox |
| `LET(name1, value1, …, expression)` | an expression with named intermediate values | `LET(x, {Price} * 1.2, ROUND(x, 0))` | `1481`, number |
| `NOT(condition)` | true when the condition is false | `NOT({Done})` | `FALSE`, checkbox |
| `OR(condition1, condition2, …)` | true when any condition is true | `OR({Quantity} > 5, {Done})` | `TRUE`, checkbox |
| `SWITCH(expression, pattern1, result1, …, [default])` | the result of the first pattern equal to the expression | `SWITCH({Quantity}, 1, "one", 3, "three", "other")` | `three`, text |
| `TRUE()` | true | `TRUE()` | `TRUE`, checkbox |
| `XOR(condition1, condition2, …)` | true when an odd number of conditions is true | `XOR({Done}, {Price} > 1000)` | `FALSE`, checkbox |

## Numbers and rounding

| Function | What it does | Example | Result |
|---|---|---|---|
| `ABS(number)` | the absolute value of a number | `ABS(-{Price})` | `1234.5`, number |
| `CEILING(number, [significance])` | rounds up to a multiple (by default 1) | `CEILING({Price}, 100)` | `1300`, number |
| `EVEN(number)` | rounds away from zero to an even number | `EVEN({Quantity})` | `4`, number |
| `EXP(number)` | e to the power of a number | `EXP(1)` | `2.71828182845905`, number |
| `FLOOR(number, [significance])` | rounds down to a multiple (by default 1) | `FLOOR({Price}, 100)` | `1200`, number |
| `INT(number)` | the whole part, rounded down | `INT(-2.5)` | `-3`, number |
| `LOG(number, [base])` | the logarithm to a base (by default 10) | `LOG(1000)` | `3`, number |
| `MOD(number, divisor)` | the remainder of a division | `MOD({Price}, 100)` | `34.5`, number |
| `MROUND(number, multiple)` | rounds to the nearest multiple | `MROUND({Price}, 50)` | `1250`, number |
| `ODD(number)` | rounds away from zero to an odd number | `ODD(2)` | `3`, number |
| `PI()` | the number π | `PI()` | `3.141592653589793`, number |
| `POWER(number, power)` | a number to a power | `POWER({Quantity}, 2)` | `9`, number |
| `ROUND(number, [places])` | rounds to places after the point, a half away from zero | `ROUND({Price} * 1.2, 1)` | `1481.4`, number |
| `ROUNDDOWN(number, [places])` | rounds towards zero to places after the point | `ROUNDDOWN({Price}, -2)` | `1200`, number |
| `ROUNDUP(number, [places])` | rounds away from zero to places after the point | `ROUNDUP({Price}, 0)` | `1235`, number |
| `SIGN(number)` | the sign of a number: −1, 0 or 1 | `SIGN(-{Quantity})` | `-1`, number |
| `SQRT(number)` | the square root | `SQRT(16)` | `4`, number |
| `TRUNC(number, [places])` | drops the places after the point | `TRUNC(-2.5)` | `-2`, number |
| `VALUE(text)` | a number read from a text | `VALUE("12.5") * {Quantity}` | `37.5`, number |

## Aggregates and statistics

| Function | What it does | Example | Result |
|---|---|---|---|
| `AVERAGE(number1, number2, …)` | the arithmetic mean, blanks left out | `AVERAGE({Scores})` | `4`, number |
| `COUNT(value1, value2, …)` | how many of the values are numbers | `COUNT({Price}, {Name}, 5)` | `2`, number |
| `COUNTA(value1, value2, …)` | how many of the values are not blank | `COUNTA({Name}, BLANK(), 5)` | `2`, number |
| `COUNTALL(value1, value2, …)` | how many values, blanks too | `COUNTALL({Name}, BLANK(), 5)` | `3`, number |
| `MAX(number1, number2, …)` | the largest of the numbers | `MAX({Price}, 1000)` | `1234.5`, number |
| `MEDIAN(number1, number2, …)` | the median of the numbers | `MEDIAN(1, {Quantity}, 10)` | `3`, number |
| `MIN(number1, number2, …)` | the smallest of the numbers | `MIN({Scores})` | `3`, number |
| `PERCENTILE(numbers, k)` | the percentile of the numbers of a list, k from 0 to 1, interpolated | `PERCENTILE({Scores}, 0.5)` | `4`, number |
| `STDEV.P(number1, number2, …)` | the standard deviation of a population | `STDEV.P(2, 4, 6)` | `1.63299316185545`, number |
| `STDEV.S(number1, number2, …)` | the standard deviation of a sample | `STDEV.S(2, 4, 6)` | `2`, number |
| `SUM(number1, number2, …)` | the sum of the numbers | `SUM({Price}, 100, {Quantity})` | `1337.5`, number |

## Text

| Function | What it does | Example | Result |
|---|---|---|---|
| `CONCATENATE(text1, text2, …)` | texts joined into one, as the & operator | `CONCATENATE({Name}, " — ", {Quantity}, " pcs")` | `Oak table — 3 pcs`, text |
| `ENCODE_URL_COMPONENT(text)` | a text for a part of a web address: a space is %20 | `ENCODE_URL_COMPONENT("a b&c")` | `a%20b%26c`, text |
| `LEFT(text, count)` | the first characters of a text | `LEFT({Name}, 3)` | `Oak`, text |
| `LEN(text)` | the number of characters of a text | `LEN({Name})` | `9`, number |
| `LOWER(text)` | the text in lower case | `LOWER({Name})` | `oak table`, text |
| `MID(text, start, count)` | characters of a text from a start position, from 1 | `MID({Name}, 5, 3)` | `tab`, text |
| `PROPER(text)` | each word with a capital letter | `PROPER("table of oak")` | `Table Of Oak`, text |
| `REPLACE(text, start, count, with)` | a part of a text from a start position replaced with another text | `REPLACE({Name}, 5, 5, "chest")` | `Oak chest`, text |
| `REPT(text, times)` | a text repeated some times | `REPT("★", {Quantity})` | `★★★`, text |
| `RIGHT(text, count)` | the last characters of a text | `RIGHT({Name}, 5)` | `table`, text |
| `SUBSTITUTE(text, what, with, [occurrence])` | occurrences of a text replaced with another text (or only the numbered one) | `SUBSTITUTE({Name}, "Oak", "Pine")` | `Pine table`, text |
| `T(value)` | the value when it is a text, blank otherwise | `T({Name})` | `Oak table`, text |
| `TEMPLATE(template, value1, …)` | a text by a template with places {1}, {2}… | `TEMPLATE("{1}: {2} pcs", {Name}, {Quantity})` | `Oak table: 3 pcs`, text |
| `TEXTAFTER(text, separator, [occurrence])` | the text after a separator | `TEXTAFTER({Name}, " ")` | `table`, text |
| `TEXTBEFORE(text, separator, [occurrence])` | the text before a separator | `TEXTBEFORE({Name}, " ")` | `Oak`, text |
| `TEXTSPLIT(text, separator)` | the parts of a text as an array | `TEXTSPLIT({Name}, " ")` | `Oak, table`, list of texts |
| `TRIM(text)` | the text without spaces at its start and end | `TRIM("  oak  ")` | `oak`, text |
| `UPPER(text)` | the text in upper case | `UPPER({Name})` | `OAK TABLE`, text |

## Search and regular expressions

| Function | What it does | Example | Result |
|---|---|---|---|
| `FIND(what, where, [from])` | the position of a text in a text, case matters, from 1; 0 — not found | `FIND("table", {Name})` | `5`, number |
| `REGEX_EXTRACT(text, pattern)` | the first match of a regular expression; the server computes it | `REGEX_EXTRACT("Order 42", "[0-9]+")` | `42`, text |
| `REGEX_MATCH(text, pattern)` | true when the text matches a regular expression; the server computes it | `REGEX_MATCH({Name}, "table$")` | `TRUE`, checkbox |
| `REGEX_REPLACE(text, pattern, replacement)` | every match of a regular expression replaced; the server computes it | `REGEX_REPLACE({Name}, " ", "_")` | `Oak_table`, text |
| `SEARCH(what, where, [from])` | the position of a text in a text, case ignored, from 1; 0 — not found | `SEARCH("TABLE", {Name})` | `5`, number |
| `SIMILARITY(text1, text2)` | how alike two texts are, from 0 to 1; the server computes it | `SIMILARITY({Name}, "Oak table")` | `1`, number |
| `TEXT_MATCH(text, words, [language])` | true when the text has the words in any form; the server computes it | `TEXT_MATCH("Tables of oak", "table")` | `TRUE`, checkbox |

## Dates and times

| Function | What it does | Example | Result |
|---|---|---|---|
| `DATEADD(date, count, unit)` | a date moved by a count of units: "days", "months", "hours"… | `DATEADD({Date}, 10, "days")` | `2026-03-23`, date |
| `DATETIME_DIFF(date1, date2, [unit])` | the difference of dates in units: date1 − date2 (by default in seconds) | `DATETIME_DIFF({Deadline}, {Date}, "days")` | `7`, number |
| `DATETIME_FORMAT(date, [format])` | a date as a text by a Moment.js format: "DD.MM.YYYY" | `DATETIME_FORMAT({Date}, "MM/DD/YYYY")` | `03/13/2026`, text |
| `DATETIME_PARSE(text, [format])` | a date read from a text by a Moment.js format or ISO 8601 | `DATETIME_PARSE("03/13/2026", "MM/DD/YYYY")` | `2026-03-13`, date |
| `DAY(date)` | the day of the month, 1–31 | `DAY({Date})` | `13`, number |
| `EDATE(date, months)` | the same date some months later, moved to the last day of a short month | `EDATE({Date}, 1)` | `2026-04-13`, date |
| `EOMONTH(date, months)` | the last day of the month some months later | `EOMONTH({Date}, 0)` | `2026-03-31`, date |
| `HOUR(date)` | the hour, 0–23 | `HOUR({Deadline})` | `15`, number |
| `ISOWEEKNUM(date)` | the week number by ISO 8601, weeks from Monday | `ISOWEEKNUM({Date})` | `11`, number |
| `IS_AFTER(date1, date2)` | true when the first date is later than the second | `IS_AFTER({Date}, TODAY())` | `FALSE`, checkbox |
| `IS_BEFORE(date1, date2)` | true when the first date is earlier than the second | `IS_BEFORE({Date}, {Deadline})` | `TRUE`, checkbox |
| `IS_SAME(date1, date2, [unit])` | true when the dates are the same up to a unit | `IS_SAME({Date}, {Deadline}, "month")` | `TRUE`, checkbox |
| `MINUTE(date)` | the minute, 0–59 | `MINUTE({Deadline})` | `30`, number |
| `MONTH(date)` | the month, 1–12 | `MONTH({Date})` | `3`, number |
| `NOW()` | the current date and time; recounted every hour | `NOW()` | `2026-03-16 12:00`, date and time |
| `SECOND(date)` | the second, 0–59 | `SECOND({Deadline})` | `0`, number |
| `SET_TIMEZONE(date, zone)` | a date in another time zone: "Asia/Vladivostok" | `HOUR(SET_TIMEZONE({Deadline}, "Asia/Vladivostok"))` | `22`, number |
| `TODAY()` | today's date in the zone of the organization; recounted at midnight | `TODAY()` | `2026-03-16`, date |
| `WEEKDAY(date, [week start])` | the day of the week: 0 is Sunday | `WEEKDAY({Date})` | `5`, number |
| `WEEKNUM(date, [week start])` | the week number of the year, weeks from Sunday | `WEEKNUM({Date})` | `11`, number |
| `YEAR(date)` | the year | `YEAR({Date})` | `2026`, number |

## Business days

| Function | What it does | Example | Result |
|---|---|---|---|
| `NETWORKDAYS.INTL(date1, date2, [weekend], [holidays])` | the working days between dates with weekend days of one's own | `NETWORKDAYS.INTL({Date}, DATEADD({Date}, 6, "days"), 11)` | `6`, number |
| `WORKDAY(date, days, [holidays])` | the date some working days later | `WORKDAY({Date}, 5)` | `2026-03-20`, date |
| `WORKDAY.INTL(date, days, [weekend], [holidays])` | the date some working days later with weekend days of one's own | `WORKDAY.INTL({Date}, 1, 11)` | `2026-03-14`, date |
| `WORKDAY_DIFF(date1, date2, [holidays])` | the working days between dates | `WORKDAY_DIFF({Date}, DATEADD({Date}, 14, "days"))` | `11`, number |

## Lists

| Function | What it does | Example | Result |
|---|---|---|---|
| `ARRAYCOMPACT(array)` | the array without blank values | `ARRAYCOMPACT(TEXTSPLIT("a,,b", ","))` | `a, b`, list of texts |
| `ARRAYFLATTEN(array)` | nested arrays as one array | `ARRAYFLATTEN({Tags})` | `Urgent, Important`, list of texts |
| `ARRAYJOIN(array, [separator])` | the items of an array as one text with a separator (by default «, ») | `ARRAYJOIN({Tags}, "; ")` | `Urgent; Important`, text |
| `ARRAYSLICE(array, start, [end])` | a part of an array from the start position to the end one, from 1 | `ARRAYSLICE({Tags}, 2)` | `Important`, list of texts |
| `ARRAYSORT(array, [descending])` | the array in ascending or descending order | `ARRAYSORT({Tags})` | `Important, Urgent`, list of texts |
| `ARRAYUNIQUE(array)` | the array without repeated items | `ARRAYUNIQUE(TEXTSPLIT("a,b,a", ","))` | `a, b`, list of texts |
| `ARRAY_INTERSECT(array1, array2)` | the items both arrays have | `ARRAY_INTERSECT({Tags}, TEXTSPLIT("Important,Later", ","))` | `Important`, list of texts |
| `HAS_ALL(array, value1, …)` | true when the array has every value | `HAS_ALL({Tags}, "Urgent", "Later")` | `FALSE`, checkbox |
| `HAS_ANY(array, value1, …)` | true when the array has any of the values | `HAS_ANY({Tags}, "Urgent", "Later")` | `TRUE`, checkbox |

## The record

| Function | What it does | Example | Result |
|---|---|---|---|
| `CREATED_BY()` | the name of the author of the record | `CREATED_BY()` | `Anna`, text |
| `CREATED_TIME()` | when the record was created | `CREATED_TIME()` | `2026-03-02 10:00`, date and time |
| `LAST_MODIFIED_BY()` | the name of who last changed the record | `LAST_MODIFIED_BY()` | `Boris`, text |
| `LAST_MODIFIED_TIME()` | when the record was last changed | `LAST_MODIFIED_TIME()` | `2026-03-13 18:20`, date and time |

## JSON

| Function | What it does | Example | Result |
|---|---|---|---|
| `JSON_ARRAY_LENGTH(json, [path])` | how many items a JSON array has; the server computes it | `JSON_ARRAY_LENGTH({Data}, "$.items")` | `3`, number |
| `JSON_VALUE(json, path)` | the value at a path of a JSON as a text: "$.client.inn"; the server computes it | `JSON_VALUE({Data}, "$.client.inn")` | `7700000000`, text |

## Error codes

When a formula cannot be computed for a record, the cell shows an error code. ISERROR and IFERROR catch it.

| Code | What it means |
|---|---|
| `#DIV_ZERO` | division by zero |
| `#VALUE` | a value of the wrong kind: VALUE("abc") |
| `#NUM` | a number out of range, or an argument the function does not take |
| `#TOO_LONG` | a text longer than a long text may be |
| `#FIELD_DELETED` | a field the formula reads was deleted or changed its type |
| `#USER` | the error the function ERROR gave |
| `#NOT_FOUND` | only in automations: the answer of the step has no such path |


## Excel functions that are missing, and what to use instead

| Excel functions | Instead |
|---|---|
| `VLOOKUP`, `XLOOKUP`, `INDEX` and `MATCH` | A link to the other table and a lookup |
| `SUMIF(S)`, `COUNTIF(S)`, `AVERAGEIF(S)` | A rollup with **Only the linked records where** |
| `RAND`, `RANDBETWEEN` | None: the value of a formula must not change at every recount |
| `INDIRECT`, `OFFSET`, `ROW`, `COLUMN` | References to fields in braces |
| `LAMBDA`, `MAP`, `FILTER`, `SORT` | `LET`, `ARRAYSORT`, a rollup with a condition |
| `WEBSERVICE` | An automation with an «HTTP request» step |
| `ISNUMBER`, `ISTEXT` | Not needed: the type of a value is checked when the formula is saved |
