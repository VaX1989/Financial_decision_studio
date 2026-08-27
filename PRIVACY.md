# Privacy

This document describes the privacy characteristics of Financial Decision Studio as actually implemented in the definitive release (`release/Financial_Decision_Studio.html`, version 3.0.0, build `FDS-DEFINITIVE-20260826`), based on inspection of that file. It does not describe hypothetical future behavior.

## Network activity

The definitive release contains **no `fetch`, `XMLHttpRequest`, `WebSocket`, remote script, remote stylesheet, remote font, or CDN reference** of any kind. There is no analytics, telemetry, or third-party API call anywhere in the file. Everything the application needs — markup, styles, and application logic — is embedded in the single HTML file, including its icon (an inline SVG data URI).

In practice, this means: once the HTML file is downloaded, the application does not need, and does not attempt, an internet connection to function. You can verify this yourself by opening the file with your browser's network/DevTools panel open — it should show no outgoing requests during normal use.

## Where your data lives

Financial Decision Studio keeps your financial data on your own device using standard browser storage mechanisms:

- **`localStorage`** — used for smaller pieces of application/session state.
- **`IndexedDB`** — used for larger structured data, such as your saved plan(s).

None of this data is transmitted anywhere by the application. It stays in your browser's local storage for the origin (or file context) you opened the app from.

### Browser-dependent behavior when opened via `file://`

Some browsers restrict or partition storage differently for pages opened directly from disk (`file://...`) versus pages served over `http(s)://`. Depending on your browser, storage under `file://` may be more limited, may not persist as reliably across sessions, or may behave inconsistently between browsers. See the user guide's "Local persistence" and "`file://` requires caution" sections for details and mitigations built into the app (checkpoints, exports, portable HTML).

### Session-only / Privacy mode

The application offers a mode that avoids writing plan data to persistent local storage at all, keeping it in memory for the current session only. See the user guide for exact behavior.

### Portable HTML and Encrypted Portable HTML

You can export your plan as a portable HTML file — including an encrypted variant protected by a password you choose — to move data between devices or keep an offline backup. The encryption (and its limitations, including what happens if you lose the password) is described in the user guide. Encrypted exports are processed locally in your browser; the application does not transmit them anywhere.

## What this project does not do

- It does not collect analytics or usage telemetry.
- It does not phone home to check for updates.
- It does not require an account, sign-in, or email address.
- It does not send your financial data, plan, or any derived information to the project maintainer, to GitHub, or to any third party as part of normal local use.

## Limits of this statement

This document reflects what the current release's code does and does not do, as inspected. It is not a guarantee of absolute privacy or security: your browser, operating system, extensions, or device could still affect how locally stored data is protected. If you download a modified or third-party copy of the software, this document may no longer apply — only the official release referenced above has been reviewed.
