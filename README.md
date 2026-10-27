# Root My Galaxy Payloads — SM-S928B DZF2 / U5DZDP

This repository contains only SM-S928B payloads. It keeps the original
`S928BXXS6DZF2` KernelSU v3.2.5 build and adds a source-built KernelSU Next
variant for tested firmware `S928BXXU5DZDP`.

The support feed exposes one profile per firmware/KernelSU variant. Root My
Galaxy fetches the exploit payload and `ksud` from `support/targets-v3.json`.
Final payloads stay in the repository; intermediate build output does not.

## Original KernelSU v3.2.5 — DZF2

- Exploit payload: `artifacts/e3q-S928BXXS6DZF2/cve-2026-43499-app.so`
- KernelSU module: `kernelsu/android14-6.1_kernelsu-e3q-S928BXXS6DZF2-kdp.ko`
- Late-load binary: `kernelsu/ksud-e3q-S928BXXS6DZF2-kdp`
- Patch stack: Samsung KDP/RKP/DEFEX, upstream mount-hide commit, and the
  Samsung SELinux Hide kretprobe fallback.

## KernelSU Next — U5DZDP

- Exploit payload: `artifacts/e3q-S928BXXU5DZDP/cve-2026-43499-app.so`
- KernelSU Next module and late-load binary: `kernelsu-next/`
- Built from source commit `1a65590d32cfb764bdccb44ec098b660d6c48808`; no
  PR #408 binaries are used.
- Mount Hide remains available in the original KernelSU v3.2.5 variant. The
  KernelSU Next source includes SELinux Hide but does not include Mount Hide.

In the original KSU v3.2.5 variant, Mount Hide and SELinux Hide initialize
enabled. Mount Hide filters proc
mount-table views. It does not hide ordinary files. Root My Galaxy removes its
staged helper, exploit payload, and `ksud` copies after an install attempt.
SELinux Hide filters SELinuxFS query/status results; `/proc/self/attr/current`
writes remain unchanged.

## Build the exploit payload

```sh
make TARGET=e3q-S928BXXS6DZF2 ANDROID_NDK_HOME=/path/to/android-ndk stable
```

The release payloads are padded to 104,128 bytes. Keep generated `build/`
output out of the repository; commit only final S928B payload artifacts.

The U5DZDP exploit uses the same device-tested S928B offsets and is built with
`TARGET=e3q-S928BXXU5DZDP`. See [`kernelsu-next/README.md`](kernelsu-next/README.md)
for the alternate KernelSU build and its validation limits.

## KernelSU source and attribution

KernelSU v3.2.5 is based on commit
`b0bc817b4e966aa6aa830834eaf6ef765d821d40`. The mount-hide patch derives from
[JingMatrix's upstream commit 80a3ab31](https://github.com/JingMatrix/KernelSU/commit/80a3ab31eb108a5515ecaea0f4799a035b7d1ce1).
The exploit payload is based on
[NebuSec's CVE-2026-43499 source](https://github.com/NebuSec/CyberMeowfia/tree/main/IonStack/CVE-2026-43499/exploit).
Root My Galaxy is by [BuSung-dev](https://github.com/BuSung-dev/Root-My-Galaxy).
See [CREDITS.md](CREDITS.md) for attribution and upstream links.

## Documentation

- [S928B DZF2 build and validation record](docs/SM-S928B-S928BXXS6DZF2.md)
- [S928B U5DZDP KernelSU Next build](kernelsu-next/README.md)
- [Reproduce the port](docs/REPRODUCE_PORT.md)
- [Payload support format](support/README.md)
