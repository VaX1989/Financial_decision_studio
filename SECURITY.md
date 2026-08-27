# Security Policy

Financial Decision Studio is a single, self-contained, offline-first HTML file with no server component and no runtime dependencies fetched over the network (see [`PRIVACY.md`](PRIVACY.md)). This limits its attack surface considerably, but reports are still welcome.

## Reporting a vulnerability

Please use GitHub's **[private vulnerability reporting](../../security/advisories/new)** for this repository rather than opening a public Issue, so that any real weakness isn't disclosed before a fix is available. (If private reporting is not enabled yet, or unavailable to you, open a regular Issue but omit exploit details until a maintainer responds and ask to move the conversation to a private channel.)

When reporting, please include:

- the release version, engine version, and build ID (shown in the app and in [`NOTICE.md`](NOTICE.md)),
- your browser and operating system,
- clear reproduction steps, and
- the potential impact, as you understand it.

## Please do not include personal financial data in reports

**Do not paste real account balances, real plan JSON exports, real portable HTML backups, or any other personal financial information into a vulnerability report, whether public or private.** If you need to demonstrate an issue, please reproduce it using anonymized or synthetic example data.

## Scope

In scope: the application code in `release/Financial_Decision_Studio.html`, and anything that could cause it to mishandle locally stored data, execute unintended code, or leak data off-device.

Out of scope: general questions about calculation results (please use a **Calculation / Model Discrepancy** issue instead — see the issue templates) and vulnerabilities in your own browser, operating system, or unrelated third-party software.

## Response

This is an independently maintained project. There is no guaranteed response time, but security reports are prioritized over feature requests.
