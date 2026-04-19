# senyangom.github.io

Personal website for Sen Yang — PhD, Operations Management, NYU Stern.

Built on Jekyll, structurally derived from the [academicpages](https://github.com/academicpages/academicpages.github.io) template (itself a fork of [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes), MIT-licensed). Original template © Stuart Geiger / © Michael Rose under MIT — see `LICENSE`.

## Local preview

```bash
bundle install
bundle exec jekyll serve
# → http://127.0.0.1:4000
```

## Deploy

This is a GitHub Pages user site. Pushing to the `main` branch of `SenYangOM/SenYangOM.github.io` triggers an automatic build. Site is served at <https://senyangom.github.io>.

## Edit pointers

| What | Where |
|---|---|
| Site config (title, author block, social links) | `_config.yml` |
| Homepage / About / News | `_pages/about.md` |
| Projects | `_pages/projects.md` |
| Publications + Working papers | `_pages/publications.md` |
| CV (web version) | `_pages/cv.md` |
| Contact | `_pages/contact.md` |
| Navigation order | `_data/navigation.yml` |
| Blog posts | `_posts/YYYY-MM-DD-slug.md` |
| Profile photo | `images/profile.jpg` (replace) |
| CV PDF | `files/SenYang-CV.pdf` (drop in once compiled) |

## TODO before launch

- [ ] Drop a real headshot at `images/profile.jpg`.
- [ ] Compile `senyang.tex` → `files/SenYang-CV.pdf`.
- [ ] Add Google Scholar URL to `_config.yml` once profile exists.
- [ ] Fill in the three blog post drafts in `_posts/`.
- [ ] (Optional) Set Google Analytics tracking_id.
