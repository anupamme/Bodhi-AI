# README source and release audit

Checked 2026-10-03. This is a documentation snapshot; moving release and branch links can change.

| Boundary | Evidence |
|---|---|
| Zenith pin | `6d850368c6fe83bea85c70aea7d8426ee5575321` before this documentation-only commit |
| Observed upstream main | `git ls-remote origin refs/heads/main`: `d0e40e895feb15097f90b569ce1af6f2af4923ba`, three commits after the pin |
| Latest public installer | [app-v2026.9.20](https://github.com/bigduu/Bodhi-AI/releases/tag/app-v2026.9.20), tag resolves to `46fad2074adc2ce465553fd9a207731ce55b4fde`; verified through public release HTML and expanded asset list |
| Installer's frontend | `git show app-v2026.9.20:scripts/frontend-package-lock.json`: `@bigduu/lotus-next@2026.9.16`, source `0495772ecab37402c3915c10a6c945cf286a132b` |
| Pinned source's frontend | [frontend-package-lock.json](../scripts/frontend-package-lock.json): `2026.9.22`, source `a480e2bb94f5dd08fe4b01b2f8844a2c9ed03245` |

The post-pin main commits document Homebrew installation, add bounded local image previews, and fix CI Rust cache paths. The README does not transfer those capabilities to the pinned source or installer. Unmerged branch work is outside this refresh.

Implementation sources reviewed:

- [Tauri configuration](../src-tauri/tauri.conf.json): splash, sidecar and frontend resources.
- [Shell entrypoint](../src-tauri/src/lib.rs): native commands, shortcut, runtime port injection and backend lifecycle.
- [Sidecar](../src-tauri/src/sidecar.rs): owned local process and startup checks.
- [CLI installation](../src-tauri/src/cli_install.rs): per-platform PATH behavior.
- [Package scripts](../package.json), [sidecar builder](../scripts/build-sidecar.cjs), [release workflow](../.github/workflows/release.yml): real development/build commands and target matrix.

The old README's “release train still needs a follow-up PR” text was historical change narration, not a current installation requirement. Assembly, rollback, native integrations and isolated acceptance instructions are retained in the bilingual development guides.

Validation: relative Markdown links checked, `git diff --check` passed. No native app was launched in this headless Linux documentation task, and no macOS/Windows runtime verification is claimed. Published asset availability is distinct from runtime acceptance. GitHub's public API returned HTTP 403, so public release HTML, tags and asset HTML were used instead. No credentials or user application state were inspected.

## Approved brand illustration

The user-approved nature illustration is saved at `docs/assets/bodhi-nature-hero.png`.
The original PNG was visually inspected and decoded, and its SHA-256 matched
the approved image package. It is a brand illustration, not a software screenshot;
the README alt text and visible caption say so. Existing source/release and
recording limits still apply. The older artwork remains in repository history
and any existing SVG asset is preserved.

- Pixels: 1672 × 941 (RGB PNG)
- Bytes: 1939284
- SHA-256: `e63928e03b038650b83ba6a259eef45057f3ff09271b7cb6e7aa273822cdb08f`
