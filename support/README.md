# Payload feed

This repository publishes one payload: `e3q-S928BXXS6DZF2` for model
`SM-S928B`, firmware `S928BXXS6DZF2`, and kernel
`6.1.145-android14-11-33419968-abS928BXXS6DZF2`.

`targets-v3.json` is the current feed. `targets-v2.json` remains for clients
that still use schema version 2. Both files contain only the S928B profile.
Artifact paths and target identity must stay in the same commit because clients
resolve the repository commit before downloading the payload.
