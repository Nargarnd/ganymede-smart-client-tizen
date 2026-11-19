# Ganymede Smart Client for Samsung TVs (Tizen)

A [Ganymede](https://github.com/Zibbp/ganymede) client for Samsung Smart TVs. It installs as its
own app on the TV's home screen. This repository holds the releases only.

Features: browse recent videos and channels, play VODs, watch live captures (with seeking back
inside a stream that is still recording), resume where you left off, and sync watch progress with
your Ganymede account. Hold Left/Right in the player to seek faster.

## Install

1. On the TV, enable Developer Mode: open **Apps**, type `12345` with the remote, switch
   Developer Mode on and enter the IP of the PC or phone you will install from. Restart the TV.
2. Get [TizenBrew Installer](https://github.com/reisxd/TizenBrew/blob/main/docs/README.md) on
   that PC or phone and connect it to the TV. Tizen 7.0+ TVs (2023 and newer) need a Samsung
   account certificate, which the installer creates.
3. In TizenBrew Installer choose **Install from GitHub** and enter
   `Nargarnd/ganymede-smart-client-tizen`. It installs the `.wgt` from the latest release.
4. Open **Ganymede Smart Client** from the TV's apps. Enter your Ganymede server address (and,
   for live playback, the temp file server if you run one), then sign in.

To update, repeat step 3: the newer release replaces the app and keeps its settings and sign-in.
You can also download the `.wgt` from [Releases](../../releases/latest) and use **Install from
USB**.

Tested on a 2023 QN95C (Tizen 8.0). Tizen 6.0 (2021) or newer should work.

## Why does it include a service?

The app's page is not on your Ganymede server's site, so the TV's browser engine never sends
Ganymede's session cookie. The app carries a small background service that runs on the TV itself:
it listens only on `127.0.0.1`, forwards `/api/` calls to your server with the cookie, and refuses
requests from websites. Without it, browsing and playback still work, but signing in with a
username and syncing watch progress do not.

## Troubleshooting

Press the red colour key to show or hide a diagnostics overlay (app version, Tizen version,
whether the service is running, player events). A photo of it helps when reporting a problem.
