# Security Policy

## Reporting a Vulnerability

Do not open a public GitHub issue for security vulnerabilities.

Report vulnerabilities by emailing **security@buildbetter.com** (replace with actual address before publishing this repo). Include:

- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Any suggested mitigations

You will receive an acknowledgement within 2 business days. We aim to triage all reports within 5 business days and to communicate a remediation timeline within 10.

## Scope

The following are in scope:

- Authentication and authorization flaws
- Data exposure (content, user data, credentials)
- Injection vulnerabilities (SQL, command, template)
- Publishing pipeline abuse (unauthorized content publication)
- Asset access control bypass
- Privilege escalation within the platform

The following are out of scope:

- Denial of service
- Social engineering
- Issues in third-party dependencies (report those upstream; notify us if you believe the impact is critical)
- Issues in non-production environments

## Disclosure Policy

We follow coordinated disclosure. We ask that you:

1. Give us reasonable time to fix the issue before public disclosure
2. Make a good-faith effort not to access or modify data you do not own
3. Not perform testing that degrades service availability

We will credit security researchers in our changelog unless they request anonymity.

## Supported Versions

As a pre-release project, only the latest commit on `main` is supported.
