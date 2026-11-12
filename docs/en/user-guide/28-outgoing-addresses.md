---
title: "Outgoing addresses"
description: "A page of the administrator of the organization (the menu of the account → Outgoing addresses): where automations may send requests and letters."
version: "v0.8.0"
lang: "en"
order: 28
---

A page of the administrator of the organization (the menu of the account → **Outgoing addresses**): where automations may send requests and letters. By default nowhere outside: letters go to members of the organization only.

- **Allowed hosts**, one a line: `api.example.com`, `*.example.com` (all subdomains) or an IP address. **Any host** opens every address; it asks for the password again.
- **Allowed addresses of letters**: addresses outside the organization automations may write to.
- **Domains of invitations**: the domains of your organization. Managers of members invite only from these domains. An administrator of the organization may also invite a person from another domain — a contractor, say: such a member becomes external (see "Members"). Letters of automations may go to these domains.
- **Only administrators invite**: only administrators invite new people into the organization, while managers of workspaces and bases give roles to those already in it.
- **Keep the run log, days**: how many days the run log of automations is kept, from 7 to 365.
