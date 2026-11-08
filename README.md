# Rotavox Runner

The Rotavox Runner connects a RadioDJ station to [Rotavox](https://app.rotavox.com). It
loads the station's approved music logs into RadioDJ, song by song, and reports back
what played.

**To install it:** in Rotavox, open **Station › Runner** and follow the steps there. The
installer is attached to each release on this page.

This repository holds the Runner's releases and the files its installer is built from.
Each release is tagged `runner-<commit>`, and a Runner updates itself only to releases
published here, checked against each release's `SHA256SUMS`.

Each release has:

- `RotavoxRunnerSetup-<version>-<commit>.exe`, the installer. The **Installer** workflow
  (`.github/workflows/installer.yml`) builds it with Inno Setup on GitHub's Windows
  runner when the release is published, from the release's own package, and adds it to
  `SHA256SUMS`. The installer isn't code-signed during the beta, so Windows SmartScreen
  warns before it runs.
- `rotavox-runner-<commit>.zip`, the package the installer unpacks and that a Runner
  updates itself from.
- `SHA256SUMS`.

## Third-party software in each release

- **Node.js** (MIT): the Windows x64 runtime, from nodejs.org, checked against its
  published SHA-256.
- **NSSM 2.24-101** (public domain): runs the Runner as a Windows service.
  `vendor/nssm/2.24-101/win64/nssm.exe` is the copy every release uses. It's from
  `https://nssm.cc/ci/nssm-2.24-101-g897c7ad.zip` (SHA-256 of the zip:
  `99f5045fffbffb745d67fe3a065a953c4a3d9c253b868892d9b685b0ee7d07b8`), and the SHA-256
  of the exe is
  `eee9c44c29c2be011f1f1e43bb8c3fca888cb81053022ec5a0060035de16d848`.
