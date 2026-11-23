---
title: "Administering the organization"
description: "The administrator of the organization manages it in Administration of the account menu. The data of bases stays closed to the administrator until they have a role (see Access below)."
version: "v0.9.0"
lang: "en"
order: 33
---

The administrator of the organization manages it in **Administration** of the account menu. The data of bases stays closed to the administrator until they have a role (see Access below). Actions that change security ask for the password.

## Members

- **Invite**: enter the e-mail and the name — the person gets an invitation. Search the list by name or e-mail.
- Each member shows whether they are an administrator, whether they have a second factor, whether their password sign-in is locked after wrong passwords, and when they were last active.
- The buttons of a member: **Block** / **Unblock** (a block ends their sessions and tokens at once), **Make administrator** / **Remove administrator**, **End sessions and revoke tokens** (e.g. after a lost laptop), **Reset second factor** (when the person lost the phone and the codes), **Unlock sign-in**, **Send the invitation again**.

![Members](img/admin-users.png)

**External members** are marked "external". An external member sees in the lists of people only themselves and those who share workspaces and bases with them, creates no workspaces and invites nobody. xtab sets the mark when an administrator invites a person outside the domains of the organization; an administrator sets it with **Make external** and clears it with **Clear «external»**.

**Deletion on the request of the person.** Press **Delete on request**, type the e-mail of the account in the window that opens and press **Delete the account** (xtab asks for your password). The sessions and tokens of the person end at once. In a few seconds:

- the data of the account is exported to an archive — the person gets a link to it by e-mail (when mail is set up), and you download it in **Exports of account data** below (the archive is kept for a day, every download is written to the audit log);
- the account is anonymized: the name, the e-mail, the password, the second factor, the roles and the groups are erased, nobody can sign in to it, and its e-mail can be invited again;
- values in tables and the audit log stay under the name "Deleted user #N".

A deletion cannot be undone. You cannot delete yourself — another administrator does it.

![Deleting an account](img/admin-delete.png)

![Exports of account data](img/admin-exports.png)

## Groups

- Enter a name and press **Create a group**.
- **Members** opens who is in the group: add a person by e-mail or name, the cross takes them out. If you add yourself to a group that has roles, xtab asks for your password.
- **Rename** and **Delete** are on each group. Deleting a group also removes the access it gave.
- A group can follow a group of the sign-in provider (see SSO sign-in): its members are then updated at every sign-in.

![Groups](img/user-groups.png)

## Access

Every workspace and base of the organization with the roles of people and groups. When a base has no owner left, or you need to work with its data, press **Give myself** and choose a role — the owners get a letter and the audit log records it. **Make owner** hands a base over to another person.

## Policies

- **Passwords and the lockout**: the length and the make-up of a password, no reuse of old ones, how long it works, the lockout after wrong attempts, the number of sessions of one person at once (10 by default: a sign-in beyond it ends the oldest session). A new password is also checked against a list of breached ones.
- **Second factor of administrators**: **Ask administrators for a second factor** or **Ask everyone for a second factor** (until a person sets up a second factor, only the profile works for them) and **Count only a passkey**.
- **Public links**: whether public links to forms are allowed.
- **Browser metrics**: whether the browsers of your people tell the server of your installation how fast the interface works: the load time, the smoothness of scrolling and the delay of input. Only anonymous counters are sent, and they go nowhere but this server.
- **Automations**: how many days (7 to 365) the run log keeps each run with its steps; older runs are deleted once an hour.
- **Outgoing addresses**: where automations may send requests and letters (see Outgoing addresses).
- **Invitations**:
  - **Domains of invitations**: the domains of your organization. Managers of members invite only from these domains. An administrator of the organization may also invite a person from another domain — a contractor, say: such a member becomes external (see "Members"). Letters of automations may go to these domains.
  - **Only administrators invite**: only administrators invite new people into the organization, while managers of workspaces and bases give roles to those already in it.

Each part of the page has its own button **Save**: it saves only the settings of that part.

The policy of API tokens is set on the page of API tokens.

## SSO sign-in

The OpenID Connect providers of the organization: **Add a provider**, enter the name of the sign-in button, the issuer, the client id and its secret. Register the **redirect address** and the **logout address** shown on the page at the provider. **Check** makes sure the provider answers. Turn on **The provider confirms a second factor** only when the provider itself asks administrators for a second factor: a sign-in through it then replaces the second factor of xtab when the provider says so. By default an administrator passes the second factor of xtab after a sign-in through a provider. Below are the groups of the organization that follow groups of the provider, and the lifetime of a session opened through a provider.

## Audit log

Who did what and when in the organization: sign-ins, changes of rights and policies, exports, actions of administrators. Choose events by action, person and time and press **Show**; **Download CSV** saves what is chosen (xtab asks for the password; the download is in the log too).

The records are sealed into a chain: each is tied to the previous one, the checkpoints are signed. **Chain of seals** shows the last seal and the last check — if a record was changed or deleted in the database, the check finds it and an alert comes. Here are also how long the log stays in the database (older months go to the archive), the thresholds of the alerts and the delivery to SIEM.

![Audit log](img/admin-audit.png)

## Alerts

Without a separate monitoring system xtab itself tells about suspicious events: an administrator gave themselves access, a mass export, a token from a new network, a spike of denied access, mass lockouts of accounts, a reset of the second factor of an administrator, the mandatory second factor turned off, a broken chain of the log. The administrators get a letter; mark what you handled with **Handled** in the feed.

![Alerts](img/admin-alerts.png)

## Permission matrix and settings

**Permission matrix** shows what each role may do in the installed version. **Organization settings** hold the name, the time zone and the language of the organization; a new time zone or language recounts the formulas with dates and texts, and the page shows how far it got.

## Instance

The **Instance** tab of Administration is shown to the administrator of the whole xtab installation (the administrator of the server makes one) and opens only with a second factor connected.

- **Alerts** — what needs attention: the term of the license, a full backup not taken for long, a restore not checked, background jobs that failed.
- **License** — its state (trial, valid, grace period, read-only), term and quotas. Choose the license file from the supplier with **Choose a file** and install it with **Install**; the nodes apply it within 5 minutes.
- **Backups** — the last full backups and segments of the database log, when a restore was last checked and how long it took.
- **Background migrations and jobs** — changes of field types and the queue of background jobs.

![Instance](img/admin-instance.png)

**Instance settings** — mail, limits, logs, rules of sign-in and passwords, backups, the **announcement** — the text of a banner above the pages of every user, the sign-in page included, with the time it starts and ends (about planned maintenance, say); people see it within a minute. Changes apply on all nodes without a restart; **Reset** returns the value of the server's settings or the default.

![Instance settings](img/admin-instance-settings.png)

![The announcement above the page](img/announcement.png)

**The license for everyone.** Shortly before the license or the trial ends, a warning shows above the page. When the term and the grace period are over, the data stays available for reading and export, but not for changes, until an administrator installs a new license.
