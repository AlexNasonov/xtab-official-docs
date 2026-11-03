---
title: "Outgoing addresses"
description: "A page of the administrator of the organization (the menu of the account → Outgoing addresses): where automations may send requests and letters."
version: "v0.5.0"
lang: "en"
order: 27
---

A page of the administrator of the organization (the menu of the account → **Outgoing addresses**): where automations may send requests and letters. By default nowhere outside: letters go to members of the organization only.

- **Allowed hosts**, one a line: `api.example.com`, `*.example.com` (all subdomains) or an IP address. **Any host** opens every address; it asks for the password again.
- **Allowed addresses of letters**: addresses outside the organization automations may write to.
- **Domains of invitations**: when set, only addresses of these domains can be invited into the organization; letters of automations may go to them too.
