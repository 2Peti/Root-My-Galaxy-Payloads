# KernelSU Next — SM-S928B U5DZDP

This is an additional S928B variant. The original KernelSU v3.2.5 build and its
Mount Hide patch remain in `../kernelsu/`.

| Field | Value |
| --- | --- |
| Model | `SM-S928B` |
| Firmware | `S928BXXU5DZDP` |
| Fingerprint | `samsung/e3qxeea/e3q:16/BP4A.251205.006/S928BXXU5DZDP:user/release-keys` |
| Kernel release | `6.1.145-android14-11-33419968-abS928BXXU5DZDP` |
| KernelSU Next version | `v3.2.0` |
| Source commit | `pascua28/KernelSU-Next-Samsung@1a65590d32cfb764bdccb44ec098b660d6c48808` |

Both binaries were built from source; PR #408's S926B binaries were not used.
The module uses the existing local Manager package and signing certificate
(`me.weishu.kernelsu`, expected certificate block size `0x02fc`, SHA-256
`4374ef7003188d2f7e4cbeec432ed758e98af594e47b1e785b08ef46ad5e3e65`).

| Artifact | Size | SHA-256 |
| --- | ---: | --- |
| `android14-6.1_ksunext-e3q-S928BXXU5DZDP-kdp.ko` | 577,904 | `35d4f29b7bb47ed11a48fc6d6b9c30afc4a38bf58a8ec4a366d22f8587e74c0c` |
| `ksud-e3q-S928BXXU5DZDP-kernelsu-next` | 4,199,720 | `d2bd9be09880da3922d5d43905271d9fb02a59fb4ddb5d54303f6e8ed8d2652c` |

The `ksud` binary embeds the module for KMI `android14-6.1`. Its build used
`ghcr.io/ylarod/ddk-min:android14-6.1-20260313`; that image's prepared kernel
tree reports `6.1.166-dirty`. The module's `vermagic` was set to the phone's
U5DZDP release, and `check_symbol` passed against the DDK's `vmlinux`. The
exact U5DZDP `vmlinux` and `Module.symvers` were unavailable, so the module has
not been checked against the phone's kernel ABI or tested on-device.

This KernelSU Next source includes SELinux Hide but not Mount Hide. Use the
original KernelSU v3.2.5 variant when Mount Hide is needed. The newly built
variant is for testing; it has no public release yet.
