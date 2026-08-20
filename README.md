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
| [06-components.md](06-components.md) | Товч, форм, table, card, 4 төлөв + tabs/menu/tooltip/badge/date/upload/search/pagination/confirm… |
| [07-accessibility.md](07-accessibility.md) | WCAG 2.2 (шинэ шалгуур орсон), contrast, focus, keyboard, ARIA/live region |
| [08-design-tokens.md](08-design-tokens.md) | Token архитектур, нэрлэлт, light/dark theming, DTCG формат |
| [09-localization-mn.md](09-localization-mn.md) | Монгол хэл: кирилл шрифт, урт үг, огноо/тоо/₮ формат, EN/MN toggle |
| [10-dashboard-patterns.md](10-dashboard-patterns.md) | Dashboard/ERP: app shell, навигаци, table-ийн гүн дүрэм, хариу үйлдлийн цаг, destructive/permission төлөв |
| [11-data-viz.md](11-data-viz.md) | Chart сонголт, KPI tile, палитр (categorical/sequential/diverging), axis, a11y |
| [12-landing.md](12-landing.md) | Landing/маркетинг: hero, section хэмнэл, CTA, pricing, SEO, Core Web Vitals |
| [13-checklist.md](13-checklist.md) | Pre-ship шалгах хуудас — хуудас/компонент бүрт ажиллуулна |
| [00-sources.md](00-sources.md) | Бүх эх сурвалж + зөрчилдөхөд аль нь давамгайлах |
| [references/](references/README.md) | Амтны сан — зорьж буй / зайлсхийх жишиг зургууд |

## Товч дүрмүүд (cheat sheet)

- **Өнгө**: 60% суурь · 30% хоёрдогч · 10% accent. 1 accent hue + 2-3 semantic-аас хэтрэхгүй.
- **Font**: 1 family (+mono) · 6-8 size · 3-4 weight. Body ≥16px, UI 13-14px.
- **Нэгж**: текстэд rem, зайд 4px/8px scale.
- **Contrast**: энгийн текст ≥4.5:1, том текст ≥3:1.
- **Motion**: 150-300ms, ease-out, `prefers-reduced-motion`-ыг хүндэл.
- **Token**: hex-ийг шууд бүү хэрэглэ — semantic token-оор дамжуул.
- **Хариу**: 100ms шууд · 1s урсгал · 10s анхаарал; skeleton 300ms хойшлуул.
- **Touch**: WCAG доод 24px, зөвлөмж 44px; target хооронд ≥8px.
- **Монгол**: `Өө Үү` шрифтэд бий эсэх; товч `min-width` (width биш); огноо `yyyy-MM-dd HH:mm` UTC+8; `1,250,000₮`.
- **Chart**: bar 0-ээс эхэлнэ; ≤6 hue; pie ≤5 хэсэг; өнгө дангаар мэдээлэл дамжуулахгүй.
- **Landing**: 1 h1 · 1 primary CTA · LCP ≤2.5s · JS ≤150KB gz.

## Ашиглах урсгал

1. `references/` — зорьж буй амтыг зургаар хар.
2. Хэв маяг: dashboard бол `10`, landing бол `12`, chart бол `11`.
3. Суурь дүрэм `01–08` + монгол `09`.
4. Мокап → батлуул → код.
5. Дуусахын өмнө `13-checklist.md`-ийг бүхэлд нь ажиллуул.
