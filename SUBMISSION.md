# Submission prep

Do not open the Dracula issue from this file. It is a checklist and a draft for a person to file later.

Repository: https://github.com/fits-ki/kepler

This is the **GitKraken Kepler** port (`schemaVersion` 2). It is not an update to the classic GitKraken JSONC themes in https://github.com/dracula/gitkraken.

## Checklist

Compared with https://draculatheme.com/contribute and https://draculatheme.com/spec.

- [x] Built from the Dracula template shape: `README.md`, `INSTALL.md`, `CONTRIBUTORS.md`, `screenshot.png`, `LICENSE` (MIT), `.github/dracula-pro.png`.
- [x] `README.md` titles the port "Dracula for GitKraken Kepler", points Install at https://draculatheme.com/kepler, and credits Tobias Feigel (`Mr56k`) plus the core team (Zeno Rocha, Lucas de França).
- [x] `INSTALL.md` tells people to copy `themes/dracula/dracula.json` into `~/.kepler/themes` or `%USERPROFILE%\.kepler\themes`, then pick **Dracula** or **Alucard** under **Settings → Appearance → Your themes**.
- [x] Install text distinguishes this family from [dracula/gitkraken](https://github.com/dracula/gitkraken).
- [x] Clone URL in Install is `https://github.com/fits-ki/kepler.git`.
- [x] Two themes in one family: `dracula-classic` (Dracula, extends dark) and `alucard-classic` (Alucard, extends light).
- [x] Syntax tokens follow the spec mapping (keywords pink, functions green, types cyan, strings yellow, numbers orange, comments italic, `this`/`self`/`super` purple italic, diff colors, foreground for variables and punctuation).
- [x] Terminal ANSI uses the spec lists, with the exceptions in [Contrast nudges](#contrast-nudges).
- [x] `themes/dracula/gallery.json` is ready for a later pull request to [gitkraken/kepler-themes](https://github.com/gitkraken/kepler-themes).
- [x] Family JSON parses, uses two-space indent, and ends with a newline.
- [x] Checked with Kepler's gallery validator (`vendor/kepler-theme-check.mjs` from gitkraken/kepler-themes, Kepler `0.15.0`): no errors, no notices, no reserved ids, no contrast failures.
- [x] `sample/` is gone. Those template leftovers do not ship with this repository.
- [x] `screenshot.png` is a real capture of GitKraken Kepler 0.16.0 on macOS with Dracula Classic (`dracula-classic`) active, showing the Todo dashboard.
- [ ] After the Dracula team accepts the port, they transfer the repository into the organization. Update the contributors link in `README.md` if the repo moves to `dracula/kepler`.
- [ ] Optional, after acceptance: open a pull request on gitkraken/kepler-themes that adds `themes/dracula/dracula.json` and `themes/dracula/gallery.json` only. That folder must not contain images or docs.

## Gallery tags

`tags.json` in gitkraken/kepler-themes (fetched while building this port) allows:

`purple`, `blue`, `green`, `red`, `orange`, `yellow`, `pink`, `teal`, `brown`, `gray`, `warm`, `cool`, `muted`, `vivid`, `high-contrast`, `pastel`, `retro`, `minimal`.

`dark`, `cyan`, `magenta`, and `vibrant` are not in that list. This family uses five valid tags: `purple`, `pink`, `vivid`, `retro`, `muted`. `vivid` is the catalog name closest to vibrant. `muted` is the last preferred tag that exists; Dracula is vivid first, and `muted` is only there so the file uses a fifth legal tag from the requested set.

## Contrast nudges

Kepler requires 4.5:1 for text and syntax, and 3:1 for highlights, lanes, and the dormant ring. Spec colors were kept wherever that check passed. The validator (`checkThemeFamily`) is clean only with the shifts below. No other hex values were invented.

Surfaces:

- Dracula uses Background Darker `#191A21`, Background Dark `#21222C`, Background `#282A36`, and Floating `#343746`.
- Background Lighter `#424450` is the usage track, not a surface. Purple `#BD93F9` is 4.00:1 on it, under the text floor.
- Alucard surfaces stay on Background `#FFFBEB`. Floating `#EFEDDC` and the darker UI steps drop Yellow `#846E15` and Red `#CB3A2A` under 4.5:1, so they are not surfaces. `#DEDCCF`, `#CECCC0`, and `#CFCFDE` are used for tracks and the terminal selection, where the check allows them.
- Functional colors (`#DE5735`, `#A39514`, `#089108`, `#0081D6`, `#815CD6`) are not used. On these surfaces they miss 4.5:1. Status colors use each variant's palette Green, Cyan, Orange, Pink, Red, and Purple instead.

| Role | Spec | Shipped | Why |
| --- | --- | --- | --- |
| Dracula comment, ANSI bright black, dormant ring, scrollbar thumb | `#6272A4` | `#8390B7` | 3.03:1 on `#282A36`. Same hue, mixed toward white until code plates clear 4.5:1. |
| Dracula `code-selection` | `#44475A` | `#80828F` | 1.56:1 against the code plate (needs 3:1). Current Line `#6272A4` is 3.03:1 against the plate, but neither foreground nor background-dark ink clears 4.5:1 on it. `#80828F` keeps the selection hue. Terminal selection stays `#44475A`. |
| Dracula `status-danger` | `#FF5555` | `#FF8080` | `#FF5555` is 3.75:1 on Floating `#343746`. ANSI bright red `#FF6E6E` is 4.33:1 on the 4% alert tint. `#FF8080` clears that tint. Syntax `diff.minus` stays `#FF5555`. |
| Dracula brand and brand fill | `#BD93F9` | `#CDADFA` | Purple is 3.77:1 as text on its own 15% tint. Hover and brand-fill hover use spec ANSI bright blue `#D6ACFF`. |
| Alucard `code-selection` | `#CFCFDE` | `#6C664B` | Selection is 1.49:1 against `#FFFBEB`. Current Line / Comment `#6C664B` clears 3:1 against the plate and 4.5:1 under the light highlight ink. Terminal selection stays `#CFCFDE`. |
| Alucard ANSI slot 0 | `#FFFBEB` | `#1F1F1F` | Spec ANSI black is the paper color. Kepler exempts slots 7 and 15 on a light theme and requires slot 0 to contrast, so slot 0 uses Foreground (spec ANSI white). Slots 7 and 15 stay `#1F1F1F` and `#2C2B31`. |
| Alucard ANSI bright red | `#D74C3D` | `#CA4839` | 4.06:1 on `#FFFBEB`. |
| Alucard ANSI bright green | `#198D0C` | `#18860B` | 4.17:1 on `#FFFBEB`. |
| Alucard ANSI bright yellow | `#9E841A` | `#897217` | 3.51:1 on `#FFFBEB`. |
| Alucard ANSI bright cyan | `#047FB4` | `#047BAF` | 4.31:1 on `#FFFBEB`. |
| Alucard diff washes | palette green and red | same hues at alpha `0E` | A stronger wash drops the removed-line number under 4.5:1. |

Line-highlight fallbacks from the spec (`#353747`, `#E2DECA`) are not theme tokens. Both are under 3:1 against their backgrounds, so Kepler's opaque `code-selection` cannot use them.

## Draft issue

File this on https://github.com/dracula/dracula-theme/issues. `sample/` is already gone, and `screenshot.png` is a real Kepler capture of Dracula Classic. Do not file it from automation.

**Title**

```
New theme: Dracula for GitKraken Kepler
```

**Body**

```markdown
## Application

GitKraken Kepler, the new theme-family format (`schemaVersion` 2).

This is not the existing classic GitKraken port. That one is https://github.com/dracula/gitkraken and ships JSONC themes (`dracula-theme.jsonc`, `dracula-theme-soft.jsonc`) for `~/.gitkraken/themes`. Kepler loads a single family file from `~/.kepler/themes`.

## Repository

https://github.com/fits-ki/kepler

## Variants

- Dracula (`dracula-classic`) — Dracula Classic, dark, extends `dark`
- Alucard (`alucard-classic`) — Alucard Classic, light, extends `light`

Both follow https://draculatheme.com/spec. Syntax mapping: keywords and tags pink, functions green, types and regex cyan, strings yellow, numbers and constants orange, comments italic, instance words (`this` / `self` / `super`) purple italic.

## Maintainer

Tobias Feigel — https://github.com/Mr56k

## Contrast

Kepler checks text at 4.5:1. A few spec colors miss that floor on these surfaces, so those roles use the nearest step that passes. The list is in `SUBMISSION.md` in the repository (comment `#6272A4` → `#8390B7` on Dracula, brand purple slightly lifted, Alucard ANSI bright colors darkened a few steps, Alucard code selection uses Current Line `#6C664B` because Selection `#CFCFDE` is 1.49:1 against the background). Everything else is a spec hex.

## Template

`README.md`, `INSTALL.md`, `screenshot.png`, and `LICENSE` match the Dracula template. `sample/` was removed before this issue. Install steps are for Kepler, and the Install link points at https://draculatheme.com/kepler as the page to publish after the repository is transferred.
```

## After acceptance

The Dracula team moves accepted repositories under the Dracula organization and grants the maintainer access. The website updates on a later rebuild, not at the moment the issue is accepted.

A Kepler gallery pull request is separate. Copy only `themes/dracula/` into a fork of https://github.com/gitkraken/kepler-themes and run `node scripts/check.mjs` there (Node 24.2 or newer). Theme ids `dracula-classic` and `alucard-classic` should stay stable once anyone is using them.
