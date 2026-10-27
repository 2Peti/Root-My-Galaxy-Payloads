# SM-S928B — S928BXXS6DZF2

## Target

| Field | Value |
| --- | --- |
| Model | `SM-S928B` |
| Firmware | `S928BXXS6DZF2` |
| Device | `e3q` |
| Product | `e3qxxx` |
| Android fingerprint | `samsung/e3qxxx/e3q:16/BP4A.251205.006/S928BXXS6DZF2:user/release-keys` |
| Kernel | `6.1.145-android14-11-33419968-abS928BXXS6DZF2` |
| Profile | `e3q-S928BXXS6DZF2` |

## Published payloads

| File | Size | SHA-256 |
| --- | ---: | --- |
| `artifacts/e3q-S928BXXS6DZF2/cve-2026-43499-app.so` | 104,128 | `a49b378d654c7e637697a701c3c4c5fd02d22b9b30a7069c03e64ec5844af206` |
| `kernelsu/android14-6.1_kernelsu-e3q-S928BXXS6DZF2-kdp.ko` | 412,600 | `64b10f49cfd86a702c06b4bea80d3dea4a1a7d5cd4a1f2d1e7d45783a0c53625` |
| `kernelsu/ksud-e3q-S928BXXS6DZF2-kdp` | 4,772,304 | `3edb768b549e5c92e9043cebdb0fffdd5b61dec42313571c3157e4078d65991b` |

## KernelSU build

KernelSU v3.2.5 (`b0bc817b4e966aa6aa830834eaf6ef765d821d40`) includes the
Samsung KDP/RKP/DEFEX patch, JingMatrix's mount-hide commit
[`80a3ab31`](https://github.com/JingMatrix/KernelSU/commit/80a3ab31eb108a5515ecaea0f4799a035b7d1ce1), and the Samsung SELinux Hide kretprobe
fallback. The exact DDK vermagic is:

```text
6.1.145-android14-11-33419968-abS928BXXS6DZF2 SMP preempt mod_unload modversions aarch64
```

The module was built with Samsung no-patch-text mode. DDK `check_symbol` passed
against generated `vmlinux`; exact recovered-ELF audit and hardware
revalidation of this default-enabled build remain pending. The module accepts
the upstream Manager signer and the local Manager signer
(`0x02fc`, SHA-256
`4374ef7003188d2f7e4cbeec432ed758e98af594e47b1e785b08ef46ad5e3e65`).

Mount Hide and SELinux Hide initialize enabled. Mount Hide filters proc
mount-table views, not regular files. SELinux Hide filters SELinuxFS
context/access/status results; `/proc/self/attr/current` writes remain
unchanged. The offline Root My Galaxy app removes its staged helper, exploit
payload, and `ksud` copies after each install attempt.

## Attribution

The exploit port is based on
[NebuSec's CVE-2026-43499 source](https://github.com/NebuSec/CyberMeowfia/tree/main/IonStack/CVE-2026-43499/exploit).
Mount Hide is based on JingMatrix's upstream commit above. Original Root My
Galaxy is by [BuSung-dev](https://github.com/BuSung-dev/Root-My-Galaxy).
