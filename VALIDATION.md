# Validation — macOS 0.2.0, 2026-10-16

Experimental laboratory prerelease. Live testing was deferred by the owner.

| Check | Evidence |
| --- | --- |
| Swift tests | 11 passing: CIDR, QR, secret-free profile encoding, legacy settings, Windows D3S vectors, CFG roundtrip, XML rejection, duplicate policy, three-way merge/deletions/conflicts and recovery policy |
| Rust tests | 10 unit + 4 ROUTES migration tests passing |
| Rust fmt / Clippy | Passing, all targets with warnings denied |
| Local synthetic TLS/UDP/ROUTES/rekey test | Passing: 306 authenticated echoes and 7 changed route callbacks in 32 seconds |
| App / extension / both framework binaries | Universal 2: arm64 + x86_64 |
| PKG | Extracted payload architecture, local signatures, icon, notices and uninstaller checks |
| Localization | 162 matching RU/EN keys |
| Visual review | Offscreen actual SwiftUI renders, synthetic profile only; RU/EN, dark/light and all tabs |
| Apple Developer signing / provisioning / notarization | Not available; app and extension use local ad-hoc signatures |
| Extension activation / corporate firewall / OS routing | Not tested |
| Physical Intel Mac | Not tested |
| Installed menu behavior, login startup, notification approval, Keychain permissions | Runtime acceptance pending |
| Installer install/upgrade/remove and update handoff | Runtime acceptance pending |
| External Kerio writer concurrency | Three-way merge tested synthetically; runtime coexistence pending |

The downloaded lab build is not a production-ready VPN release. Synthetic tests do
not establish real-server compatibility or Apple approval. Protection settings were
not changed. No personal profile store, CFG or clipboard was inspected during this task.
