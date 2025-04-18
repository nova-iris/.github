# Security Policy

This is the security notice for all repositories under the Space and Time (SxT) organization. At SxT, we have a centralized security team that manages vulnerabilities across all projects. This team works closely with maintainers and contributors to triage and remediate reported issues promptly. We are committed to maintaining the security and integrity of our open source software.

## Reporting a Vulnerability
If you believe you have found a security vulnerability in any Space and Time owned repository, please report it to us through coordinated disclosure.

**Please do not report security vulnerabilities through public GitHub issues, discussions, or pull requests.**

Instead, please send an email to opensource-security@github.com.

Please include as much of the information listed below as you can to help us better understand and resolve the issue:

- The type of issue (e.g., buffer overflow, SQL injection, or cross-site scripting)
- Full paths of source file(s) related to the manifestation of the issue
- The location of the affected source code (tag/branch/commit or direct URL)
- Any special configuration required to reproduce the issue
- Step-by-step instructions to reproduce the issue
- Proof-of-concept or exploit code (if possible)
- Impact of the issue, including how an attacker might exploit the issue

This information will help us triage your report more quickly.

## Disclosure Policy
When the security team receives a security bug report, they will assign it to a primary handler. This person will coordinate the fix and release process, involving the following steps:

- Confirm the problem and determine the affected versions.
- Audit code to find any potential similar problems.
- Prepare fixes for all releases still under maintenance. These fixes will be released as fast as possible.

## Bug bounty
Unfortunately, SxT doesn't offer a paid bug bounty programme. SxT will make efforts to show appreciation to people who take the time and effort to disclose vulnerabilities responsibly. We do have `an acknowledgements page for legitimate issues found by researchers`.

## Comments on this Policy
If you have suggestions on how this process could be improved please submit a pull request.