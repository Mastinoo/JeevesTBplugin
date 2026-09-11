# Jeeves Chat

Jeeves Chat is a GWToolbox++ plugin for linked Guild Wars alliance communities. It makes Jeeves-relayed alliance chat look closer to native chat and gives linked opposite-faction guilds an immediately recognisable native overhead guild tag.

## What it does

- Restores the original player as the visible sender of Jeeves-relayed alliance chat, keeping the player name clickable.
- Colors relayed chat guild tags by source faction:
  - **Kurzick:** `#5AA8FF`
  - **Luxon:** `#FF4040`
- Colors the complete native overhead **[TAG]**, including brackets, for players in the linked **opposite faction**:
  - **Opposite Kurzick:** `#B07CFF`
  - **Opposite Luxon:** `#FF4040`
- Leaves the character-name color unchanged.
- Leaves your own linked faction on Guild Wars' normal nameplate colors.
- Uses ArenaNet's native nameplate itself, so normal nameplate stacking, highlighting, hiding and UI occlusion continue to work.
- Matches guilds by **guild identity / GHKey**, not by the visible guild tag string.
- Refreshes the read-only linked-alliance registry automatically.

## What it does not do

Jeeves Chat does not automate gameplay, move characters, use skills, recruit players, invite guilds or replace the Guild Wars nameplate with a custom overlay.

## Settings

The public settings panel is intentionally small:

- **Enable Jeeves Chat** — enables the relay-chat presentation and plugin behavior.
- **Color linked alliance overhead tags** — enables the native opposite-faction overhead `[TAG]` coloring.
- **What it does** — short visual explanation and faction color legend.
- **Status** — registry/community/faction state.
- **Advanced diagnostics** — compact counters for troubleshooting only.

## Installation

See [INSTALL.md](INSTALL.md).

## Compatibility note

GWToolbox++ plugins are binary plugins and may need to be rebuilt when the Toolbox plugin API changes. Always fully close Guild Wars before replacing a plugin DLL.

## Network use

Jeeves Chat periodically fetches a read-only alliance registry used to decide which guild identities belong to linked Kurzick/Luxon communities. The registry lookup is separate from Guild Wars gameplay automation.
