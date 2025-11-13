# Repository Guidelines

## Project Structure & Module Organization
This Hugo site keeps human-edited content in `content/` (section folders such as `projects`, `publications`, and the homepage `_index.md`). `archetypes/` stores the starter front matter for new content types, while `layouts/` and `themes/` hold shared templates and partials that render those pages. Reusable data lives in `data/`, localized strings in `i18n/`, and processed pipeline assets (Sass, JS) belong in `assets/`. Use `static/` for passthrough files like PDFs or favicons. Generated output lands in `public/` and `resources/`; never edit those by hand—clear them before releases if necessary. Global configuration is centralized in `hugo.toml`.

## Build, Test, and Development Commands
Run `hugo serve --buildDrafts --buildFuture --bind 0.0.0.0` for live development with drafts and future-dated posts included. Build the production site with `hugo --gc --minify` to garbage-collect unused resources and emit compressed HTML/CSS/JS into `public/`. Before publishing, use `rm -rf public && hugo` to ensure you are deploying a clean artifact.

## Coding Style & Naming Conventions
Write content in Markdown with TOML front matter; keep keys lowercase (`title`, `date`, `summary`) and prefer ISO-8601 dates. Name files and directories with lowercase-hyphenated slugs (e.g., `molecular-design.md`) to match Hugo’s routing. Templates and partials use two-space indentation and descriptive filenames such as `layouts/partials/hero.html`. Keep prose concise, using sentence case headings unless a proper noun dictates otherwise.

## Testing Guidelines
Treat `hugo --panicOnWarning --templateMetrics` as the regression test: it surfaces broken links, missing resources, and slow templates. Review the generated `public/` diff (e.g., `git status public`) before committing to make sure only intentional pages changed. For new components, verify responsive behavior locally by loading the served site in narrow and wide viewports.

## Commit & Pull Request Guidelines
Follow the established imperative tense seen in `git log` (e.g., "Add MolSelector project details", "Fix formatting …"). Keep messages under 72 characters on the subject line and describe user-facing changes; add details below if needed. Pull requests should summarize the change, reference related issues or content requests, include screenshots for visual tweaks, and mention how you validated the build.

## Security & Configuration Tips
Keep secrets and API keys out of `hugo.toml`, `data/`, and content files—use environment variables or deployment-specific config instead. When adjusting analytics or third-party embeds, document the required keys in the PR so deploy pipelines can be updated safely.
