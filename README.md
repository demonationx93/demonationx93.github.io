# Personal Academic Website

A minimal, content-first academic CV and article site built with Astro. It is designed for static deployment to GitHub Pages and uses Astro Content Collections for typed Markdown articles.

## Development

Requires Node.js 22.12 or newer.

```bash
npm install
npm run dev
```

Astro prints the local URL, normally `http://localhost:4321`.

## Production build

```bash
npm run build
npm run preview
```

The static site is written to `dist/`.

## Content editing

- Edit identity, contact links, and the profile image path in `src/config/profile.ts`.
- Edit global titles, descriptions, author, and locale in `src/config/site.ts`.
- Edit biography, research interests, education, experience, publications, projects, and awards in `src/data/cv.ts`.
- Add and edit long-form writing in `src/content/articles/`.
- Set the production URL and optional repository base path in `site.config.mjs`.

All included CV entries and articles are labeled sample content. Empty link values are intentionally hidden instead of pointing to invented accounts.

## Adding an article

Create a Markdown file in `src/content/articles/`. The filename becomes the URL slug.

```yaml
---
title: "Article title"
description: "A concise description for the archive and search metadata."
publishedAt: 2026-09-04
updatedAt:
tags:
  - Security
  - Research
draft: false
featured: false
---
```

Set `draft: true` to exclude an article from generated routes, the archive, sitemap, and RSS. Markdown supports footnotes, syntax-highlighted code, tables, and inline or block math such as `$E = mc^2$`.

## Profile photo and CV

Replace `public/profile-placeholder.svg` with a portrait, ideally a 4:5 image. Either keep that filename or update `profile.portrait` and `profile.portraitAlt` in `src/config/profile.ts`.

To add a downloadable CV, place the PDF in `public/` and set `profile.cv` to `/your-cv.pdf`.

## GitHub Pages

1. Replace `USERNAME` in `site.config.mjs`.
2. For a user site repository named `USERNAME.github.io`, leave `basePath` as `/`.
3. For a project repository, set `basePath` to `/REPOSITORY_NAME`.
4. Push the repository to GitHub and enable **Settings → Pages → Source → GitHub Actions**.
5. Push to `main` or run the included workflow manually from the Actions tab.

The workflow in `.github/workflows/deploy.yml` builds the site and publishes `dist/` using GitHub’s official Pages actions.

## Project structure

```text
src/
├── components/       Reusable CV and article presentation
├── config/           Profile and site metadata
├── content/articles/ Markdown article source
├── data/             Editable CV data
├── layouts/          Shared document and article layouts
├── lib/              Date, URL, and reading-time helpers
├── pages/            Homepage, archive, articles, and RSS
└── styles/           Global design tokens and base styles
```
