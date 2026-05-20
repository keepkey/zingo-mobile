<!-- Describe this change and link any relevant issues -->

---

> This checklist is a starting point. Skip items that don't apply (e.g. a docs typo fix needs no hardware test). For background on the review approach, see the [KeepKey contributing guide](../../docs/contributing.md).

# Author

## General
- [ ] Self-reviewed the diff in GitHub's web interface
- [ ] Added or updated automated tests as appropriate
- [ ] Updated documentation (`README.md`, `docs/`) as appropriate
- [ ] Ran `yarn test` — all tests pass
- [ ] Ran the app and exercised the changed behaviour manually

## KeepKey Integration (skip if this PR does not touch keepkey code)

**Transport / protocol changes**
- [ ] Proto file hashes in `.github/proto-hashes.sha256` updated if proto files changed (see `docs/firmware-compat.md`)
- [ ] HID packet framing unit tests pass (`KeepKeyHIDTransport` / native module tests)
- [ ] Golden vector tests pass (see `docs/golden-test-vectors.md`)

**Hardware test results** — fill in before marking ready for review:

| Scenario | Platform | Result | Notes |
|---|---|---|---|
| Address display on device | Android (USB) | | |
| Address display on device | iOS (WalletConnect) | | |
| Shielded send — sign & broadcast | Android (USB) | | |
| Shielded send — sign & broadcast | iOS (WalletConnect) | | |
| Device disconnected mid-flow | Android | | |
| Wrong device (seed mismatch) rejected | Android | | |

> Hardware tests may be run against the `kkemu` emulator. See `docs/emulator.md`.

**UI changes**
- [ ] Before/after screenshots included below (if applicable)

# Reviewer

- [ ] Reviewed the diff against the [KeepKey integration plan](../../docs/) for the relevant platform
- [ ] Verified no KeepKey protocol deviations from `docs/pczt-signing-flow.md`
- [ ] Checked that `seed_fingerprint` binding is enforced on all device calls
- [ ] Ran the app and exercised the change manually
- [ ] Automated tests reviewed
