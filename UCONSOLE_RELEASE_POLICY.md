# uConsole kernel source release policy

This repository supplies patched source only. Build manifests, Debian packages,
signed APT transactions, hardware evidence and publication receipts are owned by
`blue-1ms/uconsole-ubuntu-lts` and `blue-1ms/uconsole-apt`.

## Dynamic release identity

No validator, service, maintainer script or policy code may embed a concrete
kernel ABI, candidate number, stable tag, platform version, source commit or
archived manifest path. Those values come from the selected manifest, immutable
package/release receipts, dpkg metadata, A/B deployment state or explicit
evidence paths. Code retains only stable rules such as the `*-uconsole` flavour,
ABI/asset consistency, minimum platform compatibility, signatures and current
plus one adjacent N-1 fallback.

## Validation layers

Fast CI validates source policy, patch/config hashes and package metadata. Each
new immutable kernel payload receives one signed content-addressed Artifact
validation covering ownership, modules/depmod/vermagic, headers external-module
build, DTB/DTBO and staging initramfs. A later candidate with identical package
bytes reuses that receipt after signature and SHA verification.

The hardware stable gate separately covers `piboot-try`, promote, FAT mailbox,
panel/backlight/DRM, input/audio/PMIC, Wi-Fi/BT/basic USB and the sole adjacent
N-1 fallback. Kernel-only releases do not perform image compose, mounted-image,
GNOME or first-boot validation. README, GitHub Release, tag, retention and final
publication checks run only during stable closeout.

## Kernel/platform transaction

A normal kernel stable APT transaction contains separate image, modules,
headers, buildinfo and `uconsole-kernel` packages, plus the exact tested
`uconsole-platform`, applicable Plymouth package, signed repository, checksums
and receipts. Packages remain separate `.deb` files. The meta package declares
`uconsole-platform (>= minimum-compatible-version)` and must not downgrade a
newer compatible platform.

Platform uses independent monotonic SemVer. An independent
`platform-<semver>-stable` Release is created only when kernel source and kernel
package bytes are unchanged. Normal kernel closeout does not require a second
platform Release.

Candidate and stable source tags are immutable. Stable aliases the exact
hardware-passed candidate source and package identity; no published bytes or tag
may be rebuilt, overwritten or moved.
