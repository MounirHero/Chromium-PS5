# Chromium PS5

Debian's x86-64 Linux Chromium, unmodified, running inside a native PS5 homebrew app:
Linux as a library (LKL) underneath, and **gx** — a guest executor that loads Linux ELF
programs and patches every `syscall` into a jump to the host — derived from
[chromium-nx](https://github.com/shodowlo/chromium-nx) by shodowlo and ported to x86-64.

Status (0.1.0): the core runs Chromium's headless shell end to end (DOM + JavaScript) on a
Linux PC under the PS5's constraints (16 KB pages, no W+X memory, every syscall trapped);
the PS5 app builds and shows the full boot log on screen. Display, network and input are the
next milestone. See [docs/HANDOFF.md](docs/HANDOFF.md).

- `app/` — the PS5 app (BlackBearReloaded's native app boilerplate + ps5-opengl), title CHRM00000
- `app/src/gx/` — the core, shared by the console and the PC bench
- `bench/` — the PC test bench (`gx-bench -g -p 16384 rootfs.img`)
- `tools/` — root image (`build-image.sh`), syscall patch tables (`gxpatch.py`), LKL (`prepare-lkl.sh`)

Live log from the console: `nc <ps5-ip> 9031`.

Licenses: GPL-2.0 (gx, LKL), GPL-3.0-or-later (app shell, ps5-opengl). Not affiliated with
Google or Sony.
