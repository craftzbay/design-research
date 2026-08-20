# Эх сурвалжууд

Энэ репогийн дүрмүүд аль стандарт, аль эх сурвалжаас гарсныг нэг дор. Файл бүрийн төгсгөлд өөрийн эх сурвалж бий; энд нь нэгтгэсэн жагсаалт + хэрхэн хандах заавар.

## Албан ёсны стандарт (хүчин төгөлдөр)

| Стандарт | Юу заадаг | Энд хэрэглэсэн |
|---|---|---|
| **WCAG 2.2** (W3C, 2023) — w3.org/TR/WCAG22 | Contrast, focus, keyboard, target size, reflow, motion | 01, 04, 05, 07, 13 |
| **WAI-ARIA 1.2 + APG** (Authoring Practices Guide) — w3.org/WAI/ARIA/apg | Компонентын semantic/keyboard хэв маяг (dialog, tabs, menu, combobox…) | 06, 07 |
| **W3C Design Tokens (DTCG)** — designtokens.org | Токены JSON формат, alias, type | 08 |
| **CSS спецификаци / MDN** — developer.mozilla.org | `clamp`, container query, `color-scheme`, `@starting-style`, OKLCH, logical properties | 02, 03, 05, 01 |
| **Unicode CLDR** — cldr.unicode.org | `mn` locale-ийн огноо/тоо формат (ICU өгөгдөл дутуу байдгийн эх) | 09 |

## Платформын удирдамж (convention, стандарт биш)

- **Apple Human Interface Guidelines** — developer.apple.com/design/human-interface-guidelines: typography (11 түвшин), touch target 44pt, motion, color, dark mode.
- **Material Design 3** — m3.material.io: type scale (13 түвшин), 48dp touch, elevation/tonal surface, motion token (duration/easing), color roles.
- **GOV.UK Design System** — design-system.service.gov.uk: форм, алдааны мессеж, accessibility-д хамгийн хатуу шалгагдсан жишиг.
- **Atlassian / Shopify Polaris / IBM Carbon** — data-нягт enterprise UI, table, density, token нэрлэлт.

## Судалгаа, практик

- **Nielsen Norman Group** (nngroup.com): 10 Usability Heuristics; Response Times: 3 Important Limits (0.1s/1s/10s); Placeholders in Form Fields Are Harmful; Progress Indicators; Empty States; Breadcrumbs; Carousels; Infinite Scroll vs Pagination; Hamburger Menus.
- **Refactoring UI** (Adam Wathan, Steve Schoger) — иерархи size-ээр биш weight/color-оор, spacing scale, shadow давхарлах, 60-30-10 практик.
- **RAIL / web.dev** (Google): Core Web Vitals босго (LCP 2.5s, INP 200ms, CLS 0.1), font loading, `fetchpriority`, image best practices.
- **Utopia** (utopia.fyi) — fluid type/space калькулятор.
- **APCA** (Andrew Somers, WCAG 3 draft) — perceptual contrast; Lc утгууд.
- **Okabe–Ito палитр** (2008) — colorblind-safe 8 өнгө; **Tableau 10** — categorical жишиг.
- **Edward Tufte**, *The Visual Display of Quantitative Information* — data-ink ratio, chart junk.
- **Inclusive Components** (Heydon Pickering) — компонент бүрийн accessible хэрэгжүүлэлт.
- **Every Layout** (Bell, Pickering) — algorithmic CSS layout.

## Хэрэглэх зарчим

1. Зөрчилдвөл **WCAG > платформын удирдамж > практик зөвлөмж**. Жишээ: touch target — WCAG 24px (доод хязгаар), HIG 44 / M3 48 (зөвлөмж) → бид 44.
2. Тоон утга бүр эх сурвалжтай байх ёстой; "ингэж санагдсан" дүрэм нэмэхгүй.
3. Стандарт шинэчлэгдэхэд (WCAG 3, CSS шинэ feature) энэ файл + холбогдох баримтыг хамт шинэчил.
