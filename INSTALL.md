### [GitKraken Kepler](https://www.gitkraken.com/)

This package is the Dracula theme family for **GitKraken Kepler** (`schemaVersion` 2). It is not the classic GitKraken theme.

The classic JSONC files (`dracula-theme.jsonc` and `dracula-theme-soft.jsonc`) live in [dracula/gitkraken](https://github.com/dracula/gitkraken) and install into `~/.gitkraken/themes`. Kepler reads a different file, from a different folder. Installing one does not install the other.

`themes/dracula/dracula.json` holds both variants:

| Id | Name | Appearance |
| --- | --- | --- |
| `dracula-classic` | Dracula | Dark. Dracula Classic. |
| `alucard-classic` | Alucard | Light. Alucard Classic. |

`themes/dracula/gallery.json` is listing data for a future [Kepler gallery](https://github.com/gitkraken/kepler-themes) pull request. Kepler does not read it locally.

#### Install using Git

If you are a Git user, you can install the theme and keep it up to date by cloning the repo:

```bash
git clone https://github.com/fits-ki/kepler.git
```

#### Install manually

Download using the [GitHub `.zip` download](https://github.com/fits-ki/kepler/archive/refs/heads/main.zip) option and unzip it.

#### Activating theme

1. Copy `themes/dracula/dracula.json` into Kepler's themes folder. The file can keep that name, or any other `.json` name. Do not put it in a subfolder.
   - macOS and Linux: `~/.kepler/themes`
   - Windows: `%USERPROFILE%\.kepler\themes`
2. Create the folder if it is not there yet. In Kepler, **Settings → Appearance → Your themes → Open themes folder** opens the same directory.
3. Return to **Settings → Appearance**. Under **Your themes**, choose **Dracula** or **Alucard**.
   - **System** follows the OS. The moon on a tile is the dark theme and the sun is the light theme. Click the tile itself to use that family for both.
   - **Dark** or **Light** locks the appearance. Click a tile to use it.

Kepler reads up to 64 `.json` or `.jsonc` files from that folder and reloads a file when you save it. If a tile says **Has problems** or **Has warnings**, open the badge. The message names the token that failed.

#### What you get

- **Dracula** uses the Dracula Classic palette: background `#282A36`, foreground `#F8F8F2`, and the standard pink, green, cyan, yellow, orange, red, and purple syntax colors.
- **Alucard** uses the Alucard Classic palette: background `#FFFBEB` and the light-theme syntax colors from the [specification](https://draculatheme.com/spec).

A few roles are shifted just enough to clear Kepler's contrast check. The list is in [SUBMISSION.md](./SUBMISSION.md). Syntax colors stay on the specification except Dracula comments, which are a lighter step of `#6272A4`.
