# 🤝🏻 Contributors

> "We learn big things from small experiences" - **Bram Stoker**

Dracula Theme is an open-source project driven by and for the community. Most apps that support the theme are contributions from our community.

As much as the team is responsible for the core theme and wants to support all available applications, we can only do so much ourselves.

That's why the community is essential for this project to keep evolving. Below are some tips for contributors.

## 🎃 Recommendations

This repository is the Dracula port for GitKraken Kepler (the `schemaVersion` 2 theme family). It is organized like the [official template](https://github.com/dracula/template):

- [`README.md`](README.md): Introduction and guide for GitHub users.
- [`screenshot.png`](screenshot.png): Preview image displayed on [draculatheme.com](https://draculatheme.com).
- [`INSTALL.md`](INSTALL.md): Installation instructions to display on the website.
- [`themes/dracula/dracula.json`](themes/dracula/dracula.json): The Kepler theme family. Dracula Classic and Alucard Classic live in this one file.
- [`themes/dracula/gallery.json`](themes/dracula/gallery.json): Maintainer and tags for a later Kepler gallery pull request. Kepler does not load this file.

### Screenshots

Themes on [draculatheme.com](https://draculatheme.com) show a preview image on their page. You can provide one or more screenshots in two ways:

| Approach | When to use |
| --- | --- |
| [`screenshot.png`](screenshot.png) at the repo root | A single preview is enough (default and simplest option). |
| [`screenshot/`](screenshot/) folder with multiple images | You want to show different views, platforms, or variants (for example the editor, the terminal, Dracula, and Alucard). |

**Priority:** if the `screenshot/` folder contains at least one supported image, the website uses those files and ignores the root `screenshot.png`. If the folder is missing or empty, the site falls back to `screenshot.png`.

**Supported formats:** `.png`, `.jpg`, `.jpeg`, `.webp`, `.gif`

**Ordering:** images in `screenshot/` are sorted alphabetically by filename. Use numbered prefixes when order matters (for example `01-overview.png`, `02-settings.png`).

**Gallery:** when multiple images are present, the theme page renders an interactive gallery with thumbnails.

This repository ships a single root `screenshot.png`: a real capture of GitKraken Kepler 0.16.0 on macOS with Dracula Classic (`dracula-classic`) on the Todo dashboard. Do not add a `screenshot/` folder unless you want the site to prefer those images over the root file.

Previously, default formatting settings were included. Now, we recommend preparing your theme with this command:

```bash
npx prettier . --write
```

> What is that `npx` thing? `npx` ships with `npm` and lets you run locally installed tools.

The theme family file is plain JSON: two-space indent and a trailing newline. Do not run a formatter that rewrites it to a different shape. Kepler's gallery check rejects comments, trailing commas, and other JSONC syntax.

## 🦉 The Dracula Theme Team

The creators behind the scenes are [Lucas de França](https://github.com/luxonauta) and [Zeno Rocha](https://github.com/zenorocha).

This Kepler port is maintained by [Tobias Feigel](https://github.com/Mr56k).

Reach out via [email](mailto:support@draculatheme.com) or follow us on Twitter/X: [Zeno Rocha](https://twitter.com/zenorocha) and [Luxonauta (Lucas)](https://twitter.com/luxonauta).

## 🌐 How the website gets updated

Theme pages on [draculatheme.com](https://draculatheme.com) are generated at build time from the files in each theme repository (`README.md`, `INSTALL.md`, and screenshots). The website doesn't fetch this content live.

This means a merged pull request won't show up on the website right away; it appears after the next site rebuild. Rebuilds happen roughly once a week, usually in batches alongside other theme updates and maintenance fixes.

If your change needs to go live sooner, mention our team in the pull request and we may trigger a rebuild manually.
