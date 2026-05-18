# Blogg Storage

Markdown blog storage for the Wigum Gaming homepage.

This repository contains the blog posts only. The website code lives in the separate homepage repository and fetches these Markdown files from GitHub at runtime.

It also contains dynamic page content used by the homepage, such as game metadata, preview images, and about-us page/member data.

Homepage repository:

```text
~/Documents/Code/Homepage/WigumGaming-Homepage
```

Blog storage repository:

```text
~/Documents/Code/Homepage/Blogg-Storage
```

If this repository is missing on a new machine, clone it with:

```sh
git clone git@github.com:OL3s/Blogg-Storage.git ~/Documents/Code/Homepage/Blogg-Storage
```

## Purpose

Use this repository when adding, editing, or removing development blog posts.

Do not add blog Markdown files to the homepage repository. The homepage expects to find posts here, in this repository, under the `games/` folder.

The repository should stay public so the static website can fetch posts without a GitHub token.

## Folder Structure

Posts are grouped by game slug.

```text
games/
  singleplayer-roguelite/
    index.md
    index.no.md
    image/
      index-landscape.png
      index-portrait.png
    blog/
      2026-05-09-p1-menu-and-character-setup.md
  multiplayer-arena/
    index.md
    index.no.md
    image/
      index-landscape.png
      index-portrait.png
    blog/
      2026-05-09-building-the-arena-foundation.md
      2026-05-10-player-items-and-damage-visuals.md
```

About page content lives outside `games/`:

```text
about-us/
  index.md
  index.no.md
  image/
    placeholder-member.svg
  members/
    ole-kristian-wigum.md
    ole-kristian-wigum.no.md
```

The about page reads `about-us/index.md` for the top page text and `about-us/members/*.md` for team members.

Member Markdown example:

```md
---
name: Ole Kristian Wigum
role: Founder and coder
image: placeholder-member.svg
---

First paragraph.

Second paragraph.
```

The `image` value points to a file inside `about-us/image/`.

Every direct subfolder under `games/` becomes a game page on the homepage. The folder name is used as the game `slug`.

## Game Metadata

Each game includes an `index.md` file for page text and repository details.

Example:

```md
---
name: MultiplayerArena
teaser: Fast 2D PvP arena fights where bullets, movement, and destruction decide the round.
githubRepo: OL3s/MultiplayerArenaV2
githubUrl: https://github.com/OL3s/MultiplayerArenaV2.git
---

A fast 2D arena fighter where movement, aim, and destructible maps shape every round.

Longer page description shown on the game detail page.
```

If `index.md` is missing, the homepage cannot load that game page content.

## Language Files

English is the default language and uses the normal `.md` filename. Translations use a language suffix before `.md`.

Current supported content languages:

```text
English/default = unsuffixed .md
Norwegian = .no.md
```

Examples:

```text
about-us/index.md
about-us/index.no.md
about-us/members/ole-kristian-wigum.md
about-us/members/ole-kristian-wigum.no.md
games/multiplayer-arena/index.md
games/multiplayer-arena/index.no.md
```

Fallback:

- If the selected language file exists, the homepage uses it.
- If it does not exist, the homepage uses the default English `.md` file.
- Blog posts are not localized yet and should keep the existing unsuffixed `.md` filenames.

Localized content currently applies to essential site content only:

- Game metadata pages: `games/<game-slug>/index.md` and `games/<game-slug>/index.no.md`.
- About page: `about-us/index.md` and `about-us/index.no.md`.
- Team members: `about-us/members/<member-slug>.md` and `about-us/members/<member-slug>.no.md`.
- Roadmap page and items: `about-us/roadmap/*.md` and `about-us/roadmap/*.no.md`.

Do not localize blog posts yet. Blog post files should stay like this:

```text
games/<game-slug>/blog/YYYY-MM-DD-short-title.md
```

Do not create blog post files like this unless the homepage app is updated to support localized blog posts:

```text
games/<game-slug>/blog/YYYY-MM-DD-short-title.no.md
```

## Adding A New Content Language

The homepage repository controls which languages exist in `src/services/i18n.js`. Add the language there first, then add matching content files here.

Required steps:

1. Choose a language code and keep it consistent, for example `de` for German.
2. Add the language code, display label, flag, and UI strings in the homepage repository at `src/services/i18n.js`.
3. Add translated Markdown files in this repository using `.<code>.md` before the extension.
4. Keep English/default files unsuffixed as `.md`.
5. Leave blog posts unsuffixed unless blog localization is explicitly implemented later.
6. Push this repository to `main` so the static homepage can fetch the content.

Required translated files for each language:

```text
about-us/index.<code>.md
about-us/members/<member-slug>.<code>.md
about-us/roadmap/index.<code>.md
about-us/roadmap/<roadmap-item>.<code>.md
games/<game-slug>/index.<code>.md
```

Example for German:

```text
about-us/index.de.md
about-us/members/ole-kristian-wigum.de.md
about-us/roadmap/index.de.md
about-us/roadmap/001-mob-gladiator.de.md
games/multiplayer-arena/index.de.md
```

Fallback means a new language can be added gradually. If `games/mob-arena/index.de.md` is missing, the homepage shows `games/mob-arena/index.md` instead.

Agent checklist for content language work:

