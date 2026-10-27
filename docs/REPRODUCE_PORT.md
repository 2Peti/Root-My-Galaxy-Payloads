# Reproduce the S928B port

The repository supports two SM-S928B firmware profiles. Build the original
DZF2 exploit with:

```sh
make TARGET=e3q-S928BXXS6DZF2 ANDROID_NDK_HOME=/path/to/android-ndk stable
```

For U5DZDP, build the same device-tested S928B offsets under its exact identity:

```sh
make TARGET=e3q-S928BXXU5DZDP ANDROID_NDK_HOME=/path/to/android-ndk release
```

Generated `build/` directories are temporary. Compare each output to the
corresponding artifact record before publishing source changes.

The original KernelSU v3.2.5 patch stack is documented in
[`kernelsu/README.md`](../kernelsu/README.md). The additional KernelSU Next
build and its DDK limits are in [`kernelsu-next/README.md`](../kernelsu-next/README.md).
