---
title: "Account security"
description: "You set up your own account in the profile: the circle with your initials → Profile."
version: "v0.9.0"
lang: "en"
order: 32
---

You set up your own account in the profile: **the circle with your initials → Profile**.

## Profile

- **Photo**: JPEG, PNG or WebP up to 1 MB; every member of the organization sees it. **Remove the photo** brings the initials back.
- **Name** and the **time zone** — press **Save**. For now dates are shown in the time zone of the browser. Formulas count in the time zone of the organization.
- **Password**: enter the current one and the new one. Your other sessions end when it changes.
- **E-mail**: enter the new address and your password and press **Send the letter**. The address changes when you open the link of the letter; the old address gets a notice.

## Sign-in with a code

A second factor protects the account even if the password is known to someone else. Administrators of the organization usually must have one: until it is set up, their administrator rights do not work and a warning is shown at the top of the page with the link **Set it up in the profile**, which opens the profile right at **Sign-in with a code**. xtab leads such an administrator there after signing in and after accepting an invitation too. When the policy of the organization asks everyone for a second factor, only the profile works until it is set up: tables, attachments and interfaces open once the second factor is set up.

1. In **Sign-in with a code**, press **Add an app** (xtab asks for your password).
2. Scan the QR code with an authenticator app on your phone (Google Authenticator, Yandex Key and others) or type the key in by hand.
3. Enter the code from the app and press **Turn on**.
4. Keep the **recovery codes** in a safe place — they are shown only once. Each code works once when the phone is not at hand.

![Setting up an authenticator app](img/second-factor-setup.png)

From now on xtab asks for a code from the app after the password. No access to the app — press **No access to the app? Sign in with a recovery code**.

![The code at sign-in](img/second-factor-login.png)

After ten wrong codes in a row signing in with a code is locked, so nobody guesses the code even knowing the password. An administrator of the organization lifts it: **Reset second factor** in **Members**; then connect the app again.

**Passkeys** sign you in without a password and a code: the phone or the computer checks your fingerprint, face or PIN. Press **Add a passkey** and follow the browser; the sign-in page gets the button **Sign in with a passkey**.

## Sign-in through a provider

If the organization connected its corporate sign-in (Active Directory, Keycloak and others), the sign-in page has a button **Sign in with …**. To sign in this way to an account you already have, press **Bind** in **Sign-in through a provider** of the profile, confirm with your password or a passkey and sign in at the provider. **Unbind** removes the binding; the last way to sign in cannot be unbound.

## Sessions

**Sessions** shows where your account is signed in: the browser, the system, the address and when the session was last active; the current one is marked "this session". End a session you do not know with **End** and change your password. **End all others** keeps only the current one.

![Sessions](img/sessions.png)

## My data

Press **Export my data** (xtab asks for your password): in a few seconds a ZIP archive is ready with your profile, groups and roles, sessions, API tokens without their values and the audit events about you. Press **Download the archive**; when the organization has mail set up, a link to the archive also comes by e-mail. The archive is kept for a day.

![Exporting one's own data](img/data-export.png)
