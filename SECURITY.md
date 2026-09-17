# Security Policy

## Scope

This project contains public JSON resources and reference tooling for
password-manager integrations. It does not receive, store, or process user
credentials.

## Reporting a vulnerability

Do not open a public issue for a vulnerability or suspected secret. Report it
privately through GitHub's repository security advisory workflow. Include:

- the affected file, tool, or workflow;
- reproducible steps or a minimal proof of concept;
- the security impact and any suggested mitigation.

If private reporting is unavailable, contact the project maintainers through
the security contact listed in the repository's GitHub security settings.

## Resource safety

Contributors must not submit passwords, tokens, private keys, personal data,
or other secrets. Consumers should treat resource data as untrusted input,
validate it against the schemas, and preserve site-bound credential scoping
and explicit user consent.
