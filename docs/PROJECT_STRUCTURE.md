# Project structure

- `src/targets/e3q-S928BXXS6DZF2/`: S928B firmware identity and P0 data.
- `artifacts/e3q-S928BXXS6DZF2/`: published exploit payload.
- `kernelsu/`: S928B module, `ksud`, patches, and build audit tools.
- `support/`: version 2 and version 3 feeds for S928B only.
- `docs/SM-S928B-S928BXXS6DZF2.md`: target-specific build record.

`build/` contains intermediate outputs and is not committed. The checked-in
binaries are the final S928B payloads consumed by Root My Galaxy.
