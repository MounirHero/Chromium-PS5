# Chromium PS5

Debian's x86-64 Linux Chromium, unmodified, running inside a native PS5 homebrew app
(title **CHRM00000**): Linux as a library (LKL) underneath, and **gx**, a guest executor
derived from [chromium-nx](https://github.com/shodowlo/chromium-nx) by shodowlo and ported
to x86-64.

Status (0.2.0): Chromium's headless shell runs end to end (DOM + JavaScript) under the PS5's
constraints on a PC test bench; the app shows the whole boot sequence and log on screen.
Display, network and input come next.

## Install

1. Download `CHRM00000.zip` from the Releases and copy the `CHRM00000` folder to
   `/data/homebrew/` (or use `CHRM00000.ffpkg` with ShadowMount).
2. Download the root image and put `rootfs.img` inside the app folder:
   `/data/homebrew/CHRM00000/rootfs.img`. With the `.ffpkg`, put it on a USB drive as
   `chromium-ps5/rootfs.img`.
3. Open Chromium PS5. Hold Circle for two seconds to close it.

## Logs

- On screen: the boot stages on the left, the live log on the right (Triangle filters).
- Live over the network: `nc <ps5-ip> 9031`.
- Over FTP while the app runs: `/mnt/sandbox/CHRM00000_000/download0/chromium-ps5/logs/`
  and `/mnt/sandbox/CHRM00000_000/download0/hui/dev/app.log`.

`sce_module/libc.prx` is not stored here; it is inside the release files.

Licenses: GPL-2.0 (gx, LKL), GPL-3.0-or-later (app shell, ps5-opengl). Not affiliated with
Google or Sony.
