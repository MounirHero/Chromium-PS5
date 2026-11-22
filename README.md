# Chromium PS5

Debian's x86-64 Linux Chromium, unmodified, running inside a native PS5 homebrew app
(title **CHRM00000**): Linux as a library (LKL) underneath, and **gx**, a guest executor
derived from [chromium-nx](https://github.com/shodowlo/chromium-nx) by shodowlo and ported
to x86-64.

Status (0.2.0 build 15): Chromium's headless shell runs on a PS5 with firmware 4.00. It loads
a page, runs its JavaScript and prints the DOM, about 9 seconds after the app starts. The app
shows the whole boot sequence and the log on screen. A visible browser window, network and
input come next.

## Install

1. Download `CHRM00000.ffpkg` from the Releases, copy it to `/data/homebrew/` and mount it
   with ShadowMount.
2. Download the root image and copy `rootfs.img` to `/data/chromium-ps5/rootfs.img`
   (or to a USB drive as `chromium-ps5/rootfs.img`).
3. Open Chromium PS5. Hold Circle for two seconds to close it.

## Logs

- On screen: the boot stages on the left, the live log on the right (Triangle filters).
- Live over the network: `nc <ps5-ip> 9031`.
- Files: `/data/chromium-ps5/logs/` (session, stages, crash reports).

`sce_module/libc.prx` is not stored here; it is inside the release files.

Licenses: GPL-2.0 (gx, LKL), GPL-3.0-or-later (app shell, ps5-opengl). Not affiliated with
Google or Sony.
