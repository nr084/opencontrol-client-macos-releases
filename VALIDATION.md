# Validation — 2026-10-15

Development version 0.1.0. **No public binary release.** The owner cancelled
UI-only/ad-hoc testing distribution. Developer ID/provisioning are unavailable.

| Check | Result |
| --- | --- |
| Xcode 27.0 / Swift 6.4 Release build | PASS: host + System Extension + shared framework |
| App CPU architectures | PASS: arm64 and x86_64 in one app |
| System Extension / both framework architectures | PASS: arm64 and x86_64 |
| Rust | 1.99.0, release builds for both Darwin targets |
| Protocol dependency | 0.2.0, pinned Git commit 35a5c848fb2a25a64da36268026906ce3757b974 |
| Rust unit tests | PASS: 10 |
| ROUTES migration tests | PASS: 4, including failed-apply rollback and pending rekey/replay preservation |
| Rustfmt / Clippy all targets, warnings denied | PASS |
| Swift tests | PASS: 5, including CIDR exclusions, QR compatibility, password-free serialization and retry policy |
| Localization parity | PASS: 118 matching RU/EN keys |
| Synthetic 32-second loopback ABI/TLS/UDP test | PASS: 301 authenticated echoes, 7 changed route callbacks, continuing rekeys |
| PKG packaging pipeline (earlier local validation artifact) | PASS: 5.2 MB; extracted app signature integrity and Universal architecture checked |
| PKG distribution | CANCELLED: validation-only installer is not published and is removed |
| UI | RU/EN rendered from real SwiftUI with synthetic profile, visually inspected |
| Developer ID / provisioning / notarization | NOT AVAILABLE |
| Signed System Extension activation and real OS routing | NOT TESTED |
| Real corporate firewall / physical Intel Mac | NOT TESTED |
| Real machine installation, upgrade, deactivation and uninstall | NOT TESTED |

The loopback fixture owns an ephemeral certificate and local port, uses public
synthetic credentials, and deletes its key/cert/process after completion. Its
platform callbacks validate complete route configurations but do not install OS
routes. It is not a public VPN endpoint or evidence of corporate acceptance.

Current network recovery also restarts on underlying-path changes and wake; this
code compiles but needs signed System Extension sleep/wake/path acceptance testing.

The initial metadata uses the Android engine's known OS code 2 with a macOS label.
No unverified mapping to a different wire OS identifier has been invented.

No claim of Apple approval, real-world VPN readiness, notarization, or complete
Android feature parity is made. Source and build verification are separate from
those external/runtime checks.
