# @inkless/theme-blog-first

Inkless **blog-first** theme — personal-blog home, author page, header/footer chrome, reading-room tokens.

| | |
|--|--|
| Theme id | `blog-first` |
| Contract | `1` (`inkless.theme.json#contractVersion`) |
| Host facade | `@inkless/theme-host` only (runtime: `window.InklessThemeHost`) |

## Develop

```bash
pnpm install
pnpm test
pnpm build   # → dist/theme.umd.js + theme.es.js
```

Types for `@inkless/theme-host` are ambient (`types/theme-host-shim.d.ts`) so this package type-checks without the Inkless monorepo.

## Consumed by Inkless host

**Built-in (monorepo / git dependency)**

```ts
import { blogFirstTheme } from "@inkless/theme-blog-first";
themeManager.registerBuiltIn(blogFirstTheme);
```

**Remote UMD**

Host exposes React peers + `InklessThemeHost`, then loads `dist/theme.umd.js` which calls:

```js
window.__INKLESS_THEME_REGISTER__(themePlugin);
```

See Inkless monorepo `docs/theme-contract.md`.

## Layout

```
src/
  index.ts           # ThemePlugin export
  register.ts        # UMD auto-register
  chrome/            # BlogHeader / BlogFooter
  pages/home.tsx
  pages/author.tsx
inkless.theme.json
types/theme-host-shim.d.ts
```
