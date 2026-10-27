# Root My Galaxy Payloads — SM-S928B DZF2

This repository contains only the S928B payload for firmware `S928BXXS6DZF2`
and kernel `6.1.145-android14-11-33419968-abS928BXXS6DZF2`.

The feed exposes one profile: `e3q-S928BXXS6DZF2`. Root My Galaxy fetches the
exploit payload and `ksud` from this repository's `support/targets-v3.json`.
The final exploit, module, and `ksud` payloads stay in the repository; intermediate builds do not. The custom KernelSU Manager APK is a release asset for this target.

## S928B artifacts

- Exploit payload: `artifacts/e3q-S928BXXS6DZF2/cve-2026-43499-app.so`
- KernelSU module: `kernelsu/android14-6.1_kernelsu-e3q-S928BXXS6DZF2-kdp.ko`
- Late-load binary: `kernelsu/ksud-e3q-S928BXXS6DZF2-kdp`
- Patch stack: Samsung KDP/RKP/DEFEX, upstream mount-hide commit, and the
  Samsung SELinux Hide kretprobe fallback.

Mount hiding and SELinux Hide initialize enabled. Mount hiding filters proc
mount-table views. It does not hide ordinary files. Root My Galaxy removes its
staged helper, exploit payload, and `ksud` copies after an install attempt.
SELinux Hide filters SELinuxFS query/status results; `/proc/self/attr/current`
writes remain unchanged.

## Build the exploit payload

```sh
make TARGET=e3q-S928BXXS6DZF2 ANDROID_NDK_HOME=/path/to/android-ndk stable
```

The release payload is padded to 104,128 bytes. Keep generated `build/` output
out of the repository; commit only the published S928B payload artifact.

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
- [Reproduce the port](docs/REPRODUCE_PORT.md)
- [Payload support format](support/README.md)
