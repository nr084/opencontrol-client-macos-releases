# Installation and removal

**No working PKG has been published.** These steps describe the future signed
release. Do not disable SIP, Gatekeeper or certificate verification.

1. Download the Universal PKG from Releases and verify SHA256.
2. Install **OpenControl Client.app** in `/Applications`.
3. Allow the network System Extension in System Settings and approve the VPN
   configuration when macOS asks. The settings location varies by macOS version.
4. Add the server, port (4090 by default), username and password from your administrator.
5. Inspect and independently verify the server's SHA-256 fingerprint before trusting
   it, or import a trusted PEM CA certificate.
6. Accept the VPN data disclosure and connect.

Settings includes language, default menu-bar profile and network exclusions.
Profile/routing changes apply on the next connection. Import Android QR images or
profile JSON files through the import action. QR codes contain passwords; keep them private.

To remove the app, use Settings → Prepare to uninstall. Separately choose whether
to erase profiles and Keychain passwords. Confirm VPN configuration removal and
System Extension deactivation, and restart if macOS requires it. Quit the app, then
run `Uninstall OpenControl Client.command` from the release bundle. A copy is also
inside the app at `Contents/Resources/Uninstall.command`.

The script verifies the bundle identifier, asks for confirmation, removes only the
fixed application path and its PKG receipt. Administrator authentication happens
locally in Terminal. It never edits the SystemExtensions database or other VPNs.
Profiles and passwords are kept unless explicitly erased in the app.
