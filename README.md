# Design Research

Вэб дизайны нарийн ширийн жишиг, стандарт, практик дүрмүүдийн нэгдсэн тэмдэглэл. Responsive вэбсайт, SaaS/dashboard UI, landing page-д хамаарна.

## Агуулга

| Файл | Сэдэв |
|---|---|
| [01-color.md](01-color.md) | Өнгөний харьцаа — 60-30-10, palette бүтэц, semantic token, dark mode |
| [02-typography.md](02-typography.md) | Font family, type scale, font-size, line-height, letter-spacing |
| [03-spacing-layout.md](03-spacing-layout.md) | Spacing scale, grid, container, breakpoint, responsive зарчим |
| [04-visual-details.md](04-visual-details.md) | Border radius, shadow/elevation, border, divider, icon |
| [05-motion.md](05-motion.md) | Animation, transition, easing, duration, reduced motion |
| [06-components.md](06-components.md) | Товч, форм, table, card, empty/loading state |
| [07-accessibility.md](07-accessibility.md) | WCAG, contrast, focus, keyboard, touch target |
| [08-design-tokens.md](08-design-tokens.md) | Token архитектур, нэрлэлт, light/dark theming |

## Товч дүрмүүд (cheat sheet)

- **Өнгө**: 60% суурь · 30% хоёрдогч · 10% accent. 1 accent hue + 2-3 semantic-аас хэтрэхгүй.
- **Font**: 1 family (+mono) · 6-8 size · 3-4 weight. Body ≥16px, UI 13-14px.
- **Нэгж**: текстэд rem, зайд 4px/8px scale.
- **Contrast**: энгийн текст ≥4.5:1, том текст ≥3:1.
- **Motion**: 150-300ms, ease-out, `prefers-reduced-motion`-ыг хүндэл.
- **Token**: hex-ийг шууд бүү хэрэглэ — semantic token-оор дамжуул.
