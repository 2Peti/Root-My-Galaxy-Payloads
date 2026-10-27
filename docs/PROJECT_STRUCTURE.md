# Project structure

- `src/targets/`: S928B DZF2 and U5DZDP identities and P0 data.
- `artifacts/`: source-built S928B exploit payloads.
- `kernelsu/`: original S928B KernelSU v3.2.5 module, `ksud`, patches, and audit tools.
- `kernelsu-next/`: source-built S928B U5DZDP KernelSU Next module and `ksud`.
- `support/`: version 2 and version 3 feeds for S928B only.
- `docs/SM-S928B-S928BXXS6DZF2.md` and
  `docs/SM-S928B-S928BXXU5DZDP.md`: target-specific build records.

`build/` contains intermediate outputs and is not committed. The checked-in
binaries are the final S928B payloads consumed by Root My Galaxy.
