# BURM public updates

Public update manifest for the standalone BURM launcher.

## Feed URL

Configure the launcher with:

```sh
burm_launcher --manifest-url https://raw.githubusercontent.com/Akkowicz/burm-public/main/latest.json
```

You can also set `BURM_UPDATE_URL` or enter the same URL in the launcher settings.

## Replace the placeholders

`latest.json` starts with a placeholder Linux download. Installation will fail until you replace all three artifact fields:

- `url`: the HTTPS URL of the raw graphical game executable, with embedded assets (not an archive or the launcher).
- `sha256`: the executable's SHA-256 checksum as 64 hexadecimal characters. The initial all-zero value is a placeholder.
- `size`: the executable's exact size in bytes. The initial value of `1` is a placeholder.

Keep `version` equal to the game workspace release version and the downloaded executable's `--version` output. Add entries under `platforms` using the exact Rust target triples of other tested builds.

Upload the executable before updating the manifest. Publish each release at an immutable artifact URL, and update `latest.json` last. The launcher verifies the size, checksum and executable version before activating an install.

## Generate a release manifest

From the BURM source repository, after building a tested game executable:

```sh
python3 scripts/update-manifest.py \
  --base-url https://example.com/REPLACE_ME/burm \
  --binary x86_64-unknown-linux-gnu=target/dist/burm \
  --notes 'Release notes.' > latest.json
```

Replace the base URL with your actual hosting location. The script appends `VERSION/TARGET/burm` (`burm.exe` for Windows). Repeat `--binary TARGET=PATH` for additional tested platforms, then commit the generated manifest here.
