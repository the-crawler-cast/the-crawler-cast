# AGENTS.md — The Crawler Cast (public repo)

Guide for AI agents working in **this repository** — the public-facing communication repo for *The Crawler Cast: Your Death Is Sponsored*.

Game source code lives in the private **showrunner** repo (Godot). **Never** commit source code, build artifacts, or secrets here.

---

## Repository role

| Repo | Visibility | Contents |
|------|------------|----------|
| **the-crawler-cast** (this repo) | Public | Devlogs, CHANGELOG, press kit, GitHub Pages |
| **showrunner** (parent monorepo) | Private | Godot project, CI test builds, gameplay code |

When cloned as a submodule inside showrunner, this directory is `public/`.

**Distribution:** Steam (players) · test builds on private showrunner releases · this repo is **comms only**.

---

## Language & localization

### Default: English

All documentation and outward-facing communication in this repo is written in **English** by default:

- `README.md`, `CHANGELOG.md`, `index.md`, `identity.md`
- Devlogs, press pages, announcements
- GitHub Issues / release notes intended for a global audience

### French companion file (required)

Every editorial document must ship with a **French translation** as a sibling file:

| Canonical (EN) | French pair |
|----------------|-------------|
| `devlogs/02-combat-beta.md` | `devlogs/02-combat-beta.fr.md` |
| `press/factsheet.md` | `press/factsheet.fr.md` |
| `announcements/steam-wishlist.md` | `announcements/steam-wishlist.fr.md` |

**Naming:** same basename + `.fr` before the extension → `xx.fr.md`  
Do **not** use `xx-fr.md`, `fr/xx.md`, or French-only filenames without an English canonical file.

**Rules:**

1. **Unsuffixed file = English** — the reference version for Pages, RSS, and international comms.
2. **Both files must exist before push** — do not publish EN without FR (if drafted in FR first, translate to EN; EN becomes canonical).
3. **Equivalent content**, not word-for-word — adapt tone and wordplay (tagline: *Your death is sponsored* / *Votre mort est sponsorisée*). Identity vocabulary: see `identity.md` (+ `identity.fr.md` when added).
4. **CHANGELOG:** [Keep a Changelog](https://keepachangelog.com/) format in English. Optional `CHANGELOG.fr.md` for local comms if needed.
5. **This AGENTS.md** is in English because it governs this repo; the private showrunner `AGENTS.md` stays in French.

---

## Repository layout

```
README.md           Project landing (EN)
identity.md         Brand & vocabulary (EN + identity.fr.md)
CHANGELOG.md        Version history (EN)
index.md            GitHub Pages home
_config.yml         Jekyll / Pages config
devlogs/            Numbered dev posts (EN + .fr.md pairs)
press/              Factsheet, screenshots (EN + .fr.md where prose)
releases/           Release notes pointers (no binaries here)
.github/workflows/  Pages deploy
```

**Forbidden in this repo:**

- Godot source (`.gd`, `.tscn`, `.tres`, `project.godot`)
- Build outputs (`.exe`, `.pck`, `.zip` of game builds)
- Internal codenames or paths that expose private infra unnecessarily
- Secrets, tokens, `.env`

---

## Sync from showrunner (optional)

When working from the private monorepo, templates may live in `tools/public-repo/` and sync via:

```bash
# From showrunner root
./tools/publish_public.sh public/
cd public && git add -A && git commit -m "docs: …" && git push
cd .. && git add public && git commit -m "chore: bump public submodule"
```

Edit **English + `.fr.md` pairs** before sync. Do not rely on the script to generate translations.

Architecture details (CI, two-repo flow): see showrunner `docs/github-org.md` (private).

---

## Writing guidelines

### Voice

Satirical broadcast / agency tone — disposable “actors”, live dungeon spectacle, audience over heroism. Match the identity doc; avoid generic fantasy MMO wording.

### Devlogs

- Numbered: `devlogs/NN-short-slug.md` + `devlogs/NN-short-slug.fr.md`
- Lead with player-facing news; technical depth is optional and secondary
- Status line: prototype / beta / upcoming Steam

### Commits (this repo)

Prefix style: `docs:`, `chore:`, `fix:` — e.g. `docs: devlog #2 combat beta (en/fr)`.

---

## Pre-push checklist

- [ ] Canonical text in **English**
- [ ] Matching **`xx.fr.md`** for every editorial markdown added or changed
- [ ] No game binaries or source leaked
- [ ] Links work on GitHub Pages (relative paths)
- [ ] CHANGELOG updated for user-visible releases

---

## Issues & feedback

| Topic | Where |
|-------|--------|
| Player feedback, comms, wishlist | **this repo** (public Issues) |
| Bugs, code, CI, exports | **showrunner** (private — org access) |
