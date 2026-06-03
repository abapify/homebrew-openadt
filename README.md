# abapify/homebrew-openadt

Standard Homebrew tap for OpenADT. End users run:

```bash
brew tap abapify/openadt
brew install openadt
```

Homebrew resolves `abapify/openadt` to this repository (`homebrew-openadt`).

## One-time setup (maintainers)

1. Create a public repo **`abapify/homebrew-openadt`** (empty is fine).
2. Copy [homebrew-tap-mirror.yml](../homebrew-tap-mirror.yml) to `.github/workflows/sync-from-openadt.yml` in that repo and push.
3. On **`abapify/openadt`**, add secret **`OPENADT_HOMEBREW_TAP_TOKEN`**: fine-grained or classic PAT with `contents:write` on `homebrew-openadt`.
4. Seed the formula once (from a machine with the secret):

   ```bash
   OPENADT_HOMEBREW_TAP_TOKEN=<pat> bash tools/sync-homebrew-tap/sync.sh
   ```

   Or run the mirror workflow manually on `homebrew-openadt`.

Each OpenADT release runs `tools/sync-homebrew-tap/sync.sh` and dispatches `openadt-release` to the tap repo.

`Formula/openadt.rb` in the main **openadt** repo stays the release source of truth; this tap repo is a mirror for `brew tap abapify/openadt`.
