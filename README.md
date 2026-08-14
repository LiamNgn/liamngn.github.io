# liamngn.github.io

Personal website of Liam Nguyen — <https://liamngn.github.io>

Built with [Hugo](https://gohugo.io/) and the [Bear Cub](https://github.com/clente/hugo-bearcub) theme.

## Local setup

The theme is a git submodule, so clone with it:

```bash
git clone --recurse-submodules https://github.com/LiamNgn/liamngn.github.io.git
# already cloned without it:
git submodule update --init --recursive
```

Run the dev server (drafts included):

```bash
hugo server -D
```

Build:

```bash
hugo --gc --minify
```

## Layout

- `content/_index.md` — home / about page
- `content/posts/` — all posts (the only content section)
- `static/images/` — favicon and social share image
- `hugo.toml` — site config
- `.github/workflows/hugo.yml` — builds and deploys to GitHub Pages on push to `main`

`public/` and `resources/` are build output and are not tracked; CI regenerates them.

## Publishing

Posts in `content/posts/` are synced from Obsidian by a publisher bot (commits tagged
`[PUBLISHER] MERGE` / `PUSH NOTE`). Edit those notes in the vault — changes made directly
in this repo get overwritten on the next sync.
