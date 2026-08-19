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
