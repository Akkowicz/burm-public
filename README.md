# BURM

Download the standalone launcher for your platform. It installs and updates the game automatically.

- [Windows launcher (x86-64)](https://github.com/Akkowicz/burm-public/releases/latest/download/burm_launcher-x86_64-pc-windows-msvc.exe)
- [Linux launcher (x86-64)](https://github.com/Akkowicz/burm-public/releases/latest/download/burm_launcher-x86_64-unknown-linux-gnu)
- [All releases and game executables](https://github.com/Akkowicz/burm-public/releases)

On Linux, mark the downloaded launcher executable with `chmod +x burm_launcher-x86_64-unknown-linux-gnu`, then run it. Linux builds require glibc 2.35 or newer and the native graphics/window libraries. Windows executables include the Visual C++ runtime. A compatible GPU is required for the game.

## Update feed

The launcher uses [latest.json](https://raw.githubusercontent.com/Akkowicz/burm-public/refs/heads/main/latest.json) by default. It contains download URLs for the Linux and Windows game executables, exact sizes and SHA-256 checksums. The launcher verifies these plus the executable version before activating an installation.

Historical manifests are stored in `manifests/vVERSION.json`. Release assets are immutable. Launcher self-update is separate: download a new launcher from the release page when needed.

## Publication

Releases are built and tested locally with stable Rust, then uploaded directly to GitHub Releases. GitHub Actions artifacts are not used. The publisher verifies all uploaded executables before updating the live feed.
