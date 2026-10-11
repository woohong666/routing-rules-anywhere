# routing-rules-anywhere

Private routing-rule templates for **Anywhere** on macOS.

## Current rules

- `anywhere/Meta-Fixed.arrs` — Meta family routing template
  - Facebook
  - Instagram
  - Threads
  - Messenger
  - WhatsApp
  - Meta AI / Llama
  - Quest / Oculus

## Usage

1. Import the required `.arrs` file into Anywhere.
2. Bind the imported rule set to the desired proxy/chain in the Anywhere UI.
3. Check for conflicts with Anywhere Built-in rules. Built-in rules can take priority over User rules, so conflicting Built-in service groups should normally be set to **Default** when a User rule is intended to take control.
4. Keep proxy credentials, subscription URLs, UUIDs, API keys, cookies, certificates, and other secrets out of this repository.

## Repository scope

This repository is intentionally **Anywhere-only**. NekoBox rules should be maintained separately.

## Versioning

Changes are recorded in `CHANGELOG.md`.

Current initial version: **v1.0.0**
