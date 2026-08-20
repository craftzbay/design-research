# Design Tokens

## Яагаад

Hex, px утгуудыг код даяар тараавал theme солих, брэнд өөрчлөх боломжгүй болдог. Token = утгын **нэрлэсэн давхарга**; бүх стил token-оор дамжина.

## Гурван давхаргын архитектур

```
Primitive  →  Semantic  →  Component (заавал биш)
blue-600      --color-accent   --button-bg
gray-50       --color-bg       --card-bg
```

1. **Primitive** — түүхий утгууд: `--blue-600: #2563eb`, `--space-4: 16px`. Шууд UI-д хэрэглэхгүй.
2. **Semantic** — утга учиртай нэр: `--color-bg`, `--color-surface`, `--color-border`, `--color-fg`, `--color-fg-muted`, `--color-accent`, `--color-danger`. **UI бүхэлдээ энэ давхаргаас уншина.**
3. **Component** — том системд л хэрэгтэй: `--button-primary-bg`. Жижиг проектод алгасаж болно.

## Наад захын semantic багц

```css
:root {
  /* фон */
  --bg: ...;            /* хуудасны суурь (60%) */
  --surface: ...;       /* card, panel (30%) */
  --surface-hover: ...;
  /* текст */
  --fg: ...;            /* үндсэн текст */
  --fg-muted: ...;      /* хоёрдогч */
  --fg-subtle: ...;     /* caption, placeholder */
  /* бусад */
  --border: ...;
  --accent: ...;        /* 10% */
  --accent-fg: ...;     /* accent дээрх текст */
  --danger: ...; --success: ...; --warning: ...;
}
```

## Light/Dark theming

```css
:root { --bg: #fafafa; --fg: #18181b; ... }

@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) { --bg: #09090b; --fg: #fafafa; ... }
}
:root[data-theme="dark"] { --bg: #09090b; --fg: #fafafa; ... }
```

- Гурван төлөв: system (default) / гараар light / гараар dark — `data-theme` attribute нь хэрэглэгчийн сонголтыг media query-гээс дээгүүр тавина.
- Компонент код theme мэдэхгүй — зөвхөн semantic token хэрэглэнэ.
- Dark-д: цэвэр хар биш neutral-900/950; accent-ийн saturation бууруулж lightness нэмнэ; shadow-ийн оронд surface цайралт.

## Өнгөнөөс гадна юуг token болгох

- **Spacing**: `--space-1..10` (4px scale)
- **Radius**: `--radius-sm/md/lg/full`
- **Shadow**: `--shadow-sm/md/lg`
- **Font**: `--font-sans/--font-mono`, `--text-xs..4xl`, `--leading-tight/normal`
- **Z-index**: `--z-dropdown: 50; --z-modal: 100; --z-toast: 150` — «z-index дайн»-аас сэргийлнэ
- **Duration/easing**: `--duration-fast: 150ms; --ease-out: cubic-bezier(0,0,.2,1)`

## Tailwind-тай хэрхэн зохицох

Tailwind v4-д `@theme`-ээр CSS variable тодорхойлоод utility нь тэндээс уншина:

```css
@theme {
  --color-accent: var(--accent);
  --color-surface: var(--surface);
}
/* дараа нь bg-surface, text-accent гэж хэрэглэнэ */
```

shadcn/ui яг энэ хэв маягаар (semantic HSL variables + Tailwind) баригдсан — практик жишээ болгон харахад тохиромжтой.

## Дүрэм

1. Компонент дотор hex/px шууд бичихгүй — заавал token.
2. Token нэр нь **юунд** хэрэглэгдэхийг хэлнэ, **ямар өнгө** болохыг биш (`--color-blue` ✗, `--color-accent` ✓).
3. Шинэ token нэмэхээсээ өмнө байгаагаа эргэж хар — token-ийн тоо өсөх нь системийн үнэ цэнийг бууруулдаг.

## W3C DTCG формат ба tooling

Token-ийг CSS-д биш **платформ-хамааралгүй JSON**-д хадгалаад Figma, CSS, iOS, Android руу build хийдэг. Стандарт: **W3C Design Tokens Community Group (DTCG) format** (2025-10-д 1.0 стабил).

```json
{
  "color": {
    "blue": { "600": { "$value": "#2563eb", "$type": "color" } },
    "accent": {
      "$value": "{color.blue.600}",
      "$type": "color",
      "$description": "Primary action, links (10%)"
    }
  },
  "space": { "4": { "$value": "16px", "$type": "dimension" } }
}
```

- `$value`, `$type` заавал; `$description` зөвлөмж. Alias `{color.blue.600}` = гурван давхаргын холбоос (primitive → semantic) файлд өөрт нь шингэнэ.
- `$type`-ууд: `color`, `dimension`, `fontFamily`, `fontWeight`, `duration`, `cubicBezier`, `number`, `shadow`, `typography` (composite).
- **Build**: Style Dictionary v4 (DTCG-г шууд уншина) → `tokens.css` (`:root { --color-accent: … }`), мөн `.ts`, Swift, Kotlin. Tokens Studio (Figma plugin) тэр JSON-ийг Figma variables ↔ git repo хоёр тийш sync хийнэ → **Figma ба код нэг эх сурвалжтай**.
- Theme = тусдаа set: `tokens/core.json` (primitive) + `tokens/light.json` + `tokens/dark.json` (semantic alias л өөр). Build нь `:root` ба `[data-theme="dark"]` блок хоёрыг гаргана.
- Нэрлэлтийн давхарга JSON зам болно: `color.blue.600` (primitive) → `color.accent` (semantic) → `button.primary.bg` (component). CSS var нэр = зам `-`-ээр: `--color-accent`, `--button-primary-bg`.
- **Tailwind v4 pipeline**: build-ээс гарсан semantic CSS var-уудыг `@theme { --color-accent: var(--color-accent-semantic) }` гэж бүртгэнэ — utility (`bg-accent`) ба raw `var()` хоёулаа нэг утгаас уншина. `@theme inline` — theme солигдох үед utility шууд дагадаг.
- **Хувилбар**: token package-ийг (`@org/tokens`) npm-ээр semver-тэй гарга; token нэр устгах/солих = **major**, утга өөрчлөх = minor, шинэ token = patch. Changesets-ээр CHANGELOG автоматаар. Устгахаасаа өмнө нэг хувилбар `$deprecated` тэмдэглэ.
- Жижиг проект (нэг платформ, нэг repo): JSON давхарга шаардлагагүй — шууд CSS var хангалттай. DTCG нь Figma + 2-оос олон платформ байхад л үнэ цэнтэй.

## Эх сурвалж

- W3C Design Tokens Community Group — Design Tokens Format Module — tr.designtokens.org/format/
- Style Dictionary (Amazon) — v4 docs, DTCG support — styledictionary.com
- Tokens Studio for Figma — docs.tokens.studio
- Tailwind CSS v4 — Theme variables (`@theme`, `@theme inline`) — tailwindcss.com/docs/theme
- shadcn/ui — Theming (semantic CSS variables) — ui.shadcn.com/docs/theming
- MDN — Using CSS custom properties; `prefers-color-scheme`; `color-scheme`
- Material 3 — Design tokens overview — m3.material.io/foundations/design-tokens
- Changesets — github.com/changesets/changesets
- Nathan Curtis (EightShapes) — «Naming Tokens in Design Systems»
