# AGENTS.md

Working notes for AI agents and humans contributing to this repository.

## What this repository is

Source artwork for **The Kitsu Stickers**, a Telegram sticker pack starring the
mascot *Kitsu*.

- Pack on Telegram: <https://t.me/addstickers/TheKitsuStickers>
- License: CC BY-SA 4.0 — see [`LICENSE.md`](LICENSE.md).
- Sticker catalog: the table in [`README.md`](README.md).

Every sticker is stored as WebP, flat in the repository root — there is no
`assets/` or `images/` directory. Each sticker ships at two sizes: a 512px
render and a full-resolution master.

## File naming

```
<NN>_<slug>_v<N>[_<variant>]_<size>.webp
```

| Part | Meaning |
|------|---------|
| `NN` | Two-digit sticker number. `00` is the pack icon; `01`–`49` are the pack slots. |
| `<slug>` | Lowercase name of the sticker (`celebration`, `willy_wonka`). |
| `v<N>` | Variant index. A slot can ship several designs (`v1`, `v2`, …). |
| `<variant>` | Optional qualifier, used when variants need a name (`no_hat`, `hat`, `gentoo_smile`). |
| `<size>` | `512px` or `full`. The pack icon uses `100px` instead of `512px`. |

Examples:

```
00_pack_icon_v1_heart_100px.webp     pack icon, 100px
00_pack_icon_v1_heart_full.webp       pack icon, master
01_celebration_v1_512px.webp          sticker 01, variant v1, 512px render
01_celebration_v1_full.webp           sticker 01, variant v1, master
```

## Rules

### 1. Keep the `README.md` catalog in sync

The table in `README.md` is the catalog of the pack. Whenever a sticker file is
added, removed, renamed, or renumbered, update the matching row in the same
change:

- one row per sticker number, ordered ascending;
- the preview cell shows every 512px render of that sticker, side by side;
- the row's name stays in sync with the file's `<slug>`;
- no row may point at a file that does not exist, and no 512px render may be
  left out of the catalog.

### 2. One commit per sticker

Every file sharing a number — all variants, both the 512px and the master
render — is staged and committed together. Never split one sticker across
commits, and never mix two sticker numbers into one commit.

### 3. Commit message format

```
<type>(<scope>): <subject>

<body>
```

- `type` — `feat` for a new sticker, `fix` for a corrected render, `chore` for
  repo housekeeping, `docs` for documentation-only changes.
- `scope` — `stickers` for artwork; omit it for repo-wide changes.
- `subject` — imperative, lowercase, at most 72 characters, no trailing
  period.
- `body` — optional, but a sticker commit should list the variants it adds.

```
feat(stickers): add 02_willy_wonka

Adds 2 variants:
- v1_no_hat (512px + full renders)
- v2_hat (512px + full renders)
```

### 4. Follow the naming convention

New sticker files must match the grammar above. `<size>` is only `512px` or
`full` (`100px` for the pack icon). Numbers are zero-padded to two digits and
are never reused or renumbered — a number identifies a slot in the Telegram
pack for good.

### 5. Don't re-encode the artwork

The WebP files are the source of truth. Do not re-compress, resize, or convert
them without being asked: it changes bytes for no gain and quietly breaks
consistency with the catalog previews.

### 6. Leave `LICENSE.md` alone

It holds the verbatim Creative Commons Attribution-ShareAlike 4.0 International
legal code. Do not edit, shorten, or reformat it. The attribution note and the
third-party-rights caveat live at the bottom of `README.md`.

### 7. Don't push or publish

Commits are made locally on `master`. Pushing to GitHub, tagging a release, and
updating the live Telegram pack are human-initiated actions — do them only
when explicitly asked.
