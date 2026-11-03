# mmdmap

A local workspace for **Mermaid, Markdown, DBML, and draw.io**, for macOS and Windows. Edit source with live previews, arrange database tables, or draw system architecture in a `.drawio` tab. Follow document links and explore your folder as a map. Files stay on your device; the bundled editors work offline.

**[Download a release](https://github.com/ayaganov/mmdmap-release/releases)** · **[Mermaid authoring skill](skills/mermaid-author/SKILL.md)**

## Installation

- **Mac Apple Silicon:** open `mac-arm64.dmg` and drag mmdmap into Applications.
- **Mac Intel:** use `mac-x64.dmg` the same way.
- **Windows x64:** run the `win-x64.exe` installer.

Mac previews use a self-signed update certificate without Apple notarization. If macOS blocks first launch, follow [Apple's Open Anyway instructions](https://support.apple.com/en-us/102445). Windows previews are unsigned. Checksums are included in each release.

## Updates

Version 0.3.0 or later: **Check for updates → Download update → Restart to update**. Earlier versions need one manual installation to enable updates. Save your documents before restarting. The editor works offline; updates need a connection.

## Agent skill

Teach your agent to write precise Mermaid diagrams using meaningful blocks, branches, asynchronous flows, tooltips, and links. The skill works independently of mmdmap.

With Node.js 22.20 or newer:

```sh
npx skills add ayaganov/mmdmap-release --skill mermaid-author
```

Choose your agent during installation; add `--global` to use the skill across projects. To check and install skill updates, run `npx skills check` and `npx skills update`. Skill updates are separate from app updates.

For manual installation or a fixed version, download `mermaid-author-vVERSION.zip` from a release and copy the **whole `mermaid-author` folder** into your agent's skills directory.

Application source is currently private. Source access holders can build with Node.js 24: run `npm ci`, then `npm run package` in the source checkout. The first build downloads a pinned draw.io runtime; later builds can reuse its cache. Open the app under `release/`. Local builds update by rebuilding.

[MIT license](LICENSE). Bundled draw.io retains its own license and notices. Independent project, not an official Mermaid or draw.io tool.
