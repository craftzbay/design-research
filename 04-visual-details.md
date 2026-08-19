# Visual нарийн ширийн — radius, shadow, border, icon

## Border radius

Нэг проектод 3-4 л утга байхад хангалттай:

| Хэрэглээ | Утга |
|---|---|
| Жижиг элемент (badge, checkbox, tag) | 4px |
| Товч, input, select | 6-8px |
| Card, modal, popover | 8-16px |
| Avatar, pill товч | 9999px (full) |

- **Дотоод radius = гадаад radius − padding**: card 16px radius, padding 8px бол доторх зураг 8px radius байж нүдэнд зөв харагдана. Ижил утга давхарлавал дотоод булан «бүдүүн» харагддаг.
- Нэг брэнд-шийдвэр: sharp (0-4px, «ноцтой» ERP/fintech маяг) vs rounded (8-16px, найрсаг SaaS маяг) — хольж болохгүй.

## Shadow / Elevation

Shadow нь «гоёл» биш **давхаргын мэдээлэл** — юу юуны дээр байгааг хэлдэг:

| Түвшин | Хэрэглээ | Жишээ |
|---|---|---|
| xs | Товч, input | `0 1px 2px rgb(0 0 0 / 0.05)` |
| sm | Card | `0 1px 3px rgb(0 0 0 / 0.1)` |
| md | Dropdown, popover | `0 4px 12px rgb(0 0 0 / 0.1)` |
| lg | Modal, drawer | `0 16px 48px rgb(0 0 0 / 0.15)` |

- Чанартай shadow нь **2-3 давхар**: нэг жижиг тод (contact) + нэг том бүдэг (ambient). `0 1px 2px rgb(0 0 0/.06), 0 4px 12px rgb(0 0 0/.08)`.
- Гэрэл **дээрээс** тусдаг гэж үзнэ — y-offset эерэг, x-offset 0.
- Хар saturation-гүй биш, суурь өнгөний hue-тэй shadow (жишээ нь slate-д `rgb(15 23 42 / 0.08)`) илүү байгалиас.
- **Dark mode-д shadow бараг ажилладаггүй** — elevation-ыг surface-ийн цайралт + border-оор гарга.
- Border vs shadow: data-нягт UI-д 1px border хямдхан бөгөөд цэвэр; shadow-г interactive/floating элементэд үлдээ.

## Border ба divider

- Өнгө: neutral scale-ийн 200 (light) / 800 (dark) орчим — текстээс хамаагүй сул.
- 1px хангалттай; 2px нь зөвхөн focus/selected төлөвт.
- Divider-ийг spacing-аар орлуулж болдог — зай хангалттай бол шугам хэрэггүй. Шугам их = чимээ их.
- Input border нь non-text contrast 3:1 шаардлагад унадаг тул хэт цайвар болгохгүй (жишээ нь gray-300 нь цагаан дээр 1.5:1 — албан ёсоор хангалтгүй).

## Icon

- Нэг л icon set хэрэглэ (Lucide, Heroicons, Phosphor…) — өөр set-ийн icon stroke/style-аараа зөрдөг.
- Хэмжээ: UI-д 16/20/24px; текстийн хажууд байхдаа cap-height-тай тэнцэх орчим.
- Stroke width тогтмол (ихэвчлэн 1.5-2px); icon-ыг scale хийвэл stroke зузаан/нимгэн болдгийг анзаар.
- Icon + text хослохдоо `gap: 8px`, вертикаль төвлөрөл `align-items: center`.
- Icon-only товчид заавал `aria-label`.

## Зураг ба media

- `aspect-ratio` заавал өг — layout shift (CLS) -ээс сэргийлнэ.
- `object-fit: cover` + төвлөрөл; хүний зурагт `object-position` анхаар.
- Placeholder: blur-up эсвэл dominant-color фон — цагаан гялсхийлт муухай.
- Format: WebP/AVIF, srcset-тэй responsive; hero зургийг preload, доод зургуудыг lazy.
