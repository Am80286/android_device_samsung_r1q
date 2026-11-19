# LineageOS 23.2 for the Samsung Galaxy A80 (r1q)

Unofficial LineageOS 23.2 device tree for the Samsung Galaxy A80
(SM-A805F / SM-A805N / SM-A8050).

The local manifest snippet is in [`manifest/r1q.xml`](manifest/r1q.xml); the
commands below download it.

## Building

Set up a LineageOS 23.2 build environment as described in the
[LineageOS build guide](https://wiki.lineageos.org/devices/bacon/build/).
Around 400 GB of free disk space is recommended, although you could probably get away with less.

```bash
repo init -u https://github.com/LineageOS/android.git -b lineage-23.2
mkdir -p .repo/local_manifests
curl -fsSL -o .repo/local_manifests/r1q.xml \
    https://raw.githubusercontent.com/Am80286/android_device_samsung_r1q/lineage-23.2/manifest/r1q.xml
repo sync -c -j"$(nproc)" --no-clone-bundle --no-tags

source build/envsetup.sh
breakfast r1q
mka bacon -j"$(nproc)"
```

The flashable zip is written to `out/target/product/r1q/`.

## Notes

- Requires Samsung firmware A805FXXU7DXE1 (bootloader v7) or newer.
- Proprietary blobs are included in the `proprietary_vendor_samsung_*` repos,
  no extraction from a stock ROM is needed.
- The kernel is a fork of LineageOS' A71 kernel with r1q support, checked out
  to `kernel/samsung/sm7150`.
- `hardware/samsung` is used straight from LineageOS.

## Credits

Original r1q and sm7150-common trees by Andrzej Szafran, and the LineageOS
project.
