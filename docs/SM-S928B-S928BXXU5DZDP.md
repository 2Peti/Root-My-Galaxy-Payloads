# SM-S928B / S928BXXU5DZDP

## Device identity

- Model: `SM-S928B`
- Firmware: `S928BXXU5DZDP`
- Build: `BP4A.251205.006.S928BXXU5DZDP`
- Fingerprint: `samsung/e3qxeea/e3q:16/BP4A.251205.006/S928BXXU5DZDP:user/release-keys`
- Kernel: `6.1.145-android14-11-33419968-abS928BXXU5DZDP`
- `uname -v`: `#1 SMP PREEMPT Thu Apr 23 07:39:47 UTC 2026`

## Built payloads

| Artifact | Size | SHA-256 |
| --- | ---: | --- |
| `artifacts/e3q-S928BXXU5DZDP/cve-2026-43499-app.so` | 104,128 | `a539a433305aa4225561f77714123fe5c50ab8ebf9361982cf3a30dcb3b95e57` |
| `kernelsu-next/android14-6.1_ksunext-e3q-S928BXXU5DZDP-kdp.ko` | 577,904 | `35d4f29b7bb47ed11a48fc6d6b9c30afc4a38bf58a8ec4a366d22f8587e74c0c` |
| `kernelsu-next/ksud-e3q-S928BXXU5DZDP-kernelsu-next` | 4,199,720 | `d2bd9be09880da3922d5d43905271d9fb02a59fb4ddb5d54303f6e8ed8d2652c` |

The exploit was compiled from the S928B source target profile, using the same
device-tested offsets and P0 fingerprints. The KernelSU Next module passed the
DDK `check_symbol` step, but the DDK kernel tree is 6.1.166 rather than the
phone's 6.1.145 build. Exact U5DZDP `vmlinux`/`Module.symvers` validation and
hardware testing remain pending. See [`../kernelsu-next/README.md`](../kernelsu-next/README.md).
