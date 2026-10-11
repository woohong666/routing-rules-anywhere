# Security

This repository is private, but it should still be treated as if any committed file could eventually be shared.

Do **not** commit:

- proxy subscription URLs
- node passwords
- UUIDs
- private keys
- certificates
- API keys
- cookies
- session tokens
- account credentials
- exported client configurations containing secrets

Recommended content:

- routing templates
- domain lists
- rule-set files
- documentation
- changelogs
- non-sensitive examples

If a secret is committed accidentally, remove it from the repository and rotate/revoke the secret immediately. Deleting only the latest file revision is not enough because Git history may retain it.
