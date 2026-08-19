# Типограф

## Font family — 1-2, дээд тал нь 3

- **1 font** — хамгийн аюулгүй: нэг sans-serif-ийн weight-үүдээр (400/500/600/700) бүх иерархийг гаргана. Орчин үеийн SaaS/dashboard-ууд ихэнх нь ингэдэг (Inter, Geist гэх мэт).
- **2 font** — сонгодог хослол: гарчигт display/serif, body-д sans. Маркетинг, контент сайтад сайн.
- **3 дахь нь** зөвхөн monospace (код, дугаар, table-ийн тоо).

Үүнээс олон болбол сайт «эвлүүлэг» шиг харагддаг.

## Type scale — 5-8 шатлал

Дур мэдэн px өгөхийн оронд **modular scale**: суурь хэмжээг тогтмол харьцаагаар үржүүлнэ.

| Scale | Харьцаа | Хэрэглээ |
|---|---|---|
| Minor third | 1.2 | Dashboard, data-нягт UI |
| Major third | 1.25 | Ерөнхий вэб апп |
| Perfect fourth | 1.333 | Маркетинг, landing page |
| Golden ratio | 1.618 | Том hero-той editorial сайт |

Жишээ: base 16px × 1.25 → `12.8 → 16 → 20 → 25 → 31 → 39 → 49`. Tailwind-ийн default scale яг энэ логикоор баригдсан.

## Font-size-ийн нэгж: px биш rem

- `1rem = 16px` (хэрэглэгчийн browser тохиргоо). rem-ээр бичсэн текст хэрэглэгчийн default size-ийг дагаж томордог — accessibility-ийн үндсэн шаардлага.
- `html { font-size: 62.5% }` (1rem=10px) трюкийг хэрэглэхгүй — хэрэглэгчийн тохиргоог гажуудуулдаг.
- `em` нь эцгээсээ хамаарч давхарласан үед үржигддэг — зөвхөн component-дотоод харьцаанд (icon текстээ дагах гэх мэт).

## Элемент тус бүрийн түгээмэл утгууд

| Хэрэглээ | Хэмжээ | Тайлбар |
|---|---|---|
| Caption, badge, table header | 12px (0.75rem) | Үүнээс жижгийг бүү хэрэглэ |
| Secondary/UI text, dashboard body | 13-14px | Data-нягт UI-ийн ажлын морь |
| Body (контент сайт) | 16-18px | Урт текстэд 16-аас доошгүй |
| H4 / card title | 16-18px, 600 weight | |
| H3 | 20-24px | |
| H2 | 24-31px | |
| H1 / page title | 31-39px | Апп дотор 24-30px хангалттай |
| Hero (landing) | 48-72px | clamp()-тай fluid |

Апп UI (13-14px суурь) ба контент/маркетинг (16-18px суурь) хоёр өөр «горим» — нэг проект дотор зэрэгцэж болно (жишээ: admin 14px, landing 16px).

iOS 16px-ээс жижиг input-д автоматаар zoom хийдэг тул **форм дээр заавал 16px+**.

## Fluid typography — clamp()

```css
h1 { font-size: clamp(2rem, 1rem + 3vw, 3.5rem); }
```

- Гурван утга: доод хязгаар, viewport-хамааралт утга, дээд хязгаар.
- Дунд утгад заавал `rem + vw` холимог — цэвэр `vw` бол zoom-д томордоггүй тул WCAG-д унадаг.
- Зөвхөн display түвшинд (H1, H2, hero); body, товч, форм — fixed. Бүгдийг fluid болговол иерархи шахцалдана.
- [Utopia](https://utopia.fyi) — бүтэн fluid scale бодох де-факто калькулятор.

## Иерархи нь size-ээс гадна weight + color

Бүх ялгааг хэмжээгээр гаргах гэж 10 шатлал үүсгэхгүй. Ижил 14px текст 400/muted vs 600/foreground байхад л хоёр өөр түвшин болно. Текстийн өнгөний 3 түвшин: foreground / muted / subtle.

## Line-height ба мөрийн урт

- Body: **1.5-1.7**
- Гарчиг: **1.1-1.3** (том тусмаа бага)
- Мөрийн урт: 60-75 тэмдэгт — `max-width: 65ch`

## Letter-spacing / optical size

- Том гарчигт агшаана: hero-д `letter-spacing: -0.02em`
- Жижиг caption-д (12px) `+0.01em` орчим
- Variable font-ийн `opsz` axis (Inter Display cut гэх мэт) үүнийг автоматаар хийдэг.

## Ерөнхий зөвшилцөл

**1 font family (+mono) · 6-8 size · 3-4 weight · 2-3 color түвшин** — үүнээс цомхон систем бараг бүх UI-д хүрэлцдэг.

Албан ёсны стандарт гэвэл WCAG л бий (хэмжээ биш contrast + 200% zoom шаарддаг). Material Design (13 түвшин), Apple HIG (11 түвшин) нь convention; практикт 6-8 л ашиглагддаг.
