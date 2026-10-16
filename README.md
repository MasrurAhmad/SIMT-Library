# Uni Library

A free, shared library of university study materials. It costs nothing to run: a static website on GitHub Pages, with the catalog stored as data files in this repository.

- **No server, no database, no card.** Nothing to crash, pause, or bill you.
- **Files are linked, not hosted.** Each entry points to a file kept by whoever shared it.
- **Moderated.** Submissions arrive as GitHub issues and a moderator adds the good ones.

Built with [Astro](https://astro.build) (static output). This is Step 1: a plain, fast baseline. Search, the moderator helper and the "4D" design come in later steps (see `PROGRESS.md`).

## Run it on your computer

You need Node.js 22.22 or newer.

```sh
npm install
npm run dev        # opens http://localhost:4321
```

Other commands: `npm run validate` (check the catalog), `npm run build` (make the site in `dist/`), `npm run preview` (view the built site).

## Put it online for free (GitHub Pages)

1. Create a free GitHub account if you do not have one.
2. Create a new **public** repository. Its name becomes part of the web address: `https://YOUR-NAME.github.io/REPO-NAME/`.
3. Add these files to the repository (see "Upload the files" below).
4. In the repository go to **Settings > Pages**. Under **Build and deployment**, set **Source** to **GitHub Actions**.
5. Open the **Actions** tab. The workflow "Check, build and deploy" runs on every push to `main`. When it turns green, your site is live at the address above. If it ran before you changed the Pages setting, open it and press **Re-run all jobs**.

### Upload the files

With Git installed:

```sh
git init
git add .
git commit -m "Step 1: scaffold"
git branch -M main
git remote add origin https://github.com/YOUR-NAME/REPO-NAME.git
git push -u origin main
```

Without Git: on the repository page choose **Add file > Upload files** and drag in the contents of this folder (not the folder itself). Make sure the hidden `.github` folder is included; if it is not, the site will not deploy. You can instead create `.github/workflows/deploy.yml` with **Add file > Create new file** and paste its contents.

## Add a material

1. Open `src/data/materials.json` and copy an existing entry.
2. Change every field. Use only links that open without logging in, and only material that follows the content policy (`src/pages/policy.md`).
3. Run `npm run validate`. It tells you exactly what is wrong, if anything.
4. Commit. The site updates by itself in a minute or two.

Courses live in `src/data/courses.json`. The sample entries (`"sample": true`) show a banner on every page. Delete them, and the banner disappears, once real material is in.

## Folder map

| Path | What it is |
| --- | --- |
| `src/data/` | The catalog: courses and materials |
| `src/pages/` | One file per page |
| `src/layouts/`, `src/components/` | Shared page frame and small building blocks |
| `src/styles/global.css` | All styling |
| `scripts/validate-catalog.mjs` | Catalog checker, runs before every build |
| `.github/workflows/deploy.yml` | Checks, builds and publishes the site |
| `.github/ISSUE_TEMPLATE/` | The submission and report forms |

## Limits to know

GitHub Pages is free for public repositories. A published site may be at most 1 GB, with a soft limit of about 100 GB of traffic a month. Linking to files (instead of storing them here) keeps you far below both.

## Before real material goes in

Ask your department or a professor what may be shared, finish the content policy, and add a takedown contact to it. Add a license file before accepting outside contributions.
