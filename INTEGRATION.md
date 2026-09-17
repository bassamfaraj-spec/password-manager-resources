# Secure Integration Guide

This repository publishes data and reference tooling. It is not a password
manager, credential store, service endpoint, or deployment artifact. A
consumer must provide the application, platform-specific integrations, and
operational controls.

## Consumption contract

- Fetch resources over HTTPS from a trusted, authenticated source.
- Pin a reviewed release or commit; do not consume an arbitrary branch.
- Verify the expected file set, JSON schemas, and resource version before
  activation.
- Keep credentials site-bound. Shared-credential entries may improve
  suggestions, but must never authorize filling or submission without the
  user's explicit review and consent.
- Treat all domains and URLs as untrusted input. Match registrable domains
  using a vetted URL parser and reject look-alikes, malformed URLs, and
  non-HTTPS change-password URLs unless the service demonstrably requires
  them.
- Import resources into an isolated, read-only representation. Do not allow
  resource data to execute as code or change application policy outside the
  documented integration points.

## Verification and rollout

Before release, a consumer should:

1. Run the repository's schema, sorting, parser, and converter checks.
2. Run application integration tests covering password generation, autofill,
   shared-credential suggestions, change-password navigation, and appended
   2FA codes.
3. Test staging and adversarial cases, including deceptive domains,
   cross-origin frames, redirects, malformed resource data, and unavailable
   update sources.
4. Sign and version the imported resource bundle, retain the previous known
   good bundle, and support atomic rollback.
5. Release progressively with audit logging, health metrics, alerts, and an
   owner for rollback decisions.

Resource updates must not contain secrets, user credentials, session tokens,
or personally identifying data. Store application secrets in the consumer's
secret-management system, never in this repository or generated bundles.
