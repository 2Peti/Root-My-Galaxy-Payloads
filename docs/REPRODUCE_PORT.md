# Reproduce the S928B port

The only supported target is `e3q-S928BXXS6DZF2`:

```sh
make TARGET=e3q-S928BXXS6DZF2 ANDROID_NDK_HOME=/path/to/android-ndk stable
```

The generated `build/e3q-S928BXXS6DZF2/` directory is temporary. Compare the
release payload to the artifact hash in `docs/SM-S928B-S928BXXS6DZF2.md`, then
remove `build/` before publishing source changes.

KernelSU uses v3.2.5 and the patch stack documented in
[`kernelsu/README.md`](../kernelsu/README.md). Build the module against the
exact S928B release and run the DDK `check_symbol` step before publishing a
replacement.
