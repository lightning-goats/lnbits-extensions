# Lightning Goats — LNbits Extensions

A single extension **source** for the [Lightning Goats](https://github.com/lightning-goats)
LNbits extensions. Add one URL to LNbits and every extension below becomes
installable from the Extensions manager.

## Install (add the source)

**Admin UI:** Server → *Extension Sources* → **Add**, paste:

```
https://raw.githubusercontent.com/lightning-goats/lnbits-extensions/main/extensions.json
```

then Save. The extensions appear under **Extensions**; click *Install* / *Enable*.

**Or via environment variable** (`.env`), add the URL to the comma-separated list:

```
LNBITS_EXTENSIONS_MANIFESTS="https://raw.githubusercontent.com/lnbits/lnbits-extensions/main/extensions.json,https://raw.githubusercontent.com/lightning-goats/lnbits-extensions/main/extensions.json"
```

Restart LNbits.

## Extensions in this source

| id | name | repository |
|----|------|------------|
| `incomereport` | Income Report | [incomereport_extension](https://github.com/lightning-goats/incomereport_extension) |
| `lightning_goats` | Lightning Goats | [lightning_goats_extension](https://github.com/lightning-goats/lightning_goats_extension) |
| `cyberherd` | Cyberherd | [cyberherd_extension](https://github.com/lightning-goats/cyberherd_extension) |
| `nsecbunker` | Nsec Bunker | [nsecbunker](https://github.com/lightning-goats/nsecbunker) |

## How it works

`extensions.json` is an LNbits manifest. Each entry under `repos` points at an
extension repository by `{id, organisation, repository}`. LNbits reads that
repo's **GitHub Releases**, loads `config.json` at the release tag, and installs
from the release archive.

## Adding or updating an extension

1. Make sure the extension repo has a valid `config.json` at its root
   (`name`, `short_description`, `tile`, `version`, `min_lnbits_version`).
2. Cut a **GitHub Release** on that repo, tagged `v<version>` (e.g. `v0.1.0`).
3. Add a `repos` entry here (for a new extension). Updating an existing one only
   needs a new release — this file does not pin versions.

Requires LNbits ≥ 1.3 (Extension Sources / manifest install).
