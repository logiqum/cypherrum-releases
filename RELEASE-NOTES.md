# Cypherrum Release Notes

User-facing release history.

## [0.12.1] — 2026-05-17 — "Public changelog, documented Dokany default"

Tooling and documentation patch. No runtime or wire-format changes since
v0.12.0 — upgrading is risk-free, and v0.11.x shares continue to mount
unchanged.

### Added

- **`cypherrum.com/changelog`** — full release history on the website, with
  per-version anchors for deep-linking.
- **Public release-notes mirror** — every release's notes are now mirrored
  to `RELEASE-NOTES.md` in this repository.
- **Inlined release notes on GitHub** — release pages now contain the
  version notes inline; no click-through required.
- **Download-page navigation** — the "Changelog" and "All releases" cards
  on `cypherrum.com/download` now point at public destinations.

### Changed

- **Dokany is the documented default Windows mount path.** The installer
  bundles the Dokany driver. The portable-zip README, the project README,
  and the User Guide install + troubleshooting sections all reflect this.

### Release pipeline

- **`cypherrum.com/download` auto-refreshes after every release**, so the
  download buttons always serve the latest version within minutes of
  publish.

---

## [0.12.0] — 2026-05-17 — "Post-quantum mesh shares"

Cypherrum's mesh sharing is now post-quantum by default. Vault keys
exchanged between contacts are wrapped with ML-KEM-768 (NIST FIPS 203),
protecting against future "harvest-now, decrypt-later" attacks on
network-borne share material.

### Added

- **Post-quantum mesh share envelopes.** Vault member keys are wrapped
  with ML-KEM-768 across both supported share paths:
  - **QR-paired contacts:** the pairing code carries the recipient's
    post-quantum public key, so the share is wrapped immediately on
    pairing.
  - **Invite-link contacts:** the joiner posts its public key through the
    relay inbox, the inviter wraps the share and returns it — neither
    party needs to be online at the same time.
- **Per-device post-quantum keypair.** Created automatically on first
  service launch and stored alongside the device identity key.
- **Forward-compatible inbox protocol.** New message types carry the
  post-quantum bootstrap; clients ignore unrecognized types so future
  protocol additions don't break older versions.

### Compatibility

- **Existing v0.11.x shares mount unchanged.** No migration is required;
  classical share entries continue to work indefinitely.

### Known limitations

- **Pairing-code QR is denser** — best scanned at ~50 cm distance
  (Version 30 QR). Older phone cameras may need to back up slightly.

---

## [0.11.1] — 2026-05-14 — "Signed Windows installer"

First Cypherrum build whose Windows executables and installer are
Authenticode-signed by **Logiqum Korlátolt Felelősségű Társaság**.
Users will see `Verified publisher: Logiqum Korlátolt Felelősségű
Társaság` in UAC prompts and Properties → Digital Signatures, and
SmartScreen warnings will diminish as the publisher's reputation
accrues (multi-week curve per Microsoft's post-2024 model).

### Added

- **Authenticode signing for every Windows artifact** — `cypherrum.exe`,
  `cypherrum-service.exe`, the test binary, and the NSIS installer.
  Signatures are RFC3161-timestamped, so they remain valid after the
  underlying signing certificate rotates.

### Fixed

- **No more console-window flash on service start.** Cypherrum's
  background service is now built in the GUI subsystem; non-launcher
  invocations (login auto-start, post-install hook, manual launch) no
  longer briefly show a console window.
