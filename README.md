# mmdmap

A local Mermaid editor for macOS and Windows. Code, diagrams, folders, and links between diagrams — all on your device.

**[Download a release](https://github.com/ayaganov/mmdmap-release/releases)**

## Installation

- **Mac Apple Silicon:** download `mac-arm64.dmg`, open it, and drag mmdmap into Applications.
- **Mac Intel:** use `mac-x64.dmg` the same way.
- **Windows x64:** run the `win-x64.exe` installer.

Mac previews use a self-signed update certificate, without Apple notarization. If macOS blocks the first launch, use **System Settings → Privacy & Security → Open Anyway** for a download you trust. [Apple instructions](https://support.apple.com/en-us/102445). Windows may show an unknown-publisher prompt. Checksums are included in every release.

## Updates

Install version 0.3.0 manually once. After that, use **Check for updates → Download update → Restart to update** inside the app. Save edited diagrams before restarting. Update checks also run after startup and every six hours. The editor works offline; only updates need a connection. Your diagrams are never uploaded.

## Agent skill

Download `mermaid-author-vVERSION.zip` from the same release. Give your agent its `SKILL.md` for Mermaid shapes, links, tooltips, and clear diagram semantics.

This repository contains distributions; application source is currently private. Source access holders can also run `npm ci` and `npm run package` in the source checkout to build locally. Local builds update by rebuilding.

[MIT license](LICENSE). Independent project, not an official Mermaid tool.
