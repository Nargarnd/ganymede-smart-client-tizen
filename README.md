# Ganymede Smart Client for Samsung TVs (Tizen)

A [Ganymede](https://github.com/Zibbp/ganymede) client for Samsung Smart TVs, packaged as a
[TizenBrew](https://github.com/reisxd/TizenBrew) module. This repository holds the built module only.

> **Status:** in testing. There is no release yet; the `spike` branch holds a feasibility build.

## Install

1. On the TV, enable Developer Mode (Apps → type `12345`) and set your PC's IP as the host. Reboot the TV.
2. Install TizenBrew on the TV with [TizenBrew Installer](https://github.com/reisxd/TizenBrew/blob/main/docs/README.md).
   Tizen 7.0+ TVs (2023 and newer) need a Samsung account certificate during the install.
3. In TizenBrew, add the GitHub module `Nargarnd/ganymede-smart-client-tizen`.

Requires Tizen 6.0 (2021) or newer.

## Why a service?

TizenBrew serves apps from `http://127.0.0.1:8081`, so the browser treats calls to your Ganymede
server as cross-site and never sends its session cookie. The module's small service
(`service/service.js`) forwards API calls on the TV itself and carries the cookie, so watch
progress syncs. It only listens on `127.0.0.1` and only forwards `/api/` requests from TizenBrew.
