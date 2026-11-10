<p align="center">
  <img src="https://raw.githubusercontent.com/Rhyolite-App/.github/main/assets/rhyolite-256.png" width="112" height="112" alt="Rhyolite logo: a polished rhyolite river pebble with a blue flow vein">
</p>

<h1 align="center">Rhyolite Releases &amp; Issue Tracker</h1>

<p align="center">
  <b>Notes that flow into layered knowledge.</b><br>
  Official installers, portable archives, checksums, release notes, and public issue tracking for <a href="https://rhyolite.app"><b>Rhyolite</b></a>.
</p>

<p align="center">
  <a href="https://github.com/Rhyolite-App/releases/releases/latest"><img alt="Latest Release" src="https://img.shields.io/github/v/release/Rhyolite-App/releases?label=release&color=0A84FF"></a>
  <img alt="macOS arm64" src="https://img.shields.io/badge/macOS-arm64-000000?logo=apple&logoColor=white">
  <img alt="Windows x64" src="https://img.shields.io/badge/Windows-x64-0078D4?logo=windows&logoColor=white">
  <img alt="Linux x64" src="https://img.shields.io/badge/Linux-x64-FCC624?logo=linux&logoColor=black">
</p>

---

## Download

Download the latest version from **[Releases → Latest](https://github.com/Rhyolite-App/releases/releases/latest)**.

Every build is a self-contained native executable (no runtime to install), and every installer installs per-user without requiring administrator privileges.

| Platform | Per-User Installer | Portable Archive |
|---|---|---|
| **macOS** (Apple silicon, macOS 12+) | `Rhyolite-UserInstaller-v*-macos-arm64.dmg` — open and drag **Rhyolite** to **Applications** (or `~/Applications`) | `Rhyolite-v*-macos-arm64.zip` (`Rhyolite.app`) |
| **Windows** (64-bit) | `Rhyolite-UserSetup-v*-win-x64.exe` — installs to `%LocalAppData%\Programs\Rhyolite` with Start menu entry &amp; uninstaller | `Rhyolite-v*-win-x64.zip` (`Rhyolite.exe`) |
| **Linux** (64-bit) | `sh Rhyolite-UserInstaller-v*-linux-x64.sh` — installs to `~/.local` (`rhyolite` CLI, desktop entry, icon); `--uninstall` removes it | `Rhyolite-v*-linux-x64.tar.gz` |

### First Launch

- **macOS:** Release builds are signed with an Apple Developer ID certificate and notarized by Apple, so Gatekeeper opens them without warning.
- **Windows:** Builds are not yet signed with a Windows Authenticode certificate; if Windows SmartScreen appears, choose **More info → Run anyway**.

### Verify Checksums

Every release ships with `SHA256SUMS.txt`. After downloading an installer and `SHA256SUMS.txt` into the same folder:

```bash
# macOS
shasum -a 256 --ignore-missing -c SHA256SUMS.txt

# Linux
sha256sum --ignore-missing -c SHA256SUMS.txt
```

```powershell
# Windows (PowerShell)
Get-FileHash .\Rhyolite-UserSetup-*-win-x64.exe -Algorithm SHA256
```

---

## AI Agents (MCP) &amp; Command Line

Rhyolite includes a local [Model Context Protocol (MCP)](https://modelcontextprotocol.io) server over `stdio` and loopback HTTP (`127.0.0.1`), with per-folder scopes, `ai: exclude` / `ai: read-only` note rules, automatic secret redaction, destructive-change prompts, and a revertible audit log.

```bash
# Connect Claude Code over stdio (macOS)
claude mcp add rhyolite -- /Applications/Rhyolite.app/Contents/MacOS/Rhyolite --mcp-stdio --vault ~/Notes

# Run headless docs-as-code, broken-link, secret, and property checks in CI
Rhyolite check --vault ./docs --repo . --checks drift,links,secrets,frontmatter --format sarif --output rhyolite.sarif
```

---

## Feedback, Support &amp; Security

- **Report a bug or request a feature:** [Open an issue](https://github.com/Rhyolite-App/releases/issues/new/choose)
- **In-app documentation:** Press <kbd>F1</kbd> inside Rhyolite to open the searchable Help tab
- **Support &amp; FAQ:** [https://rhyolite.app/support](https://rhyolite.app/support) · [support@rhyolite.app](mailto:support@rhyolite.app)
- **Privacy policy:** [https://rhyolite.app/privacy](https://rhyolite.app/privacy)
- **Security vulnerabilities:** Please do **not** open public issues for security bugs. Report privately via [GitHub Security Advisories](https://github.com/Rhyolite-App/releases/security/advisories/new) or email **[support@rhyolite.app](mailto:support@rhyolite.app)** ([Security Policy](https://github.com/Rhyolite-App/.github/blob/main/SECURITY.md)).
