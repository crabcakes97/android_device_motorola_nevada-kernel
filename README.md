# Prebuilt kernel — Motorola Nevada (moto g play 2026, XT2615-1)

Prebuilt stock kernel for the Nevada Lineage 23 bringup. Syncs to
`device/motorola/nevada-kernel/` in the build tree (companion of the
`android_device_motorola_nevada` device repo, selected via
`TARGET_FORCE_PREBUILT_KERNEL := true`).

## Contents (all carved from stock RETUS `W1WNS36.18-114-1` firmware)

| File | Source |
|---|---|
| `Image.gz` | carved from `boot.img` (boot v4, gzip, 21.5 MB) |
| `dtb/nevada.dtb` | carved from `vendor_boot.img` DT table (single entry) |
| `vendor/*.ko` (196) | `vendor_dlkm` partition of stock super image |
| `vendor_ramdisk/*.ko` (197) | `vendor_boot` vendor ramdisk |
| `modules.load.vendor` | stock `vendor_dlkm` module load list |
| `modules.load.vendor_ramdisk`, `modules.load.recovery` | stock ramdisk lists |

## Long-term: source kernel

Stock 5.15 kernel, so these prebuilts match the shipped modules exactly.
Proper source: `MotorolaMobilityLLC/kernel-mtk`, branch
`android-16-release-w1wn36.18-114` (same release tag as stock),
config `build.config.mtk.aarch64`, DTS `mt6835-nevada-evb-overlay`,
plus the matching `motorola-kernel-modules` branch for out-of-tree modules.
Build it, refresh this directory (or point the tree at full kernel source),
then switch `BoardConfig.mk` off `TARGET_FORCE_PREBUILT_KERNEL`.
