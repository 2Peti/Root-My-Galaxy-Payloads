# S928B KernelSU artifacts

This directory contains only the SM-S928B DZF2 KernelSU pair. KernelSU is
v3.2.5, commit `b0bc817b4e966aa6aa830834eaf6ef765d821d40`.

| Artifact | Size | SHA-256 |
| --- | ---: | --- |
| `android14-6.1_kernelsu-e3q-S928BXXS6DZF2-kdp.ko` | 412,600 | `64b10f49cfd86a702c06b4bea80d3dea4a1a7d5cd4a1f2d1e7d45783a0c53625` |
| `ksud-e3q-S928BXXS6DZF2-kdp` | 4,772,304 | `3edb768b549e5c92e9043cebdb0fffdd5b61dec42313571c3157e4078d65991b` |

Apply the patch stack in this order:

1. `patches/KernelSU-v3.2.5-samsung-kdp-rkp-defex.patch`
2. `patches/KernelSU-v3.2.5-mount-hide-80a3ab31.patch`
3. `patches/KernelSU-v3.2.5-samsung-selinux-hide-kprobes.patch`

The first carries JingMatrix's upstream commit
[`80a3ab31`](https://github.com/JingMatrix/KernelSU/commit/80a3ab31eb108a5515ecaea0f4799a035b7d1ce1)
and adds the Samsung no-patch-text fallback. Mount Hide starts enabled and
filters proc mount-table views. It works without `ksu_patch_text`: Samsung
no-patch-text builds use kretprobe return handlers on proc mount-file opens and
change only each file's private `show` callback, avoiding writes to global
`file_operations`. SELinux Hide also starts enabled; it filters SELinuxFS
query/status results but leaves `/proc/self/attr/current` writes unchanged.

Build with `ghcr.io/ylarod/ddk-min:android14-6.1-20260313`, exact release
`6.1.145-android14-11-33419968-abS928BXXS6DZF2`, and:

```sh
CONFIG_KSU=m
CONFIG_KSU_SAMSUNG_KDP=y
CONFIG_KSU_SAMSUNG_RKP=y
CONFIG_KSU_SAMSUNG_DEFEX=y
CONFIG_KSU_SAMSUNG_NO_PATCH_TEXT=y
KSU_EXPECTED_SIZE2=0x02fc
KSU_EXPECTED_HASH2=4374ef7003188d2f7e4cbeec432ed758e98af594e47b1e785b08ef46ad5e3e65
```

`check_symbol` passed against the DDK-generated `vmlinux`. The recovered
S928B `vmlinux.elf` audit and hardware revalidation of this default-enabled
build remain pending. See the [S928B build record](../docs/SM-S928B-S928BXXS6DZF2.md).

The custom Manager APK is attached to the
[S928B DZF2 release](https://github.com/2Peti/Root-My-Galaxy-Payloads/releases/tag/s928b-dzf2-2026-10-27). Its local signing certificate is accepted as the secondary Manager signer above.
