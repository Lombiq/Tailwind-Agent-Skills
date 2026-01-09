# Tailwind CSS v4 gotchas (quick scan)

- Browser support is modern-only: Safari 16.4+, Chrome 111+, Firefox 128+.
- PostCSS plugin moved to `@tailwindcss/postcss`.
- CLI moved to `@tailwindcss/cli`.
- Vite plugin `@tailwindcss/vite` is recommended.
- Import Tailwind with `@import "tailwindcss";` (no `@tailwind` directives).
- Prefix syntax is `@import "tailwindcss" prefix(tw);` and classes use `tw:` at the start.
- Important modifier goes at the end: `bg-red-500!`.
- Utility renames and removals: see `references/docs/upgrade-guide.mdx` for the full list.
- Default border and ring color now use `currentColor`; ring width default is 1px.
- `space-*` and `divide-*` selectors changed; use flex/grid with `gap` if layouts break.
- Custom utilities should use `@utility` instead of `@layer utilities` or `@layer components`.
- Stacked variants apply left-to-right (reverse order from v3).
- Arbitrary CSS variable syntax is `bg-(--brand-color)` (not `bg-[--brand-color]`).
- Transform reset uses `scale-none`, `rotate-none`, `translate-none` (not `transform-none`).
- `hover:` now only applies on devices that support hover; override if needed.
- CSS modules and component `<style>` blocks need `@reference` to access theme vars.
