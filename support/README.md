# Payload feed

This repository publishes S928B-only profiles:

- `e3q-S928BXXS6DZF2`: `S928BXXS6DZF2`, original KernelSU v3.2.5.
- `e3q-S928BXXU5DZDP-ksunext`: `S928BXXU5DZDP`, KernelSU Next built from source.

Both use model `SM-S928B` and kernel version `6.1.145`.

`targets-v3.json` is the current feed. `targets-v2.json` remains for clients
that still use schema version 2. Both files contain only S928B profiles.
Artifact paths and target identity must stay in the same commit because clients
resolve the repository commit before downloading the payload.
