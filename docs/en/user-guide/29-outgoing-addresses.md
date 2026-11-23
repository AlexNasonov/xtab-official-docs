---
title: "Outgoing addresses"
description: "A part of the page of the administrator of the organization Administration → Policies: where automations may send requests and letters."
version: "v0.9.0"
lang: "en"
order: 29
---

A part of the page of the administrator of the organization **Administration → Policies**: where automations may send requests and letters. By default nowhere outside: letters go to members of the organization only. The button **Save** of this part saves the changes.

- **Allowed hosts**, one a line: `api.example.com`, `*.example.com` (all subdomains) or an IP address. **Any host** opens every address; it asks for the password again.
- **Allowed addresses of letters**: addresses outside the organization automations may write to.

Letters of automations also go to the **domains of invitations**, set in the part **Invitations** of the same page (see Policies in Administering the organization).
