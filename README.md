ClockworkPi uConsole kernel fork
================================

This repository carries the complete Linux source used by
[`blue-1ms/uconsole-ubuntu-lts`](https://github.com/blue-1ms/uconsole-ubuntu-lts)
for Ubuntu 26.04 on the ClockworkPi uConsole CM4 Lite. It is a source and
provenance repository; installable Debian packages are published by
[`blue-1ms/uconsole-apt`](https://github.com/blue-1ms/uconsole-apt).

Current stable release
----------------------

- Stable tag: [`7.1.4-stable`](https://github.com/blue-1ms/rpi-linux/releases/tag/7.1.4-stable)
- Tested candidate: `7.1.4-candidate.04`
- Runtime ABI: `7.1.4-1001-uconsole`
- Exact patched source commit: `556fdcffd188f56281a328dda1dac0f1af737a71`
- Release branch: `uconsole/ubuntu-26.04-7.1.4`
- Release base: Raspberry Pi `rpi-7.1.y` commit
  `8a033ce62b843f38bdc2af6023e6203704cf1131`

The stable source includes the CM4 uConsole overlay, CWU50 old/new panel
detection, OCP8178 backlight, AXP PMIC/battery support, audio routing hardware
support, and the BCM2711 VC4/V3D DMA-zone fix. The exact source is paired with
`uconsole-platform 0.1.20` and the signed package receipt in the control-plane
repository.

Branch and release policy
-------------------------

- `main` is the upstream-oriented landing branch and points maintainers to the
  latest stable release.
- `uconsole/ubuntu-26.04-<version>` contains the exact patched release source.
- Candidate and stable tags are immutable. A stable tag points to the same
  source commit as the hardware-passed candidate; it is never rebuilt or moved.
- `vendor/akrex-*` branches are historical uConsole hardware provenance only.
  New kernels start from a pinned official Raspberry Pi or Canonical source,
  then rebase and audit the project-owned patch series.
- Kernel packages, A/B validation, FAT diagnostics, hardware evidence and
  update instructions live in
  [`uconsole-ubuntu-lts`](https://github.com/blue-1ms/uconsole-ubuntu-lts/blob/main/HANDOFF.md).

The next upstream kernel must use a new ABI, Debian package version, candidate
tag and immutable receipt. Do not install this repository directly over
`/boot`; use the signed `uconsole-apt` packages and the supported
`flash-kernel`/`piboot-try` A/B path.

Upstream Linux kernel documentation
===================================

There are several guides for kernel developers and users. These guides can
be rendered in a number of formats, like HTML and PDF. Please read
Documentation/admin-guide/README.rst first.

In order to build the documentation, use ``make htmldocs`` or
``make pdfdocs``.  The formatted documentation can also be read online at:

    https://www.kernel.org/doc/html/latest/

There are various text files in the Documentation/ subdirectory,
several of them using the Restructured Text markup notation.

Please read the Documentation/process/changes.rst file, as it contains the
requirements for building and running the kernel, and information about
the problems which may result by upgrading your kernel.

Build status for rpi-6.12.y:
[![Pi kernel build tests](https://github.com/raspberrypi/linux/actions/workflows/kernel-build.yml/badge.svg?branch=rpi-6.12.y)](https://github.com/raspberrypi/linux/actions/workflows/kernel-build.yml)
[![dtoverlaycheck](https://github.com/raspberrypi/linux/actions/workflows/dtoverlaycheck.yml/badge.svg?branch=rpi-6.12.y)](https://github.com/raspberrypi/linux/actions/workflows/dtoverlaycheck.yml)

Build status for rpi-6.18.y:
[![Pi kernel build tests](https://github.com/raspberrypi/linux/actions/workflows/kernel-build.yml/badge.svg?branch=rpi-6.18.y)](https://github.com/raspberrypi/linux/actions/workflows/kernel-build.yml)
[![dtoverlaycheck](https://github.com/raspberrypi/linux/actions/workflows/dtoverlaycheck.yml/badge.svg?branch=rpi-6.18.y)](https://github.com/raspberrypi/linux/actions/workflows/dtoverlaycheck.yml)

Build status for rpi-7.1.y:
[![Pi kernel build tests](https://github.com/raspberrypi/linux/actions/workflows/kernel-build.yml/badge.svg?branch=rpi-7.1.y)](https://github.com/raspberrypi/linux/actions/workflows/kernel-build.yml)
[![dtoverlaycheck](https://github.com/raspberrypi/linux/actions/workflows/dtoverlaycheck.yml/badge.svg?branch=rpi-7.1.y)](https://github.com/raspberrypi/linux/actions/workflows/dtoverlaycheck.yml)