1. Check the homepage `src/services/i18n.js` for supported language codes before creating translated files.
2. Use the exact same language code in filenames.
3. Never rename or delete the unsuffixed English/default `.md` file while adding a translation.
4. Keep front matter keys the same across language variants.
5. Keep image references shared unless a language-specific image is explicitly needed.
6. Do not commit or push unless the user explicitly asks for it.

Expected path pattern:

```text
games/<game-slug>/blog/<post-file>.md
```

Example:

```text
games/multiplayer-arena/blog/2026-05-10-player-items-and-damage-visuals.md
```

## Game Preview Images

Game preview images live next to the `blog/` folder in an `image/` folder.

Expected image paths:

```text
games/<game-slug>/image/index-landscape.<ext>
games/<game-slug>/image/index-portrait.<ext>
```

Image rules:

- Use `index-landscape` for the wide preview image.
- Use `index-portrait` for the square/mobile preview image.
- Landscape should be `2:1`.
- Portrait should be `1:1`.
- Supported extensions are `.avif`, `.webp`, `.jpg`, `.jpeg`, `.png`, and `.svg`.
- `main-landscape` and `main-portrait` are also supported as fallbacks, but `index-*` is preferred because it matches the folder entry point.

If a game has no image folder or no matching image file, the homepage shows a failed-to-fetch message until images are added.

## File Naming

Use this format:

```text
YYYY-MM-DD-short-title.md
```

Rules:

- Start with the post date.
- Use lowercase words.
- Separate words with hyphens.
- Keep filenames ASCII.
- Use `.md` only.

Good examples:

```text
2026-05-10-player-items-and-damage-visuals.md
2026-06-01-new-map-test.md
2026-07-15-combat-update.md
```

Avoid:

```text
New Blog Post.md
2026_05_10_update.md
player-items.md
```

## Post Format

Every post is a Markdown file with front matter at the top.

```md
---
title: "Post Title"
date: "2026-05-10"
excerpt: "Short summary shown before the full post is opened."
---

Write the blog post here.
```

Required fields:

- `title`
- `date`

Optional fields:

- `excerpt`

If `title` is missing, the homepage will generate a title from the filename. If `date` is missing, the homepage will try to use the date at the start of the filename. Still, always include both fields for clarity.

## Writing Style

Write posts for readers, not only for developers.

Guidelines:

- Lead with what changed and why it matters.
- Use plain language before technical details.
- Explain how the update affects the game feel, player experience, or development direction.
- Keep technical terms when they are useful, but explain them briefly.
- Use headings to split the post into readable sections.
- Use bullet lists for controls, feature lists, or short summaries.
- Avoid dumping implementation notes unless the post is specifically meant to be technical.

Good blog tone:

```text
The arena is starting to feel more alive. Players can now pick an item, use it in the test room, and see objects react as they take damage.
```

Too technical for a general update:

```text
The action request is validated by the host and propagated through the item execution path with synchronized directional state.
```

## Human Workflow: Adding A New Post

1. Choose the correct game slug.
2. Go to `games/<game-slug>/blog/`.
3. Create the folder if it does not exist.
4. Create a Markdown file named `YYYY-MM-DD-short-title.md`.
5. Add front matter with `title`, `date`, and optional `excerpt`.
6. Write the post body in Markdown.
7. Check spelling, headings, and that the post reads well for visitors.
8. Commit and push the change to `main`.

Example:

```sh
git add games/multiplayer-arena/blog/2026-05-10-player-items-and-damage-visuals.md
git commit -m "Add multiplayer arena item update"
git push
```

## Human Workflow: Editing A Post

1. Open the existing Markdown file.
2. Keep the filename stable unless the date or topic is wrong.
3. Update the front matter if the title or excerpt changes.
4. Keep the post readable and reader-focused.
5. Commit and push the edit.

## How The Homepage Reads Posts

The homepage fetches folders through the GitHub Contents API:

```text
https://api.github.com/repos/OL3s/Blogg-Storage/contents/games/<game-slug>/blog?ref=main
```

For each `.md` file in that folder, the homepage downloads the raw Markdown, parses the front matter, and renders the body.

Sorting:

- Posts are sorted newest first.
- The `date` front matter is used first.
- If `date` is missing, the date from the filename is used.

Publishing:

- Pushing to `main` publishes the content source.
- The homepage does not need a rebuild for normal blog text changes.
- Browser or CDN caching may delay visible updates briefly.

## AI Agent Instructions

When an AI agent is asked to add or update a blog post, follow this workflow.

1. Work in `~/Documents/Code/Homepage/Blogg-Storage`, not the homepage repo.
2. Read this README before editing.
3. Confirm the game slug from the user request or from the homepage app if needed.
4. Use `games/<game-slug>/blog/` for the post location.
5. Use `YYYY-MM-DD-short-title.md` for new filenames.
6. Include front matter with `title`, `date`, and `excerpt` when possible.
7. Keep the body reader-friendly unless the user specifically asks for a technical post.
8. Do not commit or push unless the user explicitly asks for it.
9. If committing, commit only relevant blog storage changes.
10. If pushing, push this repository, not the homepage repository.

## Quick Template

```md
---
title: "Readable Blog Title"
date: "YYYY-MM-DD"
excerpt: "One sentence summary for the updates list."
---

Short opening paragraph explaining what changed and why it matters.

## Main Update

Explain the most important part in plain language.

## What This Means

Explain how this affects the game or future development.

## Next Steps

Briefly mention what is likely coming next.
```
