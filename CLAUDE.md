# tbe_web

Personal website for Bo Motlagh, served at bomotlagh.com via GitHub Pages.

## Stack

- SvelteKit 2 on Svelte 4, TypeScript, Tailwind CSS 3, lucide-svelte icons
- `@sveltejs/adapter-static` prerenders the single route into `docs/`
- Package manager is Yarn (Berry, node-modules linker). Never use npm.

## Commands

```
yarn dev       # local dev server
yarn build     # prerender site into docs/
yarn preview   # serve the production build
yarn check     # svelte-check
```

## Layout

- `src/routes/+page.svelte` is the only page. It defines the five columns (About, Professional, News, UEV, Contact) and the accordion state.
- `src/lib/components/InteractiveColumn.svelte` renders one column: background image, expand/collapse behavior, and which content component mounts. Column identity is by numeric index, so adding or reordering a column means updating the image, opacity, and content mappings there too.
- `src/lib/components/*Content.svelte` hold the content for each column. Contact and Professional use LinkedIn/GitHub links; News is a hardcoded array of stories.
- `static/` is copied verbatim to the build root and served from `/`. Column backgrounds live in `static/backgrounds/`. News article images go in `static/news/` (kebab-case, 16:9, under 200KB, include source and year in the name, e.g. `technically-uev-launch-2025.jpg`).
- `docs/` is build output only. Never edit it by hand. It is committed because GitHub Pages serves from it, so rebuild and commit it when deploying. Expect hash churn in `docs/_app/` on every build.
- `archive2/` is the old Hugo site. It is gitignored and unrelated; ignore it.

## Conventions

- Make the smallest change that achieves the goal. Don't refactor unrelated code or duplicate existing functionality.
- Move files with `git mv` or `mv` rather than recreating them, and update imports afterward.
- When adding a new directory, document its purpose here.
- Components are PascalCase and use `<script lang="ts">`. Import shared code via `$lib`.
- Commit `yarn.lock` changes. Never commit `package-lock.json`.
